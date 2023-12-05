## TeamSpeak 3 / Discord Musikbot erstellen (SinusBot)

## Falls Sie es noch nicht getan haben, laden Sie das Programm [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) herunter.
Verbinden Sie sich mithilfe von PuTTY via SSH mit Ihrem Root- oder vServer. Hierfür öffnen Sie PuTTY und geben im Textfeld "Host Name (or IP address)" 
die Domain oder IP-Adresse Ihres Servers ein. Klicken Sie anschließend unten auf "OK".

Aktualisieren Sie nun Ihre Paketlisten und Installieren Sie jetzt möglicherweise verfügbare Updates der auf Ihrem Server bereits installieren Pakete mit dem Befehl.

```bash
apt update && apt upgrade -y
```


Installieren Sie anschließend diese Pakete, die benötigt werden, mit folgendem Befehl:

```bash
apt install x11vnc xvfb libxcursor1 ca-certificates bzip2 libnss3 libegl1-mesa x11-xkb-utils libasound2 libpci3 libxslt1.1 libxkbcommon0 libxss1 libglib2.0-0 libxcomposite1 curl screen nano -y
```

Fügen Sie anschließend einen Benutzer, der später den Sinusbot Server ausführen wird, auf Ihrem Server hinzu. Verwenden Sie dazu folgenden Befehl:

{% tabs %}
{% tab title="Außen erreichbar" %}
Wenn du dich von außen direkt mit dem "sinusbot" Nutzer anmelden möchtest

```bash
adduser sinusbot
```

{% endtab %}

{% tab title="Außen nicht erreichbar" %}
Mit diesem Befehl, kannst du dich nur mit Root in den Nutzer "sinusbot" anmelden

```bash
adduser --disabled-login sinusbot
```

{% endtab %}
{% endtabs %}

Die Abfrage weiterer Angaben wie Name, Telefonnummer, etc. können Sie einfach mit der Enter-Taste überspringen. Bestätigen Sie zum Schluss die Korrektheit der Informationen ebenfalls mit der Enter-Taste.

![Bei den Folgenden fragen kannst du die mit der "Enter" Taste durchklicken und am Ende mit "Y/J" bestätigen](https://auroa.link/uploads/auroa/4aa27f75-9c43-4485-a185-ce137e391800.jpg)

Erstellen Sie nun das Verzeichnis, in dem der Musikbot installiert werden soll, mit diesem Befehl:

```bash
mkdir -p /opt/sinusbot 
```

und geben Sie mithilfe des Befehls dem Musikbot-Benutzer die nötigen Rechte in diesem Verzeichnis.

```bash
chown -R sinusbot:sinusbot /opt/sinusbot/
```

Wechseln Sie nun mit dem Befehl in das Benutzerkonto des Musikbot-Benutzers.

```bash
su sinusbot
```

Begeben Sie sich mit dem Befehl in das Verzeichnis, in dem der Musikbot installiert werden soll.

```bash
cd /opt/sinusbot/
```

Laden Sie den Musikbot "SinusBot" nun herunter, indem Sie den folgenden Befehl ausführen. Starten Sie nun den Download mit der Enter-Taste.

```bash
wget https://www.sinusbot.com/dl/sinusbot.current.tar.bz2
```

Nachdem der Download abgeschlossen ist, sollten Sie mit dem Befehl:
```bash
ls -lh
```

das heruntergeladene **.tar.bz2-Archiv** sehen. Entpacken Sie dieses mit dem Befehl.
```bash
tar xjf sinusbot.current.tar.bz2
```

Anschließend können Sie es mithilfe des Befehls die Vorher runtergeladenen "**.tar.bz2**" wieder löschen.

```bash
rm sinusbot.current.tar.bz2 
```


Kopieren Sie nun die benötigte Konfigurationsdatei mithilfe des folgenden Befehls: 

```bash
cp config.ini.dist config.ini
```

Nun benötigen Sie den TeamSpeak 3 Client für Linux, damit sich der Musikbot später mit Ihrem TeamSpeak 3 Server verbinden kann. Auch wenn Sie den Musikbot nur in Verbindung mit einem Discord Server nutzen möchten, benötigen Sie den TeamSpeak 3 Client, 
da der Musikbot sonst nicht startet. Laden Sie diesen Client mit folgendem Befehl herunter:

```bash
wget https://files.teamspeak-services.com/releases/client/3.5.3/TeamSpeak3-Client-linux_amd64-3.5.3.run
```

Vergeben Sie mithilfe des Befehls nun noch die Rechte zum Ausführen dieser Datei.

```bash
chmod +x TeamSpeak3-Client-linux_amd64-3.5.3.run
```
Nun müssen Sie den TeamSpeak 3 Client auf Ihrem Server einmal starten, um die Lizenzbedingungen zu akzeptieren. Das machen Sie mit dem Befehl.

```bash
./TeamSpeak3-Client-linux_amd64-3.5.3.run
```
Mit der Enter-Taste scrollen Sie durch den Text und mit der "**q**"-Taste gelangen Sie zum Ende. Bestätigen Sie mit der "**Y**"-Taste, dass Sie die Lizenzbedingungen gelesen und akzeptiert haben und drücken Sie danach die Enter-Taste.

Löschen Sie nun die Datei "libqxcb-glx-integration.so", indem Sie den Befehl ausführen.

```bash
rm TeamSpeak3-Client-linux_amd64/xcbglintegrations/libqxcb-glx-integration.so
```

Erstellen Sie jetzt das Plugin-Verzeichnis des TeamSpeak 3 Clients mit dem Befehl

```bash
mkdir TeamSpeak3-Client-linux_amd64/plugins
```

und  kopieren Sie daraufhin das Musikbot-Plugin in dieses Plugin-Verzeichnis. Verwenden Sie hierzu diesen Befehl:

```bash
cp plugin/libsoundbot_plugin.so /opt/sinusbot/TeamSpeak3-Client-linux_amd64/plugins/
```

Jetzt müssen Sie noch die benötigten Rechte zum Ausführen des Musikbot-Scripts vergeben. Das machen Sie mit dem Befehl.
```bash
chmod +x sinusbot
```

Der Musikbot ist nun installiert und Sie können ihn starten. Stellen Sie hierfür sicher, dass Sie mit dem Musikbot-Benutzer angemeldet sind, den Sie zuvor erstellt haben und dass Sie sich im Verzeichnis befinden. 
Ist das nicht der Fall, so können Sie mit dem Befehl
```bash
su sinusbot 
```
zu diesem Benutzer und anschließend mithilfe des Befehls in das Musikbot-Verzeichnis wechseln. 
```bash
cd /opt/sinusbot/ 
```

Führen Sie für den ersten Start des Musikbots folgenden Befehl aus
```bash
screen -dmS sinusbot ./sinusbot -override-password IhrPasswort
```
Anstelle von "**IhrPasswort**" vergeben Sie hier ein beliebiges Passwort für das Webinterface.
Um ein sicheres password zu benutzen, benutzt bitte folgende Seite: [Password Generator](https://bitwarden.com/password-generator/)

Ihr Musikbot ist nun gestartet. Sie können das Webinterface über die IP-Adresse oder Domain Ihres Root- oder vServers mit dem Port 8087 erreichen. 
Rufen Sie hierfür im Browser also beispielsweise "**http://123.123.123.123:8087**" auf. Der Benutzername lautet "**admin**" und das Passwort ist das, welches Sie gerade festgelegt haben.

Sie können die Sprache des Webinterfaces nun auf Deutsch umstellen, indem Sie im Menü oben auf "**Settings**" klicken und unter "**Language**" anschließend "**Deutsch**" auswählen.

Da das Passwort des Musikbots jedoch nur beim ersten Start temporär gesetzt ist, müssen Sie dieses nun noch in den Einstellungen im Webinterface fest ändern. 
Klicken Sie hierzu in den Webinterface-Einstellungen links auf "Benutzerkonten". Es erscheint nun eine Benutzerübersicht als Tabelle. 
Klicken Sie in der Zeile des Admin-Benutzers rechts auf den Bearbeiten-Button, vergeben Sie Ihr gewünschtes Passwort und speichern Sie diese Änderung abschließend mit einem Klick auf den Button "Änderungen speichern". 
Danach müssen Sie sich mit dem soeben gesetzten Passwort erneut anmelden.

## Falls Sie den Musikbot auf einem Discord Server nutzen möchten, führen Sie folgende Schritte durch:
1. Klicken Sie im Einstellungsmenü des Webinterfaces links auf "**Instanzen**" und fügen über den Button "**Instanz erstellen**" eine weitere Musikbot-Instanz hinzu.
2. Wählen Sie als "**Backend**" nun "**Discord**" aus und vergeben Sie einen Namen für den Musikbot.
3. Klicken Sie unter dem letzten Textfeld auf das rot markierte Wort "**here**", um die Übersicht Ihrer Discord-Apps aufzurufen. Hier müssen Sie den Musikbot über einen Klick auf "**New Application**" als Discord-App registrieren.
4. Vergeben Sie einen Namen für Ihren Musikbot, welcher später auf dem Discord Server angezeigt wird (z.B. "**SinusBot**").
5. Aktivieren Sie die Checkbox "**By clicking Create, you agree to the Discord Developer Terms of Service and Developer Policy**" und klicken Sie auf den Button "**Create**", um die Discord-App zu erstellen.
6. Klicken Sie nun links auf den Menüpunkt "**Bot**", dann auf den Button "**Add Bot**" und anschließend auf "**Yes, do it!**".
7. Klicken Sie unter der Überschrift "Token" auf den Button "**Copy**", um den Token (Zugangsschlüssel) für den Musikbot zu kopieren. Fügen Sie diesen Token nun im Musikbot-Webinterface in das Textfeld "**Bot-Token**" ein. Klicken Sie daraufhin auf "**Erstellen**".
8. Wählen Sie in der Instanz-Übersicht nun die soeben erstellte Discord-Instanz aus, indem Sie auf den entsprechenden "**Auswählen**"-Button klicken.
9. Wechseln Sie danach in den Einstellungen des Webinterfaces links auf die "**Instanz-Einstellungen**".
10. Klicken Sie auf den roten Link "**Klicke hier um dem Bot die Erlaubnis zu erteilen, deinen Server zu betreten**", wählen Sie dann Ihren Discord-Server aus und klicken Sie anschließend auf den Button "**Autorisieren**", um den Musikbot nun mit Ihrem Discord Server zu verbinden.
11. Starten Sie die Musikbot-Instanz, indem Sie im Webinterface oben auf den Einschalten-Button klicken. Nun sollte der Musikbot Ihrem Discord Server beigetreten sein.
12. Laden Sie die Webinterface-Einstellungsseite im Browser noch einmal neu, wählen den gewünschten Discord-Channel unter "**Standard-Channel**" aus und klicken anschließend unten auf "**Änderungen speichern**". Der Musikbot sollte jetzt dem Discord-Channel beitreten und ist einsatzbereit.

Um den Musikbot - neben dem Webinterface - auch über Chat-Befehle steuern zu können, müssen Sie die Benutzer Ihres TeamSpeak 3 Servers bzw. 
Discord Servers mit entsprechenden Webinterface-Benutzern verknüpfen. Klicken Sie hierzu in den Webinterface-Einstellungen links auf "**Benutzerkonten**".

Derzeit gibt es nur den Benutzer "**admin**", über den Button "**Benutzer hinzufügen**" können Sie jedoch noch weitere hinzufügen.

Sie können einen Benutzer mit einem TeamSpeak- bzw. Discord-Benutzer verknüpfen, indem Sie rechts auf den Bearbeiten-Button klicken, unter "**An neue Identität binden**" den entsprechenden Benutzer auf Ihrem Server auswählen und anschließend auf "**Änderungen speichern**" klicken. 
In der Tabelle können Sie unter "**Rechte**" für jeden Benutzer individuell festlegen, welche Aktionen dieser ausführen darf.

Die verfügbaren Chat-Befehle finden Sie, wenn Sie in den Webinterface-Einstellungen links auf "**Info**" und dann auf den Reiter "**Befehle**" klicken.

Ihr Musikbot läuft ab sofort ununterbrochen im Hintergrund, somit können Sie ***PuTTY*** nun ohne Probleme schließen. Um den Musikbot zu stoppen, verwenden Sie den Befehl. 
```bash
screen -r sinusbot -X quit
```
Wenn Sie den Musikbot starten möchten, stellen Sie sicher, dass Sie als Musikbot-Benutzer angemeldet sind entweder direkt beim SSH-Login in PuTTY oder über den Befehl 
```bash
su sinusbot
```
wechseln Sie mit dem Befehl 
```bash
cd /opt/sinusbot/ 
```
in das Musikbot-Verzeichnis und starten Sie den Musikbot letztendlich mit dem Befehl.
```bash
screen -dmS sinusbot ./sinusbot
```
