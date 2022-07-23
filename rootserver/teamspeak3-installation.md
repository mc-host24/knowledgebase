# Teamspeak3 Server

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

# Teamspeak3 Installation

* Laden den Teamspeak3 Server herunter.

```bash
wget https://dl.4players.de/ts/releases/3.13.5/teamspeak3-server_linux_amd64-3.13.5.tar.bz2
```

* Entpacke den Teamspeak3 Server

```bash
tar xfvj teamspeak3-server_linux_amd64-3.13.5.tar.bz2
```

* Lösche die .tar.bz2 Datei

```bash
rm teamspeak3-server_linux_amd64-3.13.5.tar.bz2
```

* Navigiere in das Teamspeak3 Verzeichnis

```bash
cd teamspeak3-server_linux_amd64
```

* Akzeptiere die Ts3 Server Lizenz.

```bash
touch .ts3server_license_accepted
```

* Nun gebe deinem Teamspeak3 Ordner "ts3" Nutzer rechte

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

* Navigiere in dein Teamspeak3 Ordner

```bash
cd /home/ts3/teamspeak3-server_linux_amd64
```

* Starte dein teamspeak3 Server mit

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

# Die Installation vom Teamspeak3 Server ist abgeschlossen
