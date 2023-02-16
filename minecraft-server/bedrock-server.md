# Einen Minecraft: Bedrock Edition Server konfigurieren

Hallo! Dieses Tutorial soll dir zeigen, wie du dir deinen eigenen Minecraft: Bedrock Edition Server bei MC-Host24 konfigurieren kannst.

## 1. Den Server erstellen

Das ist ganz einfach! Dafür musst du oben in der Menüleiste auf "Gameserver" klicken, Minecraft Bedrock auswählen, den Arbeitsspeicher (RAM) auswählen und dann auf "Bestellen" klicken. Jetzt dauert es etwas, bis der Server eingerichtet wurde. Sobald das erledigt ist, musst du dich per FTP mit dem Server verbinden oder den integrierten Datei-Editor benutzen und die "<b>Server.properties</b>"-Datei öffnen.

## 2. Konfiguration

Nachdem du die Datei "<b>Server.properties</b>" geöffnet hast, kannst du dort verschiedene Einstellungen vornehmen. Die folgenden Einstellungen sind mit einer dazu passenden Erklärung und den möglichen Einstellungs-Werten verfügbar:

### server-name

Dieser Wert ist der Name des Bedrock Servers, der an den Client gesendet wird. Es sind hier alle Zeichen bis auf Semikolons (;) erlaubt

### gamemode

Dieser Wert legt den Standard-Spielmodus des Bedrock Servers fest. Es sind hier nur die folgenden Werte erlaubt: "creative", "survival", "adventure" und "spectator".

### force-gamemode

Dieser Wert zwingt den Client dazu, den Spielmodus in der "gamemode"-Zeile zu benutzen, falls es auf "true" gestellt wurde. Die möglichen Werte sind hier: "true" oder "false".

### difficulty

Dieser Wert legt die Schwierigkeit der Serverwelt fest. Die folgenden Werte sind möglich: "peaceful", "easy", "normal" und "hard".

### allow-cheats

Dieser Wert legt fest, ob Cheats wie z.B. /gamemode, /kill, /fill, /difficulty etc. erlaubt sind. Die möglichen Werte sind: "true oder "false".

### max-players

Dieser Wert legt die maximale Anzahl an gleichzeitigen Spielern fest, die sich mit dem Server verbinden können. Mögliche Werte sind: "0" bis "2147483647".

### online-mode

Dieser Wert legt fest, ob alle Spieler, die dem Server beitreten wollen, bei Xbox Live angemeldet sein müssen.

### allow-list

Dieser Wert erzwingt, dass alle Spieler, die dem Server beitreten wollen, in der separaten "<b>allowlist.json</b>"-Datei gelistet sein müssen.

### server-port

Dieser Wert legt den Port des Servers fest. Der Port ist eine fünfstellige Nummer, die auf dem WLAN-Router freigegeben werden muss, damit dieser von außen erreichbar ist. Gilt nur für IPv4-Verbindungen. Die möglichen Werte sind hier: "0" bis "65535". Standard ist 19132.

### server-portv6

Dieser Wert hat die gleiche Funktion wie "<b>server-port</b>", ist aber eher für IPv6-Verbindungen gedacht. Hier sind die möglichen Werte 0 bis 65535. Standard ist 19133.

### view-distance

Dieser Wert legt die Sichtweite auf dem Server fest, also wie weit man in die Ferne schauen kann. Trägt man hier z.B. 8 als Zahl ein, so kann man 8 Chunks weit in die Ferne sehen. Alle Werte von 5 bis 32 sind hier erlaubt.

### tick-distance

Dieser Wert legt fest, wie weit die Welt vom Spieler entfernt Ticks auslösen soll. Alle Werte von 4 bis 12 sind hier möglich.

### player-idle-timeout

Dieser Wert legt die Anzahl an Minuten fest, die ein Spieler inaktiv sein soll, um gekickt zu werden. Alle Werte von 1 bis 60 sind hier möglich, falls der Wert auf 0 gesetzt wurde, so können Spieler für immer inaktiv sein und werden nie gekickt.

### max-threads

Dieser Wert gibt an, wie viele sogenannte Threads der Server nutzen soll. Die möglichen Werte sind hier 1 bis 9. Falls der Wert auf 0 gesetzt wurde oder komplett fehlt, werden so viele Threads wie möglich benutzt.

### level-name

Dieser Wert legt den Namen der Serverwelt fest. Hier sind alle Buchstaben, Zahlen und sonstige Zeichen bis auf /\n\r\t\f`?*\\<>|\": erlaubt.

### level-seed

Dieser Wert legt das Aussehen der Welt fest. Möchte man jetzt z.B. eine Welt mit einem Fluss am Anfang (Spawn) generieren, lohnt sich z.B. der Seed 49128. Hier sind alle Werte von -9223372036854775808 bis 9223372036854775807 möglich.

### level-type

Dieser Wert legt den Typen der Welt, also wie sie generiert werden soll, fest. Mögliche Werte sind hier: <b>default</b> und <b>flat</b>.

### default-player-permission-level

Dieser Wert legt die standardmäßigen Berechtigungen, die jeder Spieler auf dem Server haben soll, fest. Will man jetzt z.B., dass sich neue Spieler erstmal nur umschauen möchten, kann man hier den passenden Wert eintragen. Mögliche Werte sind hier: <b>visitor</b>, <b>member</b> und <b>operator</b>. Standard ist <b>member</b>.

### texturepack-required

Dieser Wert gibt an, ob ein sogenanntes "Texturenpaket", also eine kleinere Client-Modifizierung, die Minecraft's Spiel-Texturen ändert. Standardwert ist hier <b>false</b>.

### content-log-file-enabled

Dieser Wert legt fest, ob beim nächsten (Neu)start des Servers eine sogenannte "Content-Log-Datei", die z.B. Fehler auf dem Server speichert, angelegt werden soll. Standardwert ist hier <b>false</b>.

### compression-threshold

Dieser Wert bestimmt die kleinste zu komprimierende Größe der rohen Netzwerknutzlast. Standard ist hier 1 und die möglichen Werte sind hier 0 bis 65535.

### server-authoritative-movement

Aktiviert die autoritative Bewegung des Servers. Bei "server-auth" gibt der Server lokale Benutzereingaben wieder an den Server und sendet Korrekturen nach unten, wenn die Position des Clients nicht mit der des Servers übereinstimmt. Wenn "server-auth-with-rewind" aktiviert ist und der Server eine Korrektur sendet, werden die Clients angewiesen, die Zeit zurück zur Korrekturzeit zu spulen, die Korrektur anzuwenden und dann alle Eingaben des Spielers seitdem wiederzugeben. Dies führt zu sanfteren und häufigeren Korrekturen. Korrekturen erfolgen nur, wenn <b>correct-player-movement</b> auf true gesetzt ist. Mögliche Werte sind hier client-auth, server-auth und server-auth-with-rewind.

### player-movement-score-threshold

Die Anzahl der inkongruenten Zeitintervalle, die erforderlich sind, bevor abnormales Verhalten gemeldet wird.
Ist immer deaktiviert, wenn "server-authoritative-movement" aktiviert ist.

### player-movement-action-direction-threshold

Der Betrag, um den sich die Angriffsrichtung und die Blickrichtung des Spielers unterscheiden können.
Zulässige Werte: Jeder Wert im Bereich von [0, 1], wobei 1 bedeutet, dass die Blickrichtung des Spielers und Angriffsrichtung des Spielers genau übereinstimmen muss und ein Wert von 0 bedeutet, dass die beiden Richtungen sich um bis zu einschließlich 90 Grad unterscheiden können.

### player-movement-distance-threshold

Die Differenz zwischen Server- und Client-Position, die überschritten werden muss, bevor abnormales Verhalten erkannt wird. Ist immer deaktiviert, wenn "server-authoritative-movement" aktiviert ist.

### player-movement-duration-threshold-in-ms

Die Zeitdauer, in der die Server- und Client-Positionen nicht synchron sein können (wie durch Player-Movement-Distance-Threshold definiert), bevor der Wert für abnormale Bewegungen erhöht wird. Dieser Wert wird in Millisekunden angegeben. Ist immer deaktiviert, wenn "server-authoritative-movement" aktiviert ist.

### correct-player-movement

Wenn auf <b>true</b> gesetzt, wird die Client-Position auf die Server-Position korrigiert, wenn der Bewegungswert den Schwellenwert überschreitet.

### server-authoritative-block-breaking

Wenn auf <b>true</b> gesetzt, berechnet der Server Block-Mining-Operationen synchron mit dem Client, damit er überprüfen kann, ob der Client in der Lage sein sollte, Blöcke zu brechen, wenn er dies für möglich hält.

## 3. Abschluss

Ich hoffe sehr, dass dir dieses Tutorial gefallen hat! Wenn ja, kannst du jetzt auf deinem neu eingerichteten Minecraft: Bedrock Edition Server spielen. Viel Spaß!
