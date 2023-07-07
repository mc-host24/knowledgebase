# Dynmap auf dem Server installieren

DynMap ist ein kostenloses Plugin, geschrieben von Mikeprimm, welches dem/den Spieler/n eine Übersichtskarte von allen Server-Welten im Webbrowser anzeigen lassen kann. Dafür braucht man einen PC und/oder Server mit viel Leistung und ähnlich wie bei GeyserMC einen zusätzlichen Port.

## 1. Herunterladen und installieren

Dynmap kann man sich entweder auf [Bukkit](https://dev.bukkit.org/projects/dynmap) oder auf [SpigotMC](https://spigotmc.org/resources/dynmap.274) herunterladen. Danach muss es nur noch entweder per Drag & Drop oder per FTP-Client in den "plugins"-Ordner bewegt werden und der Minecraft Server, auf dem man das Plugin gerade installiert hat, muss auch nochmal neugestartet werden.

## 2. Konfiguration

Dynmap generiert, so wie fast jedes andere Plugin, eine sogenannte Konfigurationsdatei. Diese kann bearbeitet werden. [Hier](https://github.com/webbukkit/dynmap/wiki/Configuration.txt) können alle Optionen der Konfigurationsdatei angeschaut werden. Allerdings heißt hier die Datei nicht wie üblich "config.yml", sondern "configuration.txt". Darauf <b>muss</b> man achten, wenn man Dynmap benutzen will oder eigene Erweiterungen schreiben möchte.

## 3. Die Welt rendern

Nach Installation des Plugins und einem erfolgreichen Serverneustart wird dem Besucher erstmal nur eine schwarze Weltkarte angezeigt. Dies ist normal und <b>kein Bug</b>. Es liegt daran, dass die Welt einfach noch nicht gerendert wurde. Damit etwas angezeigt wird, muss ein Server-Operator den Befehl /dynmap fullrender ausführen. Wenn alles fertig gerendert wurde, wird dem Besucher nun eine Welt angezeigt. Bei kleineren Welten (z.B. 512 x 512) dauert das eigentlich nicht so lange, aber bei größeren Welten (z.B. 8192 x 8192) kann das ganze auch teilweise mal sehr lange dauern. Auf der Dynmap werden z.B. immer alle aktuell aktiven Spieler mit ihren Leben angezeigt.

## 4. Spielen mit Dynmap

Nachdem alles fertig gerendert wurde und geladen hat, kann man nun mit dem Spielen beginnen. Viel Spaß!

## 5. Hinweise

Damit die Map im Browser angezeigt werden kann, muss ein zusätzlicher Port freigegeben werden. Dies ist im Webinterface möglich.
