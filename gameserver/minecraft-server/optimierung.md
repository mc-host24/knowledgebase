# Deinen Minecraft-Server optimieren

Ein Minecraft-Server muss regelmäßig optimiert werden, z.B., wenn er laggt. Den Server zu optimieren ist ganz einfach, man entfernt z.B. nicht mehr benötigte Plugins oder Mods.

## Was passiert bei einer Optimierung?

Bei der Optimierung werden in den meisten Fällen sehr viele Einstellungen an den Servern geändert, wodurch sich die Verhaltensweise des Servers selbst teilweise stark ändert. Unter anderem werden einige Einstellungen heruntergeschaubt, wodurch der Server entlastet wird und dadurch mehr Performance erbringen kann. Damit das allgemeine Spielerlebnis jedoch nicht zu stark beeinflusst wird, sollte man hier immer die goldene Mitte finden.

Die Möglichkeiten einen Vanilla-Server zu optimieren, sind leider sehr begrenzt, da hierbei nur sehr wenige Einstellungsmöglichkeiten bereitstehen. Wir versuchen den Vanilla-Server dennoch etwas mehr Power zu verschaffen, indem wir folgende Maßnahmen durchführen:

## Beispiele
### Sichtweite

Hat man die Sichtweite seines Servers zu hoch eingestellt (z.B. 32 Chunks), kann es passieren, dass der Server abstürzt, weil ihn das sehr viel Performance kostet, denn er muss ja alle Chunks laden. Bei einem Vanilla-Server kann die Sichtweite in der Konfigurationsdatei "server.properties" angepasst werden, hierzu muss man der Wert "view-distance" anpassen. Um das Spielerlebnis selbst nicht besonders groß einzuschränken, sollte man diesen Wert auf 5-6 zu stellen, wodurch der Server bis zu 50% entlastet wird.

### Weltgenerierung

Das Generieren von neuen Bereichen in der Welt ist eine der aufwendigsten Aufgaben, die ein Minecraft Server ausführen muss. Wenn sehr viele Spieler gleichzeitig durch bisher unbesuchte Bereiche wandern oder fliegen (z.B. Elytra) kann dies sehr viel Performance kosten. Es ist jedoch möglich, einen bestimmten Bereich der Welt bereits zu generieren, bevor ein Spieler diesen besucht (sogenannte Pre-Generation). Dies kann mit Plugins wie Chunky oder WorldBorder erreicht werden. Dafür wird ein bestimmter Bereich festgelegt (z.B. Radius 10.000 Blöcke) und dieser dann generiert. Alternativ kann man auf einem Vanilla Server auch die zu generierenden Bereiche als Administrator selbst überfliegen und somit manuell generieren. Während dieser Generierung wird kurzzeitig sehr viel Leistung verbraucht, dafür ist die Performance während des eigentlichen Spielens besser.

## Datenkomprimierung

Auf einem Server werden permanent zwischen Server und den verbundenen Spielern ausgetauscht. Dabei werden etwas die Bewegungen von den Spieler selbst an den Server übertragen und der Server sendet dies dann wiederum an alle anderen Spieler. Aber auch Spieler-Aktionen oder Ereignisse in der Welt, wie Explosionen als Beispiel sind ein Teil der Daten, welche immer wieder übertragen werden.

Um die Regelmäßigkeit dieses Austausches etwas eleganter zu gestallten, kann man die Größe der gepackten Daten verdoppeln. Dies erzielt, dass der Server im Vergleich zu vorher nur 50% des Aufwandes betreiben muss, um die gleichen Daten mit den Spielern auszutauschen. Dafür muss in der "server.properties" Config der Wert "network-compression-threshold" angepasst werden. Er sollte am besten auf 512 gestellt werden.
