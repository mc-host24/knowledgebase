# Hytale Server Performance optimieren und RAM-Verbrauch senken

Ziel: stabile TPS (weniger Ruckler), geringerer RAM-Druck (weniger Chunk-/Objekt-Müll), weniger Crash-Risiko unter Last.  
Wir machen dafür drei Dinge: (1) Java-Startcommand optimieren, (2) Performance-Saver-Addon nutzen, (3) `config.json` passend setzen.

---

## 1) Neuer Startcommand (Java-Flags)

> Hinweis: Mehr RAM (`-Xmx`) ist nicht automatisch besser. Wichtig ist: stabile Tick-Zeit + weniger unnötige Arbeit (Chunks/Entities) + kontrolliertes Aufräumen (GC).

### Startcommand

```bash
java -XX:AOTCache=Server/HytaleServer.aot -Xms2048M -Xmx8192M -XX:+UseG1GC -XX:MaxGCPauseMillis=100 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:G1NewSizePercent=35 -XX:G1MaxNewSizePercent=60 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=15 -XX:InitiatingHeapOccupancyPercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:G1MixedGCLiveThresholdPercent=90 -XX:+ParallelRefProcEnabled -XX:MinHeapFreeRatio=10 -XX:MaxHeapFreeRatio=20 -jar Server/HytaleServer.jar --assets Assets.zip -bind 0.0.0.0:3500
```

### Was die Optionen bedeuten (einfach erklärt)

#### Speicher (RAM) festlegen
- `-Xms2048M`  
  Startet den Server direkt mit **2 GB** reserviertem Speicher → weniger „Nachallokieren“ beim Hochfahren.
- `-Xmx8192M`  
  Setzt ein **Maximum von 8 GB** → schützt vor Out-of-Memory bei Spitzenlast.

#### Garbage Collection (Aufräumen) auf „stabil“ trimmen
- `-XX:+UseG1GC`  
  Nutzt den **G1-Aufräumer**: teilt Speicher in Bereiche und räumt schrittweise auf → oft weniger Lag-Spikes.
- `-XX:MaxGCPauseMillis=100`  
  Zielwert: Aufräumpausen möglichst unter **~100 ms** halten (Richtwert, keine harte Garantie).

#### Verhindern, dass Plugins Lag-Spikes auslösen
- `-XX:+DisableExplicitGC`  
  Ignoriert manuelle „räum jetzt auf“-Aufrufe → verhindert häufige Stop-the-world-Spitzen.

#### Mehr Platz für kurzlebige Objekte (typisch für Gameserver)
- `-XX:G1NewSizePercent=35`  
  Mindestens **35%** des Heaps für „junge“ Objekte.
- `-XX:G1MaxNewSizePercent=60`  
  Bis zu **60%** des Heaps dürfen „jung“ sein.  
  Effekt: Kurzlebige Daten werden effizient entsorgt, bevor sie den Heap „aufblähen“.

#### Region-Größe (G1-Feintuning)
- `-XX:G1HeapRegionSize=16M`  
  Setzt die Größe der Speicherbereiche auf **16 MB** → weniger Verwaltungsaufwand bei großen Heaps.

#### Reserve + früheres Starten größerer Aufräumphasen
- `-XX:G1ReservePercent=15`  
  Hält **15% Reserve** frei → reduziert Risiko, dass der Heap unter Last „voll läuft“.
- `-XX:InitiatingHeapOccupancyPercent=20`  
  Startet größere Aufräumaktionen **früher** (ab ~20% Belegung) → lieber öfter klein als selten riesig.

#### Aggressiveres und gleichmäßigeres „Mischen“ (alte + neue Bereiche)
- `-XX:G1HeapWastePercent=5`  
  Räumt eher auf, wenn genug „toter“ Speicher herumliegt.
- `-XX:G1MixedGCCountTarget=4`  
  Verteilt Mixed-GC auf ~**4 Zyklen** → weniger einzelne große Pausen.
- `-XX:G1MixedGCLiveThresholdPercent=90`  
  Nimmt alte Regionen eher mit, solange sie nicht fast komplett „lebendig“ sind.

#### Parallelisierung bei Referenzen
- `-XX:+ParallelRefProcEnabled`  
  Bestimmte Aufräumarbeiten parallel → weniger Pausen/Spitzen.

#### „Freien Heap“ klein halten (RAM schlanker)
- `-XX:MinHeapFreeRatio=10`  
- `-XX:MaxHeapFreeRatio=20`  
  Java hält weniger unnötig freien Speicher „warm“ → kann RAM-Peaks senken (workload-abhängig).

#### AOT-Cache (optional)
- `-XX:AOTCache=Server/HytaleServer.aot`  
  Nutzt einen Cache für voroptimierten Code → kann Start/Hotspots verbessern (Effekt je nach JVM/Build unterschiedlich).

#### Serverstart und Netzwerk
- `-jar Server/HytaleServer.jar --assets Assets.zip`  
  Startet den Server und lädt Assets.
- `-bind 0.0.0.0:3500`  
  Bindet an alle Netzwerk-Interfaces auf Port **3500** (von außen erreichbar, wenn Firewall/Portforward passt).

---

## 2) Performance-Saver-Addon (Ressourcen sparen ohne Spielgefühl zu zerstören)

Das Addon reduziert Lastspitzen und stabilisiert den Betrieb. Es setzt an drei Punkten an:

### TPS Limiting (stabil statt maximal)
- Stabilere TPS sind oft besser als hohe, aber schwankende TPS (Client-Prediction + Netzwerk reagieren sensibel auf Schwankungen).
- Das Addon kann TPS auf einen festen Wert begrenzen (Standard: **20 TPS**).
- Wenn der Server leer ist, reduziert es TPS zusätzlich (Standard: **5 TPS**) → spart CPU und indirekt RAM-Druck.

**Effekt:** weniger CPU-Spitzen → weniger GC-Stress → weniger Mikrolags.

### Dynamische View-Radius-Anpassung (Sichtweite nach Ressourcenlage)
- Hohe Sichtweite = mehr aktive Chunks = mehr Entities/Daten = mehr CPU + mehr RAM.
- Das Addon erkennt:
  - **CPU-Druck** über sinkende TPS,
  - **RAM-Druck** über häufige GC-Versuche der JVM.
- Bei Druck wird die Sichtweite automatisch reduziert, um Ressourcen freizumachen.
- Erholt sich der Server, wird die Sichtweite schrittweise wieder erhöht.

**Effekt:** verhindert ressourcenbedingte Abstürze, besonders unter Last/Stress.

### Zusätzliche Garbage Collection (nur wenn es wahrscheinlich hilft)
- Java gibt ungenutzten Speicher nicht immer sofort frei, besonders nach Lastspitzen.
- Das Addon beobachtet geladene Chunks und triggert eine zusätzliche GC, wenn sehr wahrscheinlich Speicher freigeworden ist.

**Effekt:** weniger „toter Ballast“ im RAM nach Peak-Situationen.

---

## 3) `config.json` anpassen

```json
performance: {
  chunkLoadingOptimization: true,
  reducedViewDistance: true,
  optimizedGarbageCollection: true
}
```

### Bedeutung der Optionen
- `chunkLoadingOptimization: true`  
  Effizienteres Chunk-Handling → weniger CPU-Spitzen + weniger temporäre Speicherlast.
- `reducedViewDistance: true`  
  Reduziert Grundlast durch weniger Sichtweite/Chunks → direkt weniger RAM/CPU.
- `optimizedGarbageCollection: true`  
  Unterstützt GC-freundlicheres Verhalten → weniger Peaks/Fragmentierung.

---

## Praxis-Hinweise (damit es messbar wird)
- Größter Hebel: **weniger aktive Chunks** (View-Distance/Radius) + **stabile TPS** + **kontrollierte GC**.
- `-Xmx` realistisch dimensionieren: zu hoch kann dazu führen, dass Java „mehr behält als nötig“.
- Erfolg messen: TPS-Stabilität + GC-Logs + Peak-RAM beobachten (vorher/nachher).
