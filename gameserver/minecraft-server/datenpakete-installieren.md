# Datenpakete auf dem Vanilla Server installieren

Für Minecraft: Vanilla Server aller Art gibt es auch Datenpakete. Das sind kleinere Mods mit beschränkterem Funktionsumfang, wo man aber kein Java lernen muss, da diese in JSON geschrieben werden. Sie können z.B. benutzerdefinierte Funktionen oder Erfolge zum Spiel hinzufügen. Dieses Tutorial zeigt, wie sie installiert und optional auch passend konfiguriert werden.

## 1. Download & Installation

Als erstes muss man sich ein Datenpaket, welches man gerne auf seinem Server haben möchte, herunterladen. [Hier](https://planetminecraft.com) gibt es z.B. coole Datenpakete. Für diese Anleitung nutzen wir [dieses Datenpaket](https://www.planetminecraft.com/data-pack/custom-trees-from-saplings/). Dort auf die blaue "Download"-Schaltfläche neben oder unter den Bildern klicken, die Werbung überspringen und dann sollte es im "Downloads"-Ordner des PCs landen.

Danach muss man zum Weltordner navigieren (in diesem Fall SERVERVERZEICHNIS/WELTNAME/datapacks und es dort entweder per Drag & Drop oder per FTP-Client hochladen.

## 2. Datenpakete deaktivieren und aktiveren

Als nächstes wollen wir das oben stehende Datenpaket aktivieren, so dass wir seine Funktionen auch auf dem Vanilla-Server benutzen können. Dies machen wir im Spiel mit dem Befehl <code>/datapack enable "file/custom-trees-for-saplings"</code>. Jetzt müsste eine Meldung kommen, dass das Datenpaket erfolgreich aktiviert wurde, falls man alles richtig gemacht haben sollte. Wenn man jetzt das Datenpaket aber nicht mehr auf dem Server haben möchte, führt man den Befehl <code>/datapack disable "file/custom-trees-for-saplings"</code> aus. Dann müsste das Datenpaket wieder deaktivert werden.

## 3. Spielen

Wenn man alles richtig gemacht hat, das Datenpaket hochgeladen hat, es erfolgreich aktiviert wurde und den Server neugestartet hat, kann man mit dem Datenpaket in der aktuellen Server-Welt spielen. Viel Spaß!
