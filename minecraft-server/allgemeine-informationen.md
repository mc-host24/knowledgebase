## Wie werde ich Admin (OP)
Um Operator deines Servers zu werden öffne das Webinterface. Dies findest du unter "Meine Server -> Webinterface".
Klicke auf "Konsole" und gebe den Command "op SPIELERNAME" ein.

## Wie lade ich eine eigene Welt auf meinem Server hoch?
Per FTP können Welten problemlos per Drag&Drop hochgeladen werden.
Ein Video dazu haben wir auf YouTube hochladen.
{% embed url="https://www.youtube.com/watch?v=zvb7oUQ_BMQ" %}

## Wie richte ich eine Whitelist ein?
Um eine Whitelist auf auf deinem Server einzurichten gebe im Minecraft Chat oder in der Server-Konsole den Befehl 
```bash
/whitelist on
```
ein. Dies aktiviert, dass nur Spieler, die auf der Whitelist stehen, sich mit dem Server verbinden können.

Um einen Spieler zur Whitelist hinzuzufügen verwende den Command 
```bash
/whitelist add SPIELERNAME
```

## Es werden keine Skins angezeigt. Wieso?
Sollten die Skins bei einem Gameserver nicht zu sehen sein wird dies in der Regel an der Einstellung "online-mode=false" liegen. Dies verhindert, dass sich der Gameserver mit den Mojang-Servern verbindet.

## Wie erstelle ich eine neue Welt?
Du musst den Server stoppen, den Weltordner löschen (standardmäßig heißt der "world") und den Server wieder starten, dann wird automatisch eine neue generiert.
Alternativ kann in der server.properties die Einstellung "level-name=" geändert werden. Es wird dann in dem dort angegeben Ordner eine neue Welt generiert. Die alte Welt bleibt dabei erhalten. So können beliebig viele Welten erstellt werden. Mehrere Welten sind auch mit dem kostenlosen Plugin "Multiverse-Core" möglich, welches hier heruntergeladen werden kann: [Downloadlink](https://www.spigotmc.org/resources/multiverse-core.390/). Alternativ kann man sich auch das Tutorial [Mehrere Welten mit Multiverse](minecraft-server/mehrere-welten.md) anschauen.

## Was heißt unlimited RAM (Arbeitsspeicher)?
Unbegrenzter RAM bedeutet, dass wir sicherstellen, dass so viel RAM ausgeben wird, wie der Server benötigt.