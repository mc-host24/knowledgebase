## Wie kann ich meinen Server verwalten?

Um mit der Verwaltung deines Servers zu beginnen musst du dich zuerst in unserem **Webinterface** anmelden. Dort kannst du dann deinen Server auswählen und mit der Verwaltung beginnen.

Das Webinterface findest Du, wie im nachfolgenden Screenshot gezeigt unter Meine Server, Gameserver. 
Dort kannst du dann deinen Server auswählen und mit dich mit dem Button "Ins Webinterface einloggen" anmelden.

![Webinterface](../../.gitbook/assets/gamecp-login.png)

{% hint style="info" %}
Bitte beachte die Anweisungen zur Anmeldung, welche du unter dem Button "Ins Webinterface einloggen" findest.
{% endhint %}


<details>
<summary>Welten</summary>
  ### Wie kann ich die Welt meines ARK-Servers anpassen?

In ARK : Survival Evolved gibt es diverse Karten die man Spielen kann. Neben den 12 Karten die vom Spiel selber mitgeliefert werden, gibt es auch noch verschiedne Karten die man durch Mods hinzufügen kann.
Man sollte jedoch zwingend beachten, dass es Karten gibt, die man von den erstellern **zuätzlich, kostenpflichtig** erwerben muss und Karten, die man sich kostenlos herunterladen kann. 
Unteranderen gibt es folgende Karten:

TheIsland(Kostenlos, Vorinstalliert, Story)<br>
TheCenter(Kostenlos)<br>
Ragnarok(Kostenlos)<br>
ScorchedEarth_P(Kostenpflichtig, Story)<br>
Aberration_P(Kostenpflichtig, Story)<br>
Extinction(Kostenpflichtig, Story)<br>
Valguero_P(Kostenpflichtig, Story)<br>
Genesis(Kostenpflichtig, Story)<br>
CrystalIsles[Kostenlos]<br>
Gen2(Kostenpflichtig, Story)<br>
Fjordur(Kostenlos)<br>
Um deinen Server auf eine bestimmte Karten einzustellen, musst du als erstes wie oben beschrieben in Webinterface. Nachdem du angemeldet bist, musst du den Server auswählen, den du bearbeiten willst. Jetzt musst du dein Karte auswählen. Dies geschieht unter dem Reiter **"Startup"**(Siehe Grafik).<br>
![StartseiteWebinterface](https://github.com/user-attachments/assets/6ecefd75-734a-4215-9cc0-0b1b2da2c1e4)
(Hier kann man übrigens auch wie oben erklärt, das Admin Passwort, den Server-Namen, die Maximale Spieleranzahl und die zusätzlichen Startargumente verändern.)
Dort suchst du dann nach dem Eingabe Feld **"Server Map"** und schreibst den Namen von einer der oben gennanten Maps in das Feld. Sofort wird der eintrag gespeichert und beim Hochfahren wird nun diese Map gespielt.
Neben diesen offiziellen Welten gibt es auch eine Vielzahl an Mod-Welten, die du auf deinem Server nutzen kannst.
Diese findest unteranderem im [Steam Workshop](https://steamcommunity.com/app/346110/workshop/).
Zum nutzen dieser musst du die Mod-IDs in der [serverconfig.ini](https://ark.gamepedia.com/Server_Configuration) eintragen.
</details>
<details>
<summary>Server Konfigurationen</summary>
Umd deinen Server konfigurieren, also z.B. die Multiplikatoren beim Rohstoff-Abbau zu verändern, mussst die die UserGameSettings.ini oder die Game.ini Datei verändern. Hierbei bezieht sich die Game.ini auf fortgeschrittene Einstellungn und die UserGameSettings.ini eher auf die Grundeinstellungen. <br>
  Um diese zu finden, drückst du oben auf den Reiter Files, und dann folgst du diesem Pfad: /ShooterGame/Saved/Config/LinuxServer/
Um alle Werte zu finden die du verändern kannst nutze den Eintrag im Offiziellen [Ark-Wiki](https://ark.wiki.gg/wiki/Server_configuration). Hier findest du viele Einstellungen, jedoch widerrum auch nicht alle. Daher, solltest du nach besonders spezifischen Einstellungen online suchen. Hier gibt es oft Hilfe von Ark-Nutzern auf [Reddit](https://Reddit.com) oder [SurviveTheArk](https://survivetheark.com/) <br>
Übrigens kann man hier auch viele Einträge für die zusätzlichen Startargumente finden.<br>
</details>
<details>
<Summary>RAM</Summary>
<strong>Wie viel RAM brauche ich für meinen ARK-Server?</strong> <br>
Wie viel RAM du brauchst hängt von verschiedenen Faktoren ab: <br>
Welche Karte? <br>
Wie viele Spieler? <br>
Wie lang spielt ihr auf der Map? <br>
Welche Mods/Plugins wollt ihr installieren? <br>.
jede Map hat eine andere Größe und andere Komplezität, daher sit der RAM verbrauch pro Map auch sehr unterschiedich. Hier daher eine Kurzer Übersicht:
TheIsland: 3.5-4.5GB <br>
TheCenter: 3-4GB <br>
ScorchedEarth_P: 3-4GB <br>
Ragnarok: 4-5GB <br>
Abberation_P: 3-4GB <br>
Extinction: 3-4GB <br>
Valguero_P: 3-4GB <br>
Genesis: 5-6GB <br>
CrystalIsles: 5.5-6.5GB <br>
Gen2: 10-12.5GB <br>
LostIsland: 5.5-7GB <br>
Fjordur: 4-5GB <br>
Jeder spieler nimmt ungefähr 100MB Ram in anspruch. Außerdem steigert sich der RAM verbrauch exponenziell, umso länger man auf der Map spielt. Das liegt daran, das man beim Spielen normalerweise immer mehr Dinos zähmt, Strukturen baut, usw. diese verbrauchen jeweils immer RAM. Daher immer ein paar Gigabyte mehr RAM nehmen als eigentlich nötig.
</details>
<details>
<Summary>IP & PORT</Summary>
Die Ip und den Port zu finden an sich, ist nicht all zu schwer. Dafür geht man einfach ins Webinterface und sieht direkt unter Console, Startup oder Network, die IP und den PORT. Doch hier wird es oftmals etwas Kompliziert, wenn man die IP kopiert und den Server hinzufügen will, kann der Server manchmal trotzdem nicht gefunden werden.
<details>
<Summary>Server hinzufügem</Summary>
Um einen ARK-Server auf Steam hinzuzufügen, musst du zu allererst auf die Startseite von Steam gehen. Dort drückst du oben links auf "Anzeigen".
![Serverhinzu1](https://github.com/user-attachments/assets/d0a2b857-84e0-48ec-a54a-e5bd7690253e)
Dannach drückst du im Dropdown-Menü auf "Spielserver".
![Serverhinzu2](https://github.com/user-attachments/assets/e5c436ca-0a86-4aa8-8057-caafdafebc81)
Es sollte sich jetzt ein Fenster geöffnet haben, auf der oberen Seite dieses Fenster drückst du dann auf Favoriten. Hier werden dier dann deine bisjetzt Favorisierten Server angezeigt. Drücke nun auf das "+". 
![Serverhinzu3](https://github.com/user-attachments/assets/0839bf46-defa-4250-9a9f-e9444d00d9eb)
Es sollte sich wieder ein kleines Fenster geöffnet haben.
![Serverhinzu4](https://github.com/user-attachments/assets/6dde9dea-ee11-4235-9378-f921e0b3865f)
Dort gibst du nun die Ip und den Port deines Servers ein.
</details>
Sollte dies der Fall sein gibt es 2 Möglichkeiten. <br>
1. Gehe oben auf den Reiter Network und wähle einmen anderen Port aus.
![PORT](https://github.com/user-attachments/assets/1af13b48-238a-4832-a0d3-3ff9eafb22ba)
In diesem Beispiel ist das der Port 20186. <br>
Wemm anschließend startest du deinen Server neu und probiert erneut beizutreten, bzw. den Server hinzuzufügen. <br>
Wenn es immer noch nicht funkioniert bleibt nur noch die Möglichkeit 2: <br>
Bei Möglichkeit 2, musst du einfach nur probieren. In dem obrigen Beispiel war zwar der Port 20186 ausgewählt, aber am Ende konnte man nur über den Port 20187 beitreten. Nun sollte es geklappt haben. Falls nicht bleibt dir nur noch ein [Support-Ticket](https://mc-host24.de/support) zu öffnen.
</details>
