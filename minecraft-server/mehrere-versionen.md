# Mehrere Versionen auf dem Minecraft-Server zulassen mit ViaVersion

Dieser Artikel soll erklären, wie man auf seinem Minecraft: Java Edition Server mehrere Versionen zulassen kann. Dafür braucht man einen Plugin-fähigen Server (am besten Spigot/PaperMC) und das kostenlose Plugin ViaVersion, welches [hier](https://viaversion.com) kostenlos heruntergeladen werden kann.

## 1. Voraussetzungen

* ein Minecraft: Java Edition Server (mindestens mit PaperMC 1.8.8 und neuer)
* der Server sollte Plugin-fähig sein.

## 2. ViaVersion herunterladen und installieren

Am besten lädt man sich das Plugin unter dem obigen Link herunter. Nachdem es heruntergeladen wurde, muss es vom lokalen Desktop in den "plugins"-Ordner verschoben werden. Dies kann man entweder im Multicraft-Panel oder im FTP-Client machen. Jetzt muss man nur noch einmal den Server neustarten und schon sollte ViaVersion starten.

## 3. Konfiguration

Beim erstmaligen Start des Plugins wird eine sogenannte "config.yml"-Datei generiert, die man bearbeiten kann. Dort kann man z.B. bestimmte Versionen blockieren oder einige Einstellungen vornehmen. Die Datei mit allen Einstellungen lässt sich [hier](https://github.com/ViaVersion/ViaVersion/blob/master/common/src/main/resources/assets/viaversion/config.yml) finden.

## 4. Tipps

* Es ist am besten, wenn der Server mit dem Plugin auf Version 1.8.8 läuft, damit sich so viele Versionen wie möglich mit dem Server verbinden können.

## 5. Add-Ons (Erweiterungen) für ViaVersion

Als offizielle Erweiterungen für ViaVersion gibt es z.B. noch ViaBackwards, dieses Plugin fügt Unterstützung für die Versionen 1.9 bis 1.19.3 auf 1.19.4-Servern hinzu und ViaRewind, welches nochmals zwei weitere Versionen (1.8 - 1.8.9 und 1.7 - 1.7.10) auf 1.19-Servern erlaubt.
