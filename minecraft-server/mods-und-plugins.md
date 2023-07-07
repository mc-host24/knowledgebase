Dieses Tutorial zeigt, wie man sich Mohist auf Minecraft-Servern installieren kann.

# 1. Anforderungen
Zuerst wird ein [Mohist-Server](https://mohistmc.com) für die <b>Java Edition von Minecraft</b> benötigt. Dieser Server ist ein Forge-Server, der speziell für Mods und Plugins gedacht ist.

# 2. Mohist installieren
Falls du aktuell noch kein Mohist installiert hast, kannst du dies noch nachträglich dazu installieren. Wie das geht, steht [hier](minecraft-server/version-wechseln.md). Hier wird die aktuelle Minecraft Version 1.19.4 empfohlen.

# 3. Mods installieren
Falls du Mohist (bereits) installiert hast, kannst du jetzt Mods und/oder Plugins installieren. Dazu öffnest du in deinem Browser [CurseForge-Mods](https://curseforge.com/minecraft/mc-mods) oder [CurseForge-Plugins](https://curseforge.com/minecraft/bukkit-plugins), lädst dir den Mod oder das Plugin, das du willst für die passende Minecraft-Version (z.B. 1.19.4) herunter.

## 3.1 Mods hochladen
Falls du ein FTP-Programm besitzt, wie z.B. [FileZilla](http://filezilla-project.org/), kannst du dich dort per FTP-Zugriff auf das Dateiverzeichnis des Minecraft-Servers einloggen und dann entweder den Mod oder das Plugin per Drag-and-Drop hochladen oder du navigierst dich einmal zum Download-Verzeichnis, wo die heruntergeladene JAR-Datei des Mods oder des Plugins automatisch abgelegt wurde und auf dem Server zum Mod- bzw. Plugin-Verzeichnis. Dann kannst du den Upload der Datei starten.

# 4. Server neu starten
Damit der Server die kürzlich hochgeladenen Mods bzw. Plugins auch erkennt, muss er noch neugestartet werden. Dies machst du am besten übers Webinterface deines Minecraft-Servers oder ingame über den Befehl /restart oder /stop. Nach dem Neustart sollten die Mods bzw. Plugins erkannt werden und du kannst nun mit ihnen spielen.

# 5. Hinweise
Damit z.B. die Blöcke auf beiden Seiten (Client und Server) erkannt werden, muss der Mod <b>auch auf dem Client</b> installiert sein. Ansonsten kann man den Server nicht betreten und es kommt nur eine Fehlermeldung. Bei Plugins ist dies nicht der Fall. Wie man sich Forge und Mods auf dem Client installieren kann, steht [hier](https://fabricmc.net/wiki/de:tutorial:adding_mods#:~:text=Um%20dem%20Fabric%2DClient%20eine,sie%20in%20diesem%20Ordner%20ab.)

# 6. Mods mit Ports (z.B. DynMap)
Einige Mods, die es auch als Plugins gibt (z.B. DynMap und Simple Voice Chat) erfordern, dass zusätzliche Ports freigegeben werden. Dies ist ebenfalls im Webinterface möglich. Für nähere Infos zur DynMap siehe bitte [hier](minecraft-server/weltkarte.md) und für den Sprachchat siehe [hier](minecraft-server/sprachchat.md)

Solltest du alles richtig gemacht haben, funktioniert der Server nun! Viel Spaß beim Spielen!
