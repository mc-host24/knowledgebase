# Minecraft Server mit Unterschiedlicher Java version ausführen

* Wenn du mehrere Java Versionen auf deinem Server hast, kannst du in der start.sh einen Java Path angeben, damit der Server in der gewünschten Java Version startet.

* Minecraft Start.sh:

```bash
screen -S Minecraft Dein_Java_pfad/java -Xms1G -Xmx2G -jar Spigot.jar
```

* Beispiel:

```bash
screen -S Minecraft /usr/lib/jvm/adoptopenjdk-8-hotspot-amd64/bin/java -Xms1G -Xmx2G -jar Spigot.jar
```

* Deine insatllierte Java Versionen findest du hier:

```bash
cd /usr/lib/jvm/
```

* Mit diesem Befehl kannst du anschauen, welche Java Versionen auf deinem Server installiert sind.

```bash
ls
```
