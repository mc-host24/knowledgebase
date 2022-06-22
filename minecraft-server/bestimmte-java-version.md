# Minecraft Server mit Unterschiedlicher Java version ausführen

* Wenn du mehrere Java Versionen auf deinem Server hast, kannst du immer dein Java Pfad angeben in der
* Start.sh, damit Minecraft mit dieser Java Version auch startet

* Minecraft Start.sh:

```bash
screen -S Minecraft Dein_Java_pfad/java -Xms1G -Xmx2G -jar Spigot.jar
```

* Beispiel:

```bash
screen -S Minecraft /usr/lib/jvm/adoptopenjdk-8-hotspot-amd64/bin/java -Xms1G -Xmx2G -jar Spigot.jar
```

* Deine insatllierte Javav version findest du hier im Pfad

```bash
cd /usr/lib/jvm/
```

* Mit diesem Befehl zeigst du dein Verzeichnis an und siehst, welche Java-Versionen du hast

```bash
ls
```
