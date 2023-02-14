# Mehrere Welten auf einem Java Edition Server installieren

Wenn man z.B. einen Citybuild-Server bei MC-Host24 hat und dort bereits eine Hauptwelt ist, möchte man sicherlich jetzt noch eine Farmwelt haben, in der Spieler z.B. Ressourcen farmen und sich erarbeiten können. Dafür eignet sich am besten das kostenlose Plugin Multiverse-Core, welches man sich [hier](https://dev.bukkit.org/projects/multiverse-core) herunterlädt.

## 1. Installation des Plugins

Als erstes muss man sich das Plugin vom oben stehenden Link herunterladen. Danach muss es vom lokalen Desktop in den "plugins"-Ordner bewegt werden. Dazu muss man sich mit einem sogenannten FTP-Client mit dem Gameserver verbinden, dort zum oben genannten Ordner navigieren und das Plugin dort ablegen. Nach einem erfolgreichen Server-Neustart sollte Multiverse-Core jetzt laden.

## 2. Eine Welt erstellen

Um eine weitere Welt für den Server zu erstellen, öffnet man entweder die Server-Konsole oder den Ingame-Chat, falls man bereits den Server neugestartet hat und sich mit ihm verbunden hat und gibt dort folgendes ein:

Beispiel:

```bash
/mv create Beispiel normal -t normal -s 1234567890 -a true
```

```bash
/mv create WELTNAME UMGEBUNG -t WELTTYP -s STARTWERT -a STRUKTUREN JA/NEIN
```

Jetzt lädt der Server eine neue Welt und gibt die Nachricht "Starting creation of world Beispiel" ein. Wenn dies erfolgreich war, wird "COMPLETE" ausgegeben, ansonsten "FAILED".

## 3. Die Welt besuchen

Damit man die soeben erstellte Welt nach erfolgreicher Erstellung besuchen kann, muss man <b>im Spiel-Chat</b> den Befehl /mv tp Spielername Beispiel eingeben. Jetzt lädt der Client ein bisschen und man sollte nach ein paar Sekunden (standardmäßig 3, maximal 10 bis 15) in der soeben erstellten Welt erscheinen, wenn man alles richtig eingegeben hat. Will man wieder zurück zur Hauptwelt, muss man den selben Befehl nochmal eingeben und dabei den Weltnamen ersetzen.

## 4. Multiverse-Addons

Für Multiverse-Core gibt es noch einige weitere Zusatz-Add-Ons, mit denen man sich z.B. Portale erstellen kann oder eigene Inventare verwalten kann.
