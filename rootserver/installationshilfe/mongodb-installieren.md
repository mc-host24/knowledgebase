# Installation von MongoDB auf einem Linux-Server

MongoDB ist eine kostenlose, Open-Source-Dokumenten-orientierte Datenbank, die Daten in JSON-ähnlichen Dokumenten mit einem flexiblen Schema speichert. Diese "NoSQL"-Datenbank ist eine beliebte Alternative zu traditionellen relationalen Datenbanken wie MySQL. Erfahren Sie, wie Sie MongoDB auf einem Cloud Server mit CentOS 7, Ubuntu 14.04 oder Ubuntu 16.04 installieren.

Es gibt zwei Möglichkeiten, MongoDB zu installieren:

Auf einem neuen Server:
MongoDB ist als fertige Anwendung verfügbar, die beim Aufbau automatisch auf dem Server installiert werden kann.
 
Auf einem bestehenden Server: 
MongoDB kann manuell installiert und auf einem bestehenden Server konfiguriert werden.

## CentOS

Um das Repository hinzuzufügen, muss eine anfangs leere mongodb-org-3.6.repo-Datei erstellt werden und zur Bearbeitung mit dem folgenden Befehl geöffnet werden

<pre>
sudo nano /etc/yum.repos.d/mongodb-org-3.6.repo
</pre>

Jetzt muss dort der folgende Inhalt eingefügt werden:

<pre>
[mongodb-org-3.6]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/3.6/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-3.6.asc
</pre>

Nun das System mit <code>sudo yum update</code> aktualisieren und MongoDB mit dem folgenden Befehl installieren:
<pre>
sudo yum install -y mongodb-org
</pre>

## Ubuntu
### Version 14.04

MongoDB neustarten und den öffentlichen MongoDB GPG-Schlüssel importieren:

<pre>
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5
</pre>

Erstelle eine anfangs leere mongodb-org-3.6.list Datei:

<pre>
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list
</pre>

Nun muss noch die Paketdatenbank aktualisiert werden:

<pre>
sudo apt-get update
</pre>

MongoDB lässt sich ganz einfach mit diesem Befehl installieren:

<pre>
sudo apt-get install -y mongodb-org
</pre>

### Version 16.04

Bei Ubuntu 16.04 ist genau das gleiche, der zweite Befehl ist jedoch ein wenig anders:

<pre>
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list
</pre>
