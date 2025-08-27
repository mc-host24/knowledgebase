# FiveM Server einrichten
In dieser Anleitung könnt ihr lesen, wie ihr euren FiveM Server das erste Mal einrichten könnt.

{% hint style="warning" %}
**Wenn du dich nicht auf deinen FiveM Server per connect-Befehl verbinden kannst, überprüfe bitte deine Firewall oder gebe den Port für deinen Server frei (Standard 30120 = CFX / 40120 = txAdmin)**
{% endhint %}

1. Wenn du deinen FiveM Server auf einem Windows Server startest, öffnet sich im Browser ein Fenster von txAdmin mit dem Code.<br>Auf einem Linux-Server musst du bei dir im Browser folgende URL aufrufen: `http://IP_DEINES_SERVERS:40120/` und gebe im Feld den Code ein, welcher in der Konsole des FiveM Servers angezeigt wird.

2. Wenn du auf `Link Account` gedrückt hast, wirst du gebeten, dich mit deinem CFX.re Account anzumelden. Wenn du diesen noch nicht hast, registriere dich über die offizielle [CFX.re Forum Seite](https://forum.cfx.re/)

![FiveM Link Account](https://docs.fivem.net/server-setup/windows-step2-2.png)

3. Setze ein sicheres Masterpasswort für deinen Account. Dieser kann nicht gelöscht werden und ist der "höchste" User deines FiveM Servers.

![FiveM Password](https://docs.fivem.net/server-setup/windows-step2-4.png)

4. Drücke so lange "Next", bis du gebeten wirst deinen `Deployment Type` zu setzen. Hierbei möchte er wissen, ob du bereits einen Server hast, den du verwenden möchtest, ob du einen komplett leeren Server möchtest oder ein "Template" mit beliebten Frameworks wie ESX/QBCore für Roleplay Server. Wir empfehlen dir das ESX Template (Für dieses wird eine MySQL-Datenbank benötigt. Siehe folgende Seite um [MySQL zu installieren](phpmyadmin-PHP-8-installation.md))

![FiveM Template](https://docs.fivem.net/server-setup/windows-step2-7.png)

5. Wenn du keine besonderen Konfigurationen vornehmen möchtest wie z.B. die `git clone` URLs des Templates, klicke weiter, bis du deinen CFX.re Lizenzschlüssel eingeben musst.

![FiveM Key](https://docs.fivem.net/server-setup/windows-step2-12.png)

6. Gehe auf die [Keymaster](https://keymaster.fivem.net/) Seite von FiveM und melde dich mit deinem CFX.re Account an.

7. Gehe auf den Reiter "New Server" und gebe einen Namen deines Servers ein (Dieser ist beliebig), deine IP des Servers den du bei uns gemietet hast sowie einen Server Type. Dieser ist bei einem Rootserver in der Regel ein `Dedicated Server`. Als "Server Provider" gibst du `MC-Host24` ein.

8. Kopiere diesen Schlüssel und gebe ihn auf deiner txAdmin Oberfläche ein.

9. Klicke so lange auf "Next", bis du auf deiner allgemeinen Oberfläche deines Servers landest.

10. Du kannst deinen Server nun entweder in der FiveM-Server Liste über deinen Namen finden oder mit dem `connect`-Befehl. Drücke hierfür F8 und gebe folgenden Befehl ein
```bash
connect IP_DEINES_SERVERS
```