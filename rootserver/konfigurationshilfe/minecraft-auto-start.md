# Minecraft Automatische Startdatei

* Damit dein Minecraft Server nach einem Crash Automatisch Hochfährt
* Erstelle eine start.sh datei:

```bash
nano start.sh
```

* Füge diesen code ein und drücke "STRG" + "O" Danach "Enter"
* Um das gespeicherte Terminal zu schließen, drücke "Strg" + "X" 

```bash
while true
do
  Dein_Java_File/java -jar spigot.jar
  echo 'Willst Du den Server komplett stoppen, drücke STRG+C!'
  echo "Neustart in:"
  for i in 5 4 3 2 1
  do
  echo "$i..."
  sleep 1
  done
  echo 'Server neustart!'
done
```

* Ein Beispiel für einen Pfad 

```bash
/usr/lib/jvm/adoptopenjdk-8-hotspot-amd64/bin/java -jar spigot.jar
```

* Nun gebe deiner Startdatei Rechte zum Ausführen
 
```bash
chmod +x start.sh
```

* Nun kannst du dein Server starten:

```bash
./start.sh
```

* Falls du dein Server im Hintergrund laufen lassen möchtest:

```bash
screen -AmdS Session_Name ./start.sh
```

## Aikar's Flags
Um die bestmögliche Performance aus deinem Minecraft-Server herauszuholen, empfiehlt sich die Verwendung von `Aikar's Flags`. Dies sind verschiedene Parameter, die in der Start-Datei in den `java` Befehl integriert werden und mehr Leistung ermöglichen können. Ein Beispiel Befehl kann wie folgt aussehen:
```bash
java -Xms8192M -Xmx8192M --add-modules=jdk.incubator.vector -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -Dusing.aikars.flags=https://mcflags.emc.gs -Daikars.new.flags=true -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -jar server.jar --nogui
```
Es gibt auch [Tools](https://flags.sh/), die die ideale Konfiguration der Flags für einen ermitteln.
