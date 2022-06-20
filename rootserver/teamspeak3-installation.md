# Teamspeak3 Server

* Aktualisiere die Paketlisten & installiere die Updates.

```bash
apt update && apt upgrade -y
```

* Nutzer erstellen, damit man später Teamspeak ausführen kann.

{% tabs %}
{% tab title="Außen ereichbar" %}
* Wenn du dich von außen direkt mit dem "ts3" Nutzer anmelden möchtest

```bash
adduser ts3
```

{% endtab %}

{% tab title="Außen nicht ereichbar" %}
* Mit diesem Befehl, kannst du dich nur mit Root in den Nutzer "ts3" anmelden

```bash
adduser --disabled-login ts3
```

{% endtab %}
{% endtabs %}

* Bei den folgenden fragen, kannst du die mit der "Enter" Taste durchklicken und am ende mit "Y/J" Bestätigen

![](https://bilderupload.org/image/7d9157172-adduser-ts3.png)

* Nun navigiere zum ts3 verzeichnis

```bash
cd /home/ts3
```

#Teamspeak3 installation

* Installiere Teamspeak3 Server

```bash
wget https://dl.4players.de/ts/releases/3.13.5/teamspeak3-server_linux_amd64-3.13.5.tar.bz2
```

* Entpacke Teamspeak3 Server

```bash
tar xfvj teamspeak3-server_linux_amd64-3.13.5.tar.bz2
```

* Lösche die .tar.bz2 datei

```bash
rm teamspeak3-server_linux_amd64-3.13.5.tar.bz2
```

* Navigiere in dein Teamspeak3 Verzeichnis

```bash
cd teamspeak3-server_linux_amd64
```

* Akzeptiere die Ts3 server Lizenz mit

```bash
touch .ts3server_license_accepted
```

* Nun gebe deinem Teamspeak3 Ordner "ts3" rechte

```bash
chown ts3:ts3 /home/ts3/teamspeak3-server_linux_amd64
```

* Gebe teamspeak3 server start rechte

```bash
chmod +x ts3server_startscript.sh
```

* melde dich nun mit dem "ts3" Nutzer an

```bash
su ts3
```

* navigiere in dein Teamspeak3 ordner

```bash
cd /home/ts3/teamspeak3-server_linux_amd64
```

* starte dein teamspeak3 server mit

```bash
./ts3server_startscript.sh start
```

* hier siehst du dein teamspeak3 token. gebe diese in deinem teamspeak ein
* (Kopiere es dir oder speichere es irgendwo sicher ab)

![](https://bilderupload.org/image/3eb657093-ts3-daten.png)

* Starte Teamspeak3 -> gehe oben Links auf Verbindungen danach auf -> Verbinden
* Gebe deine Server-IP oder Domain unter: Server Nickname oder Adresse ein
* und gebe unter Nickname: dein Nutzernamen/Spielnamen/Echten namen ein
* und Drücke auf Verbinden

![](https://bilderupload.org/image/ff8257054-ts3-verbinden.png)

* Nachdem du auf deinem Teamspeak3 Server bist siehst du diese meldung.
* Gebe hier deinen Token ein, den du eben im Terminal bekommen hast

![](https://bilderupload.org/image/2eac56992-token-eingeben.png)

* nun kannst du wieder in dein Terminal gehen und gibst die Tastenkombination 
* STRG + C ein und startest diesen server nochmal, damit es im Hintergrund weiterläuft

```bash
./ts3server_startscript.sh start
```

# Die Installation vom Teamspeak3 Server ist abgeschlossen
