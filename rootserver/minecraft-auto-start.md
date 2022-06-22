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
