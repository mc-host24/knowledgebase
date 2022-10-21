## Wie werde ich Admin (OP)
Um Operator deines Servers zu werden öffne das Webinterface. Dies findest du unter "Meine Server -> Webinterface".
Klicke auf "Konsole" und gebe den Command "op SPIELERNAME" ein.

## Wie lade ich eine eigene Welt auf meinem Server hoch?
Per FTP können Welten problemlos per Drag&Drop hochgeladen werden.
Ein Video dazu haben wir auf YouTube hochladen.
{% embed url="https://youtu.be/oSQebkjCFDA" %}

## Wie richte ich eine Whitelist ein?
Um eine Whitelist auf auf deinem Server einzurichten gebe im Minecraft Chat den Befehl 
```bash
/whitelist on
```
ein.

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
Alternativ kann in der server.properties die Einstellung "level-name=" geändert werden. Es wird dann in dem dort angegeben Ordner eine neue Welt generiert. Die alte Welt bleibt dabei erhalten. So können beliebig viele Welten erstellt werden.
