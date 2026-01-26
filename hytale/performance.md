# Hytale Server Performance optimieren und RAM-Verbrauch senken

## Vorher/Nachher (RAM/Cache/Buffer)

**Vorher (Beispiel-Messung):**

![Memory Basic – Vorher](./hytale-memory.jpeg)

---

Ziel: stabile TPS (weniger Ruckler), geringerer RAM-Druck (weniger Chunk-/Objekt-Müll), weniger Crash-Risiko unter Last.  
Wir machen dafür drei Dinge: (1) Java-Startcommand optimieren, (2) Performance-Saver-Addon nutzen, (3) `config.json` passend setzen.

---

## 1) Neuer Startcommand (Java-Flags)

Dieser Startcommand zielt auf **stabilere Tick-Zeiten** (weniger Lag-Spitzen) und **bessere Speicherkontrolle** durch eine für Server typische G1GC-Konfiguration.

### Startcommand

```bash
java -XX:AOTCache=Server/HytaleServer.aot -Xms2048M -Xmx8192M -XX:+UseG1GC -XX:MaxGCPauseMillis=100 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:G1NewSizePercent=35 -XX:G1MaxNewSizePercent=60 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=15 -XX:InitiatingHeapOccupancyPercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:G1MixedGCLiveThresholdPercent=90 -XX:+ParallelRefProcEnabled -XX:MinHeapFreeRatio=10 -XX:MaxHeapFreeRatio=20 -jar Server/HytaleServer.jar --assets Assets.zip -bind 0.0.0.0:3500
```

### Parameter-Erklärung

#### A) AOT / Start-Performance
- `-XX:AOTCache=Server/HytaleServer.aot`  
  Aktiviert einen AOT-Cache (Ahead-of-Time). Kann Start-/Warmup-Zeiten und Hotspot-Performance verbessern (abhängig von JVM/Build/Workload).

#### B) Heap-Größen (RAM-Budget)
- `-Xms2048M`  
  Initiale Heap-Größe: Java reserviert beim Start ~2 GB. Reduziert dynamische Heap-Vergrößerungen in der Startphase.
- `-Xmx8192M`  
  Maximale Heap-Größe: Obergrenze für Java-RAM. Verhindert Out-of-Memory bei Lastspitzen, erhöht aber nicht automatisch die Performance.

#### C) Garbage Collector (G1GC) + Latenzziel
- `-XX:+UseG1GC`  
  Verwendet G1GC (Region-basierter Collector), typischer Standard für Server mit mehreren GB Heap.
- `-XX:MaxGCPauseMillis=100`  
  Zielwert für maximale GC-Pausen. G1GC versucht, die Arbeit so zu planen, dass Pausen im Bereich dieses Ziels bleiben (Best-Effort, keine Garantie).

#### D) Schutz vor ungünstigen `System.gc()`-Aufrufen
- `-XX:+DisableExplicitGC`  
  Ignoriert explizite GC-Trigger (z. B. durch Plugins). Reduziert Risiko großer, unplanbarer Pausen.

#### E) Young-Gen-Größe (kurzlebige Objekte effizient entsorgen)
- `-XX:G1NewSizePercent=35`  
  Untergrenze für den Anteil des Young Gen am Heap (Startpunkt/Minimum).
- `-XX:G1MaxNewSizePercent=60`  
  Obergrenze für den Anteil des Young Gen. Mehr Young Gen kann die Verarbeitung vieler kurzlebiger Objekte stabilisieren.

#### F) Region-Größe
- `-XX:G1HeapRegionSize=16M`  
  Setzt die Region-Größe auf 16 MB. Bei großen Heaps kann das Verwaltungsaufwand senken; Trade-off: gröbere Granularität.

#### G) Reserve + früheres Starten der Concurrent-Phase
- `-XX:G1ReservePercent=15`  
  Reserviert freie Regionen als Puffer. Senkt das Risiko, dass der Heap unter Last „zu knapp“ wird.
- `-XX:InitiatingHeapOccupancyPercent=20`  
  Startet die concurrent marking/collection Phase bei relativ niedriger Heap-Auslastung. Ziel: frühzeitig mit dem Aufräumen beginnen, bevor Druck entsteht.

#### H) Mixed-GC-Steuerung (Old-Gen schrittweise bereinigen)
- `-XX:G1HeapWastePercent=5`  
  Schwelle, ab der G1 Regionen als „lohnend“ für Mixed GCs betrachtet (weniger tolerierter „Waste“ → tendenziell früheres Aufräumen).
- `-XX:G1MixedGCCountTarget=4`  
  Zielanzahl Mixed-GCs, um Old-Gen-Bereinigung über mehrere Zyklen zu verteilen.
- `-XX:G1MixedGCLiveThresholdPercent=90`  
  Regionen mit sehr hohem Live-Anteil werden seltener in Mixed-GCs aufgenommen (Priorisierung der „profitablen“ Regionen).

#### I) Parallelisierung
- `-XX:+ParallelRefProcEnabled`  
  Parallelisiert Reference Processing (z. B. Soft/Weak/Phantom References). Kann Pausen reduzieren.

#### J) Heap-Free-Ratio (Wachstum/Schrumpfen des Heaps)
- `-XX:MinHeapFreeRatio=10`  
- `-XX:MaxHeapFreeRatio=20`  
  Steuert, wie viel „freier“ Heap Java nach GC anstrebt. Niedrigere Werte können dazu führen, dass Java weniger freien Heap vorhält (workload-/plattformabhängig).

#### K) Serverstart / Netzwerk
- `-jar Server/HytaleServer.jar`  
  Startet das Server-JAR.
- `--assets Assets.zip`  
  Lädt die Assets.
- `-bind 0.0.0.0:3500`  
  Bindet an alle Interfaces auf Port 3500 (extern erreichbar, sofern Firewall/Portforwarding korrekt).

---

## 2) MC-HOST24 Performance Saver Addon (Ressourcen sparen ohne Spielgefühl zu zerstören)

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
