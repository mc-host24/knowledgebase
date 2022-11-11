## Teamspeak³-Server installieren

* Aktualisiere die Paketlisten & installiere die Updates.

```bash
apt update && apt upgrade -y
```

* Erstelle einen Nutzer, damit man Teamspeak ausführen kann.

{% tabs %}
{% tab title="Außen erreichbar" %}
* Wenn du dich von außen direkt mit dem "ts3" Nutzer anmelden möchtest

```bash
adduser ts3
```

{% endtab %}

{% tab title="Außen nicht erreichbar" %}
* Mit diesem Befehl, kannst du dich nur mit Root in den Nutzer "ts3" anmelden

```bash
adduser --disabled-login ts3
```

{% endtab %}
{% endtabs %}

![Bei den Folgenden fragen kannst du die mit der "Enter" Taste durchklicken und am Ende mit "Y/J" bestätigen](https://bilderupload.org/image/7d9157172-adduser-ts3.png)


* Nun navigiere zum ts3 Verzeichnis

```bash
cd /home/ts3
```

### Teamspeak³ Installation

* Laden den Teamspeak³ Server herunter.

```bash
wget https://files.teamspeak-services.com/releases/server/3.13.7/teamspeak3-server_linux_amd64-3.13.7.tar.bz2
```

* Entpacke den Teamspeak³ Server

```bash
tar xfvj teamspeak3-server_linux_amd64-3.13.7.tar.bz2
```

* Lösche die .tar.bz2 Datei

```bash
rm teamspeak3-server_linux_amd64-3.13.7.tar.bz2
```

* Navigiere in das Teamspeak³ Verzeichnis

```bash
cd teamspeak3-server_linux_amd64
```

* Akzeptiere die Ts3 Server Lizenz.

```bash
touch .ts3server_license_accepted
```

* Nun gebe deinem Teamspeak³ Ordner "ts3" Nutzer rechte

```bash
chown ts3:ts3 /home/ts3/teamspeak3-server_linux_amd64
```

* Gebe der Startdatei die benötigten Rechte, um zu starten.

```bash
chmod +x ts3server_startscript.sh
```

* Melde dich nun mit dem "ts3" Nutzer an

```bash
su ts3
```

* Navigiere in dein Teamspeak³ Ordner

```bash
cd /home/ts3/teamspeak3-server_linux_amd64
```

* Starte dein Teamspeak³ Server mit

```bash
./ts3server_startscript.sh start
```

![hier siehst du dein teamspeak3 token. gebe diese in teamspeak ein. Vergesse nicht dein Token zu Kopieren oder abzuspeichern](https://bilderupload.org/image/3eb657093-ts3-daten.png)

* Verbinde dich auf deinen Teamspeak Server und verwende den Berechtigungsschlüssel.


* nun kannst du wieder in dein Terminal gehen und drücke die Tastenkombination 
* STRG + C und starte den Server nochmal, damit der Server im Hintergrund weiterläuft

```bash
./ts3server_startscript.sh start
```
Die Installation vom Teamspeak³ Server ist damit abgeschlossen.

## Teamspeak³ Server updaten

Falls noch nicht passiert, musst du deinen Teamspeak³-Server vor dem Update zuerst herunterfahren (`./ts3server_startscript.sh stop`).

Um deinen Teamspeak³-Server zu updaten, musst du dir die neuste Server-Version von der [offiziellen Webseite](https://teamspeak.com/de/downloads/#server) herunterladen. Bei unseren Rootservern benötigst du die 64-Bit Variante von Linux.

Als nächstes entpackst du das heruntergeladene Archiv z.B. mit 7-Zip oder Winrar.

Nun verbindest du dich mittels [SFTP auf deinen Rootserver](sftp-verbinden.md), navigierst in das Verzeichnis deines Teamspeak³-Servers und lädst zur Sicherheit die `ts3server.sqlitedb` herunter, falls beim Update etwas schieflaufen sollte.

Nachdem du das gemacht hast, überschreibst du alle Dateien deines Teamspeak³-Servers mit den Dateien, welche du zuvor entpackt hast.

Wenn alles geklappt hat, kannst du nun mit `./ts3server_startscript.sh start` deinen Teamspeak³-Server wieder starten.
