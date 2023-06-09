# Bluemap auf dem Server installieren

Bluemap ist ein kostenloses Plugin welches dem/den Spieler/n eine 3D-Übersichtskarte von allen Server-Welten, ähnlich wie Dynmap, im Webbrowser anzeigen lassen kann. Dafür braucht man einen PC und/oder Server mit viel Leistung und ähnlich wie bei GeyserMC/Dynmap einen zusätzlichen Port.

## 1. Herunterladen und installieren

Bluemap kann man sich auf [SpigotMC](https://www.spigotmc.org/resources/bluemap.83557) herunterladen. Danach muss es nur noch entweder per Drag & Drop oder per FTP-Client in den "plugins"-Ordner bewegt werden und der Minecraft Server, auf dem man das Plugin gerade installiert hat, muss auch nochmal neugestartet werden.

## 2. Konfiguration

Bevor Bluemap richtig funktioniert, muss in der "core.conf"-Datei der Download weiterer benötigter Dateien aktzeptiert werden. Diese Datei befindet sich normalerweise im "BlueMap"-Ordner, der in dem "plugins"-Ordner erstellt wurde. <b>Nicht verwechseln</b> mit dem "bluemap"-Ordner, der außerhalb vom "plugins"-Ordner erstellt wurde. Wurde das "accept-download" von "false" auf "true" geändert, kann das Plugin mit /bluemap reload einfach neugeladen werden.

## 3. Die Welt rendern

Sobald die benötigten Dateien heruntergeladen wurden, fängt Bluemap automatisch an die aktuelle Welt zu rendern. Wenn alles fertig gerendert wurde, wird dem Besucher nun eine Welt angezeigt. Bei kleineren Welten (z.B. 512 x 512) dauert das eigentlich nicht so lange, aber bei größeren Welten (z.B. 8192 x 8192) kann das ganze auch teilweise mal sehr lange dauern. Auf der Bluemap werden z.B. immer alle aktuell aktiven Spieler mit ihren Leben angezeigt.

## 4. Spielen mit Bluemap

Nachdem alles fertig gerendert wurde und geladen hat, kann man nun mit dem Spielen beginnen. Viel Spaß!

