# Minecraft Version wechseln

Um die Version deines Minecraft Servers zu wechseln, gehe auf

{% embed url="https://gamingcontroller.eu/" %}

und wähle dort den Minecraft Server aus.

Klicke anschließend auf "**Startkonfiguration**".

![Startkonfiguration Pterodactyl](../.gitbook/assets/minecraft-version-wechseln-bar.png)

Unter dem Feld "Startbefehl" wird dir "**Minecraft Version**" angezeigt. Um mit der neusten Minecraft Version zu spielen, trage in das Feld

```bash
latest
```

ein.

Solltest du z.B. mit der 1.18.2 spielen wollen, trage in das Feld

```bash
1.18.2
```

ein.

![Minecraft Version ändern](../.gitbook/assets/minecraft-version.png)

Damit der Server ordentlich starten kann, muss unter "Startkonfiguration" noch die richtige Java Version angegeben werden. Dazu gehe auf "**Docker Image**" und wähle die passende Version aus.

![Java Version auswählen](../.gitbook/assets/minecraft-java-version.png)

<details>

<summary>Welche Java Version benötige ich?</summary>

1.8.x Java 8 & Java 11 & Java 16 ( server.properties= use-native-transport: false ) 

1.9.x Java 8 & Java 11

1.10.x Java 8 & Java 11

1.11.x Java 8 & Java 11

1.12.x Java 11

1.13.x Java 11

1.14.x Java 11

1.15.x Java 11

1.16.x Java 11 & Java 16 ( 1.16.5 )

1.17.x Java 17

1.18.x Java 17

1.19.x Java 17

</details>

Nachdem die Version und die Java Version ausgewählt wurde, muss der Server einmal neuinstalliert werden. Dazu klicke auf "Einstellungen" und anschließend auf "**REINSTALL SERVER**".

{% hint style="info" %}
**Es gehen dabei keine Daten verloren.**
{% endhint %}

Sobald der Installationsprozess abgeschlossen ist, kann der Minecraft Server gestartet werden.
