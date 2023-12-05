## Teamspeak 3 Server installieren

## Falls Sie es noch nicht getan haben, laden Sie das Programm [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) herunter.
Verbinden Sie sich mithilfe von PuTTY via SSH mit Ihrem Root- oder vServer. Hierfür öffnen Sie PuTTY und geben im Textfeld "Host Name (or IP address)" 
die Domain oder IP-Adresse Ihres Servers ein. Klicken Sie anschließend unten auf "OK".

* Aktualisieren Sie nun Ihre Paketlisten und Installieren Sie jetzt möglicherweise verfügbare Updates der auf Ihrem Server bereits installieren Pakete mit dem Befehl.

```bash
apt update && apt upgrade -y
```

Fügen Sie anschließend einen Benutzer, der später den TeamSpeak 3 Server ausführen wird, auf Ihrem Server hinzu. Verwenden Sie dazu folgenden Befehl:

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
In diesem Beispiel heißt der Benutzer "ts3". Sie können auch einen anderen Namen verwenden, müssen dann aber darauf achten, anstelle von "ts3" in dieser Anleitung immer Ihren selbst gewählten Benutzernamen zu verwenden (z.B. "teamspeak").

Die Abfrage weiterer Angaben wie Name, Telefonnummer, etc. können Sie einfach mit der Enter-Taste überspringen. Bestätigen Sie zum Schluss die Korrektheit der Informationen ebenfalls mit der Enter-Taste.

![Bei den Folgenden fragen kannst du die mit der "Enter" Taste durchklicken und am Ende mit "Y/J" bestätigen](https://auroa.link/uploads/auroa/4aa27f75-9c43-4485-a185-ce137e391800.jpg)


* Wechseln Sie nun mit dem Befehl in das Benutzerkonto des TeamSpeak 3 Benutzers.

```bash
su ts3
```

* Begeben Sie sich mit dem Befehl in das Home-Verzeichnis dieses Benutzers. Das Home-Verzeichnis heißt genauso wie der Benutzer selbst und befindet sich dementsprechend unter dem Pfad "/home/ts3".

```bash
cd 
```

* Besuchen Sie nun die [TeamSpeak-Downloadseite](https://www.teamspeak.com/en/downloads/#server) und kopieren Sie den Download-Link des TeamSpeak 3 Servers. Klicken Sie dazu auf das Kopieren-Symbol rechts neben der 
jeweiligen Server-Version (32- oder 64-Bit) unter der Überschrift "Linux". Haben Sie ein 64-Bit System, was meistens der Fall sein sollte, so verwenden Sie natürlich die 64-Bit Version.


* Öffnen Sie nun wieder PuTTY, gebe den Befehl "**wget**", gefolgt von einem Leerzeichen ein und führen Sie anschließend einen Rechtsklick im PuTTY-Fenster aus. Somit fügen Sie den Download-Link 
ein. Starten Sie nun den Download mit der Enter-Taste.

```bash
wget https://files.teamspeak-services.com/releases/server/3.13.7/teamspeak3-server_linux_amd64-3.13.7.tar.bz2
```

* Nachdem der Download abgeschlossen ist, sollten Sie mit dem Befehl ls das heruntergeladene .tar.bz2-Archiv sehen. Entpacken Sie dieses mit dem Befehl "**tar xfvj**", 
gefolgt von einem Leerzeichen und dem Archivnamen.

```bash
tar xfvj teamspeak3-server_linux_amd64-3.13.7.tar.bz2
```

* Nachdem das Archiv entpackt wurde, löschen Sie dieses mithilfe des Befehls "**rm**", gefolgt von einem Leerzeichen und dem Dateinamen.

```bash
rm teamspeak3-server_linux_amd64-3.13.7.tar.bz2
```

* Wechseln Sie nun in das soeben entpackte TeamSpeak 3 Verzeichnis. Verwenden Sie dazu den Befehl "**cd**", gefolgt von einem Leerzeichen und dem Verzeichnisnamen.

```bash
cd teamspeak3-server_linux_amd64
```

* Damit Sie den TeamSpeak 3 Server starten können, müssen Sie die TeamSpeak-Lizenzbedingungen akzeptieren. Hierzu erstellen Sie mithilfe des Befehls eine Datei, um zu kennzeichnen, dass Sie diese Lizenzbedingungen akzeptieren.

```bash
touch .ts3server_license_accepted
```

* Führen Sie nun das Startscript aus, um den TeamSpeak 3 Server zu starten. Verwenden Sie dazu den folgenden Befehl: 

```bash
./ts3server_startscript.sh start
```

Ihnen wird nun ein Serveradmin-Passwort sowie ein Admin-Token angezeigt. Merken oder notieren Sie sich das Serveradmin-Passwort und kopieren Sie den Admin-Token.
Mit dem Admin-Token können Sie im TeamSpeak 3 Client auf Ihrem Server die Administrationsrechte erhalten. Verbinden Sie sich dazu mit Ihrem TeamSpeak 3 Server und klicken Sie oben 
im Menü auf "**Rechte**" -> "**Berechtigungsschlüssel benutzen**". Das Serveradmin-Passwort ist wichtig, wenn Sie beispielsweise noch ein TeamSpeak 3 Webinterface installieren möchten, oder das Programm "**YaTQA**" benutzen möchten.

* Ihr TeamSpeak 3 Server ist nun einsatzbereit. Sie können ihn jederzeit starten und stoppen, indem Sie, wenn Sie als TeamSpeak 3 Benutzer angemeldet sind,
mit dem Befehl

```bash
cd /home/ts3/teamspeak3-server_linux_amd64
```
in das TeamSpeak 3 Verzeichnis wechseln und dort das Script entsprechend ausführen. Sollten Sie noch als Benutzer "**root**" angemeldet sein, müssen Sie als erstes mithilfe des Befehls "**su ts3**" zum TeamSpeak 3 Benutzer wechseln.

{% tabs %}
{% tab title="Starten" %}
* Wenn du dich von außen direkt mit dem "ts3" Nutzer anmelden möchtest

```bash
./ts3server_startscript.sh start
```

{% endtab %}

{% tab title="Stoppen" %}
* Mit diesem Befehl, kannst du dich nur mit Root in den Nutzer "ts3" anmelden

```bash
./ts3server_startscript.sh stop
```

{% endtab %}
{% endtabs %}
