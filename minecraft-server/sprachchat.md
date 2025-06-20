# Dynmap auf dem Server installieren

Simple Voice Chat ist ein kostenloses Plugin, geschrieben von henkelmax, welches dem/den Spieler/n die Möglichkeit bietet, sich ingame auch ohne Chat miteinander zu unterhalten. Dafür braucht man einen PC und/oder Server mit viel Leistung und ähnlich wie bei GeyserMC einen zusätzlichen Port.

## 1. Herunterladen und installieren

Simple Voice Chat kann man sich unter anderem auf [Modrinth](https://modrinth.com/plugin/simple-voice-chat) herunterladen. Danach muss es nur noch entweder per Drag & Drop oder per FTP-Client in den "plugins" oder "mods"-Ordner bewegt werden und der Minecraft Server, auf dem man das Plugin gerade installiert hat, muss auch nochmal neugestartet werden.

## 2. Konfiguration

Simple Voice Chat generiert, so wie fast jedes andere Plugin, eine sogenannte Konfigurationsdatei. Diese kann bearbeitet werden. [Hier](https://modrepo.de/minecraft/voicechat/wiki/configuration) können alle Optionen der Konfigurationsdatei angeschaut werden und wo sich die Datei befindet. Allerdings heißt hier die Datei nicht wie üblich "config.yml", sondern "voicechat-server.properties". Darauf <b>muss</b> man achten, wenn man Simple Voice Chat benutzen will oder eigene Erweiterungen schreiben möchte.

## 3. Spielen mit Simple Voice Chat

Sollte ein anderer Spieler, der den Simple Voice Chat Mod auf seinem Client installiert hat, nun dem Server beitreten, kann man mit der Taste <b>V</b> die grafische Benutzeroberfläche des Mods bzw. des Plugins aufrufen. Nun kann man den Namen eines Spielers anklicken oder eine Gruppe erstellen und ihn dann dort hinzufügen.

{% hint style="warning" %}
Damit andere Spieler im Spiel auch gehört werden können, muss ein zusätzlicher Port freigegeben werden. Dies ist im grundsätzlich im Webinterface möglich.
Wenn du einen One-Click Gameserver auf einem Rootserver benutzt, eröffne bitte ein Support-Ticket um einen weiteren Port freizugeben.
{% endhint %}
