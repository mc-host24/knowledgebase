# Terraria Server installieren

Im Mai 2011 veröffentlichte ein vierköpfiges Entwicklerteam unter dem Namen Re-Logic auf Steam die erste Version des Sandbox-Games Terraria für Windows-User. Mittlerweile ist das Spiel auch für Linux und Mac, PlayStation, Xbox, iOS, Android und Nintendo-Geräte verfügbar. Wer die zufällig generierte Spielwelt mit anderen Spielern erkunden möchte, kann sich am besten einen eigenen Terraria-Server erstellen. Wie das funktioniert und warum gemietete Hardware hierfür die beste Lösung darstellt, erfährt man in diesem Ratgeber.

## Hosting
### Hosting auf dem eignen PC
Will man Terraria online mit anderen Nutzern spielen, so gibt es hierfür zwei Optionen: Man nutzen die „Host & Play“-Funktion im Terraria-Client, um ein eigenes Online-Spiel direkt auf Ihrem Gerät zu hosten. Andere Spieler können der Welt dann wahlweise mit oder ohne Passwort beitreten. Wird das Spiel beendet, stoppt in diesem Fall aber automatisch auch der Server. Wer dies verhindern will, muss auf Option Nummer Zwei zurückgreifen und die Dedicated-Server-Software von Terraria ausführen. Solange diese Anwendung läuft, kann man selbst und andere Spieler sich im Spielclient über den Punkt „Join via IP“ mit dem Terraria-Server verbinden.

### Hosting auf dedizierter Hardware
Theoretisch ist es auch möglich, zuletzt genannte Software für einen dedizierten Server auch auf dem eigenen Heim-PC laufen zu lassen. Für einen durchgängigen Betrieb des Terraria-Servers müsste dieses Gerät aber rund um die Uhr laufen, was sehr hohe Stromkosten zur Folge hat. Auch die Wartung der Hardware, sollte beispielsweise mal ein Teil kaputtgehen, liegt in eigener Verantwortung. Zudem ist eine stabile und leistungsstarke Internetanbindung unverzichtbar, um allen Spielern ein möglichst reibungsloses Spielerlebnis bieten zu können. Die einfachere und bequeme Alternative besteht darin, das Terraria-Server-Hosting in die Hände eines Providers zu geben, der sich um alle elementaren Punkte wie die Verfügbarkeit, die Wartung oder die Performance des Terraria-Servers kümmert.

## Systemanforderungen
Die Anforderungen, die ein Terraria-Server an die Hardware stellt, sind – aufgrund der 2D-Optik wenig überraschend – relativ minimalistisch. Entscheidend ist insbesondere der Arbeitsspeicher: Hierfür geben die Entwickler den Startwert von 512 MB für eine kleine Spielwelt mit wenigen Spielern und ohne Modifikationen an. Für größere Welten sollte man aber mindestens 1 GB bzw. 2 GB (ab 10 Spieler) bereithalten. Plant man einen Terraria-Server für mehr als 50 Spieler, so sind allerdings 4 GB oder mehr zu empfehlen. Hinzu kommt der Hauptspeicherbedarf des Betriebssystems – für Windows Server 2019 wären dies beispielsweise 512 MB bzw. 2 GB Arbeitsspeicher (ohne bzw. mit grafischer Oberfläche).

CPU und Festplattenspeicher spielen beim Terraria-Server-Hosting kaum eine Rolle. Ein Prozessor mit 2 GHz sollte einer einzelnen Serverinstanz die notwendige Rechenpower verleihen. In puncto Speicherplatz reicht es, wenn Sie einige wenige Gigabyte zur Verfügung haben, um langfristig genügend Platz für die Nutzerdaten zu besitzen. Hinzu käme auch in diesem Fall der Ressourcenbedarf des Betriebssystems – für das erwähnte Windows-System, das wir auch im nachfolgenden Tutorial einsetzen, wäre also zusätzlich 32 GB Festplattenspeicher und ein 1,4-GHz-Prozessor (64-Bit) einzuplanen.

## Windows-Anleitung
### 1. Remote-Verbindung zum Server herstellen
Zuallerst muss man sich mit dem Server verbinden. Hierfür muss man sich ins Web-Panel von MC-Host24 einlogen und dort entweder einen Terraria-Server auf einem bereits bestehendem Gameserver installieren oder einen neuen mieten.

### 2. Den Server via Steam installieren
Die Serveranwendung für Terraria wird automatisch dazu installiert, wenn das Spiel auf Steam installiert wird. Wir haben das 2D-Game über Steam bezogen, wo man Game und Server bequem über die Bibliothek herunterladen können, indem man nach dem Kauf auf den Terraria-Eintrag klickt und den Download über den gleichnamigen Button startet.

### 3. Ein XNA-Framework installieren
Insofern es noch nicht auf dem Server installiert wurde, gilt es im nächsten Schritt, die aktuelle Version des Microsoft XNA Frameworks herunterzuladen und zu installieren. Das Framework beinhaltet die erforderlichen Laufzeitkomponenten zum Ausführen eines Terraria-Servers. Die Dateien für die Installation erhält man direkt auf der Microsoft-Website.

### 4. Konfiguration
Nach der Installation – das Standardverzeichnis lautet [b]C:\Program Files (x86)\Steam\steamapps\common\Terraria[b] – sind die folgenden vier Dateien für das Management und den späteren Start des Terraria-Servers sehr wichtig:

TerrariaServer.exe: Hauptdatei für Terraria-Server; kann eigenständig ausgeführt werden
serverconfig.txt: Konfigurationsdatei, in der alle wichtigen Parameter des eigenen Terraria-Servers definiert werden können
start-server.bat: Batch-Datei, mit der sich der Server auf Grundlage der serverconfig.txt starten lässt; enthält ein Loopback, um den Server nach einem Crash automatisch neu zu starten
start-server-steam-friends.bat: BAT-Datei zum Start eines Servers auf Grundlage der „Host & Play“-Funktion via Konsole; ermöglicht das Zusammenspiel mit Steam-Freunden

Noch vor dem ersten Start kann man in der serverconfig.txt das grundlegende Setup des Terraria-Servers festlegen. Die Textdatei lässt dabei mit jedem beliebigen Editor öffnen – zu den möglichen Einstellungen zählen unter anderem Name und Passwort des Servers, die gewünschte maximale Spielerzahl, der Schwierigkeitsgrad oder die Serversprache. Eine ausführliche Auflistung lassen im Abschnitt „Server config file“ im offiziellen Terraria-Wiki finden.

### 5. Portfreigabe
Um externen Nutzern den Zugriff auf den Server zu ermöglichen, muss man den TCP- und UDP-Port 7777 öffnen. Die Terraria-Serveranwendung nutzt die beiden Netzwerk-Ports zu Kommunikationszwecken. Beide Ports müssen in der Firewall freigeschaltet werden, bevor der Server gestartet wird.

### 6. Start
Sobald die Ports freigegeben sind, kann man den Terraria-Server starten. Die einfachste Lösung hierfür ist die bereits erwähnte Batch-Datei mit dem Namen start-server.bat. Navigieren Sie also in das Terraria-Verzeichnis und starten die Stapelverarbeitungsdatei und damit auch den Server per Doppelklick.

Wurden entscheidende Angaben, wie den Schwierigkeitsgrad oder den Namen der Spielwelt bis dato noch nicht in der Konfigurationsdatei gemacht, fragt die Kommandozeile diese nun der Reihe nach ab. Im Anschluss startet die Kreation des Servers, die je nach Größe und Seed einige Minuten in Anspruch nehmen kann. War der Prozess erfolgreich, präsentiert die Eingabeaufforderung eine entsprechende Erfolgsmeldung.

### 7. Mit dem Server verbinden
Will man oder seine Freunde sich nun mit dem neu aufgesetzten Terraria-Server verbinden, sind dafür die folgenden Schritte erforderlich:

1. Terraria in gewohnter Manier staten.
2. Auf „Mehrspieler“ klicken.
3. Die Option „Über IP beitreten“ anklicken und dann einen Avatar auswählen.
4. Die IP-Adresse des Servers eingeben (mit angehängtem :7777 für den Port).
5. Auf „Annehmen“ klicken.
6. Das Serverpasswort eingeben, sofern eines vergeben wurde.
