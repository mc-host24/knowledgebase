## Wie werde ich Admin (OP-Rechte)?
Um Operator-Rechte auf deinen Server zu erhalten, öffne das [**Webinterface**](https://panel.mc-host24.de/) (Multicraft).
Klicke im **Webinterface** auf ➜ **Konsole** und gebe den **Command** `op SPIELERNAME` ein. [**▶️Video dazu**](https://youtu.be/AQNvqg24wIc)
```bash
op SPIELERNAME
``` 
{% embed url="https://youtu.be/AQNvqg24wIc" %}


## Wie lade ich eine eigene Welt hoch?
Per FTP können Welten problemlos per Drag&Drop hochgeladen werden.
Ein [**▶️Video dazu**](https://youtu.be/oSQebkjCFDA) haben wir auf YouTube hochladen.
{% embed url="https://youtu.be/oSQebkjCFDA" %}


## Wie aktiviere ich eine Whitelist?
Um eine Whitelist auf auf deinem Server einzurichten gebe im Minecraft Chat oder in der Server-Konsole den Befehl 
```bash
/whitelist on
```
ein. Dies aktiviert, dass nur Spieler, die auf der sogenannten Whitelist stehen, sich mit dem Server verbinden und spielen können.

Um einen Spieler zur Whitelist hinzuzufügen verdende den Command 
```bash
/whitelist add SPIELERNAME
```

## Wie füge ich ein Server-Icon ein?
Das Server-Icon muss eine Größe von 64*64 Pixel, sowie das Format .png besitzen. Anschließend wird die Datei "server-icon.png" in das Hauptverzeichnis eingefügt.

Natürlich muss das Server-Icon auch genau "server-icon" heißen, damit es geladen werden kann.

## Es werden keine Skins angezeigt. Wieso?
Sollten die Skins bei einem Gameserver nicht zu sehen sein wird dies in der Regel an der Einstellung "online-mode=false" liegen. Dies verhindert, dass sich der Gameserver mit den Mojang-Servern verbindet.

## Wie erstelle ich eine neue Welt?
Du musst den Server stoppen, den Weltordner löschen (standardmäßig heißt der "world") und den Server wieder starten, dann wird automatisch eine neue generiert.
Alternativ kann in der server.properties die Einstellung "level-name=" geändert werden. Es wird dann in dem dort angegeben Ordner eine neue Welt generiert. Die alte Welt bleibt dabei erhalten. So können beliebig viele Welten erstellt werden. Mehrere Welten sind auch mit dem kostenlosen Plugin "Multiverse-Core" möglich, welches hier heruntergeladen werden kann: [Downloadlink](https://www.spigotmc.org/resources/multiverse-core.390/). Alternativ kann man sich auch das Tutorial [Mehrere Welten mit Multiverse](minecraft-server/mehrere-welten.md) anschauen.
