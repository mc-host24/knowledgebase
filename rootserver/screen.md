# Screen

## Einführung

**screen** ist ein Tool, welches Benutzern ermöglicht, mehrere virtuelle Konsolensitzungen innerhalb einer SSH-Sitzung zu verwalten. 
Es hilft dabei, mehrere Prozesse zu starten und diese auch nach dem Schließen der SSH-Sitzung weiterhin laufen zu lassen.
So laufen Prozesse wie ein Minecraft-Server weiterhin, auch wenn die SSH-Anwendung (z. B. PuTTY) geschlossen wurde.

## Installation

Um screen auf Debian oder Linux zu installieren, verwende diesen Befehl:
```bash
sudo apt install screen -y
```

## Verwendung

In dem folgenden Beispiel wird ein Minecraft-Server mit screen gestartet, allerdings funktioniert dies für alle möglichen Anwendungsfälle.

Du kannst einen Minecraft-Server mit Hilfe von screen starten, indem du den folgenden Befehl eingibst, oder ihn in dein Start-Skript einfügst:

```bash
screen -S minecraft java -jar server.jar
```

Der Parameter `-S` steht für "Session Name" und wird verwendet, um einen benutzerdefinierten Namen für den Screen festzulegen. In diesem Fall wird "minecraft" als Name für den Screen verwendet.
Gib deinen Screens am besten aussagekräftige Namen, beispielsweise den Namen deines Minecraft-Servers (Lobby-1, GunGame-1, Bedwars-2, ...).
Über diesen Namen greifen wir später wieder auf den screen zu.

{% hint style="warning" %} Bedenke, dass dein Start-Skript die benötigten Rechte braucht. Eine Erklärung zur Rechteverwaltung findest du [hier](https://docs.mc-host24.de/docs/rootserver/linux-grundlagen) {% endhint %}

Um den Screen zu verlassen, drücke die Tastenkombination `Strg + A` + `D`. Dadurch schließt sich der screen. Der Minecraft-Server läuft jedoch im Hintergrund weiter.

Wenn du zu einem späteren Zeitpunkt zum Screen zurückkehren möchtest, gib den folgenden Befehl ein:
```bash
screen -r minecraft
```

Du kannst dir alle offenen Screens mit dem folgenden Befehl anzeigen lassen:
```bash
screen -ls
```

Einen Screen kannst du beenden, indem du im Screen die Tastenkombination `Strg + C` drückst, oder in dem du außerhalb den folgenden Befehl eingibst:
```bash
screen -XS minecraft quit
```

## Mehr Informationen
[linux.die.net](https://linux.die.net/man/1/screen)<br>
[veek.it](https://www.veek.it/linux-screen-anleitung/)
