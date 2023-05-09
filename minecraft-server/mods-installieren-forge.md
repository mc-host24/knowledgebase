Dieses Tutorial zeigt, wie man sich Mods für Forge auf Minecraft-Servern installieren kann.

# 1. Anforderungen
Zuerst wird ein Forge-Server, ein [Fabric-Server](minecraft-server/mods-installieren-fabric.md) oder ein [Mohist-Server](minecraft-server/mods-und-plugins.md) für die <b>Java Edition von Minecraft</b> benötigt. Diese Server sind speziell für Mods gedacht.

# 2. Forge installieren
Falls du aktuell noch kein Forge installiert hast, kannst du dies noch nachträglich dazu installieren. Wie das geht, steht [hier](minecraft-server/version-wechseln.md). Hier wird die aktuelle Version 45.0.xx empfohlen.

# 3. Mods installieren
Falls du Forge (bereits) installiert hast, kannst du jetzt Mods installieren. Dazu öffnest du in deinem Browser [CurseForge](https://curseforge.com/minecraft/mc-mods), lädst dir den Mod den du willst für die passende Minecraft-Version (z.B. 1.19.4) herunter.

## 3.1 Mods hochladen
Falls du ein FTP-Programm besitzt, wie z.B. [FileZilla](http://filezilla-project.org/), kannst du dich dort per FTP-Zugriff auf das Dateiverzeichnis des Minecraft-Servers einloggen und dann entweder den Mod per Drag-and-Drop hochladen oder du navigierst dich einmal zum Download-Verzeichnis, wo die heruntergeladene JAR-Datei des Mods automatisch abgelegt wurde und auf dem Server zum Mod-Verzeichnis. Dann kannst du den Upload der Datei starten.

# 4. Server neu starten
Damit der Server die kürzlich hochgeladenen Mods auch erkennt, muss er noch neugestartet werden. Dies machst du am besten übers Webinterface deines Minecraft-Servers oder ingame über den Befehl /restart oder /stop. Nach dem Neustart sollten die Mods erkannt werden und du kannst nun mit Mods spielen.

# 5. Hinweise
Damit z.B. die gemoddeten die Blöcke auf beiden Seiten (Client und Server) erkannt werden, muss der Mod <b>auch auf dem Client</b> installiert sein. Ansonsten kannst du den Server nicht betreten und es kommt nur eine Fehlermeldung. Wie du dir Forge und Mods auf dem Client installieren kann, steht [hier](https://www.gamez.de/guides/minecraft-mods/#:~:text=Installation%20von%20Mods.-,Minecraft%20Forge%20sorgt%20für%20eine%20problemlose%20Installation%20von%20Mods.,und%20klickt%20auf%20“forge”.)

# 6. Mods mit Ports (z.B. DynMap)
Einige Mods (z.B. DynMap und Simple Voice Chat) erfordern, dass zusätzliche Ports freigegeben werden. Dies ist ebenfalls im Webinterface möglich. Für nähere Infos zur DynMap siehe bitte [hier](minecraft-server/weltkarte.md) und für den Sprachchat siehe [hier](minecraft-server/sprachchat.md)

Solltest du alles richtig gemacht haben, funktioniert der Server nun! Viel Spaß beim Spielen!
