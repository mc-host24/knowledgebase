# Cross-Plattform Minecraft Server auf Rootserver installieren

Diese Anleitung soll erklären, wie man einen Cross-Plattform Minecraft-Server in der aktuellen Version 1.19.1 auf einem Rootserver installiert.

## Den Server herunterladen

Als erstes muss man sich die Server-Dateien herunterladen. PaperMC ist eine ganz gute Software dafür und hat viel mehr Features gegenüber Spigot. Für einen PaperMC-Server gibt es dieses Setup-Skript, welches man hier finden kann: https://github.com/TheRemote/RaspberryPiMinecraft. Will man jedoch einen Pocket Edition Server installieren, so gibt es dieses Setup-Skript: https://github.com/TheRemote/MinecraftBedrockServer.

## Anleitung für einen Java Edition Server

Danach legt man ein leeres Verzeichnis an, öffnet das Terminal seines Rootservers, wechselt zuerst mit cd ins soeben angelegte Verzeichnis und gibt dann dort den folgenden Befehl ein: <code> curl https://raw.githubusercontent.com/TheRemote/RaspberryPiMinecraft/master/SetupMinecraft.sh | bash</code>.
Das Skript fragt jetzt einen, wie viel RAM in Megabytes man dem Server zuweisen will. 2GB RAM sind eine gute Empfehlung, damit es flüssig funktioniert, also tippt man 2048 ein. Danach sollte man gefragt werden, ob der Minecraft-Server beim Hochfahren des Rootservers aktiviert werden soll, sollte man ein "Y" eintippen. Bei der nächsten Frage, ob der Server ein Backup um 4:00 Uhr morgens machen soll, sollte auch ein "Y" eingetippt werden. Jetzt konfiguriert sich der Rest und der Server startet.

## Anleitung für einen Pocket Edition Server

Das Skript für einen Pocket Edition Server ist fast identisch, hier muss man bei der Konfiguration noch einen Pfad zu einem leeren Ordner eingeben. Das Bedrock-Skript unterstützt auch mehrere Server in einem großen Ordner als Unterordner.
