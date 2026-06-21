# PhpMyAdmin, PHP 8.4, Apache2 und MySQL Installation | Debian 13
## SSH-Client:
Falls Sie es noch nicht getan haben, installieren Sie sich einen beliebigen SSH-Client. Laden Sie sich zum Beispiel das Programm [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) oder [Termius](https://termius.com/download/) herunter. Verbinden Sie sich mithilfe von SSH mit Ihrem Root- oder V-Server. Standardmäßig ist der Benutzername "root" (wichtig, klein!), der Port 22 und der Hostname Ihre IP. Verbinden Sie sich anschließend und akzeptieren Sie den Fingerprint.

## Installation:
* Aktualisieren Sie als erstes Ihre Paketlisten und installieren Sie jetzt möglicherweise verfügbare Updates der auf Ihrem Server bereits installierten Pakete mit dem Befehl.

```bash
apt update && apt upgrade -y
```

* Als nächstes installieren Sie Pakete, die für die weiteren Installationen benötigt werden, mit folgendem Befehl: 

```bash
apt install ca-certificates apt-transport-https lsb-release gnupg curl nano unzip -y
```

* Fügen Sie die für die Installation von PHP 8.4 benötigte Paketquelle hinzu:

```bash
curl -fsSL https://packages.sury.org/php/apt.gpg -o /usr/share/keyrings/php-archive-keyring.gpg
```
```bash
echo "deb [signed-by=/usr/share/keyrings/php-archive-keyring.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
```

* Aktualisieren Sie nun erneut Ihre Paketlisten mit dem Befehl:
```bash
apt update
```

* Installieren Sie den Apache2-Webserver sowie weitere benötigte Pakete mit folgendem Befehl: 
```bash
apt install apache2 -y
```

* Installieren Sie anschließend PHP 8.4 sowie einige wichtige PHP-Module. Der Befehl hierfür lautet: 
```bash
apt install php8.4 php8.4-cli php8.4-common php8.4-curl php8.4-gd php8.4-intl php8.4-mbstring php8.4-mysql php8.4-opcache php8.4-readline php8.4-xml php8.4-xsl php8.4-zip php8.4-bz2 libapache2-mod-php8.4 -y
```

* Installiere MySQL
```bash
apt install mariadb-server mariadb-client -y
```

Schließe die MySQL Installation ab

Geben Sie nun den Befehl ein:
```bash
mariadb-secure-installation
```
Bei der ersten Abfrage des aktuellen Passworts müssen Sie nichts eingeben, sondern einfach die Enter-Taste drücken. Geben Sie bei der anschließenden Frage bezüglich des Wechsels zur Unix-Socket-Authentifizierung **'n'** ein und drücken Sie die Enter-Taste. Bestätigen Sie die nächste Frage bezüglich der Änderung des Root-Passworts mit Enter. Nun müssen Sie ein Passwort für den Root-Benutzer des MariaDB-Servers vergeben. Während der Eingabe erscheinen keine Zeichen, das ist jedoch normal. Bestätigen Sie alle darauffolgenden Fragen (Löschung des anonymen Benutzers, Verbieten des externen Root-Logins aus Sicherheitsgründen, Entfernen der Testdatenbank und Aktualisieren der Rechte) ebenfalls mit Enter. Danach ist der MariaDB-Server fertig installiert und konfiguriert.


* Wechseln Sie mit dem Befehl in das Verzeichnis, in dem phpMyAdmin installiert wird:
```bash
cd /usr/share
```

* Um phpMyAdmin herunterzuladen, führen Sie nun den Befehl aus:
```bash
wget https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-all-languages.zip -O phpmyadmin.zip
```

* Entpacken Sie das soeben heruntergeladene Archiv mit dem folgenden Befehl: 
```bash
unzip phpmyadmin.zip
```

* Entfernen Sie das heruntergeladene Archiv, mit dem Befehl:
```bash
rm phpmyadmin.zip
```

* Anschließend müssen Sie den Namen des entpackten Verzeichnisses zu **"phpmyadmin"** umbenennen. Dies machen Sie mit folgendem Befehl: 
```bash
mv phpMyAdmin-*-all-languages phpmyadmin
```

* Vergeben Sie anschließend die benötigten Rechte auf das phpMyAdmin-Verzeichnis mithilfe des Befehls:
```bash
chmod -R 0755 phpmyadmin
```

* Erstellen Sie nun eine Apache2-Konfigurationsdatei für phpMyAdmin, indem Sie den Befehl ausführen:
```bash
nano /etc/apache2/conf-available/phpmyadmin.conf
```

* Fügen Sie in diese Konfigurationsdatei nun folgenden Inhalt ein:
```bash
# phpMyAdmin Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
    Options SymLinksIfOwnerMatch
    DirectoryIndex index.php
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/templates>
    Require all denied
</Directory>
<Directory /usr/share/phpmyadmin/libraries>
    Require all denied
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Require all denied
</Directory>
```
* Speichern Sie Ihre Änderungen der Konfiguration, indem Sie **STRG + X, danach die "Y"-Taste und anschließend Enter** drücken.

* Aktivieren Sie die soeben hinzugefügte Apache2-Konfigurationsdatei mit dem Befehl:
```bash 
a2enconf phpmyadmin 
``` 

Daraufhin schlägt das System bereits einen Reload des Apache2-Webservers vor. Führen Sie den Befehl durch:
```bash 
systemctl reload apache2
``` 


* Erstellen Sie das temporäre Verzeichnis, welches phpMyAdmin benötigt, indem Sie den Befehl ausführen:
```bash 
mkdir /usr/share/phpmyadmin/tmp/
```

* Geben Sie dem Webserver-Benutzer nun die benötigten Besitzerrechte für dieses temporäre Verzeichnis mithilfe des Befehls:
```bash
chown -R www-data:www-data /usr/share/phpmyadmin/tmp/
```

Ihr Apache2-Webserver inklusive PHP 8.4, MariaDB-Server und phpMyAdmin ist nun einsatzbereit. Das Web-Verzeichnis befindet sich standardmäßig unter **"/var/www/html/"**. Die phpMyAdmin-Weboberfläche erreichen Sie, indem Sie hinter der IP-Adresse oder Domain Ihres Servers im Browser **"/phpmyadmin"** anhängen. 
Dort können Sie sich jetzt am MariaDB-Server anmelden.

## Datenbank von außen erreichbar machen
### Wichtiger Sicherheits-Disclaimer
**Die Datenbank sollte NICHT ohne zusätzliche Sicherheitsmaßnahmen von außen erreichbar sein!** Das öffentliche Exponieren einer Datenbank ist ein erhebliches Sicherheitsrisiko. Hier sind die Hauptgefahren:

- **Unautorierte Zugriffe**: Angreifer können versuchen, sich mit Standardpasswörtern oder durch Brute-Force-Attacken Zugang zu verschaffen
- **Datendiebstahl**: Sensible Informationen (Benutzerdaten, Passwörter, etc.) können gestohlen werden
- **SQL-Injection**: Anfälligkeit gegenüber SQL-Injektionen erhöht sich massiv bei direkter Exposition
- **Denial-of-Service (DoS)**: Angreifer könnten die Datenbank mit Anfragen überlasten und zum Absturz bringen
- **Ransomware & Malware**: Gehackte Datenbanken werden häufig zum Ziel von Ransomware-Angriffen

**Empfehlung**: Exponiere die Datenbank nur wenn absolut notwendig und verwende IMMER:
- Eine Firewall (z.B. UFW, hierzu gleich mehr) um den Zugriff zu beschränken
- Starke, eindeutige Passwörter
- SSH-Tunneling statt direkter Datenbank-Exposition
- Regelmäßige Backups und Security-Updates

### Datenbank von außen erreichbar machen
Standardmäßig erlaubt eine MySQL-Datenbank nur Zugriffe durch den eigenen Server (`localhost`). Um ebenso Zugriffe von außerhalb zu erlauben, müssen Sie in der Konfigurationsdatei Ihrer Datenbank den Punkt `bind-adress` von `127.0.0.1` auf `0.0.0.0` ändern.

* Nutze dafür folgenden Befehl:
```bash
nano /etc/mysql/mariadb.conf.d/50-server.cnf
```
```bash
bind-address = 0.0.0.0
```

Speichern Sie Ihre Änderungen der Konfiguration, indem Sie **STRG + X, danach die "Y"-Taste und anschließend Enter** drücken.
Danach müssen Sie lediglich Ihre Datenbank neustarten, sodass die Änderungen wirksam werden.

* Benutze dafür folgenden Befehl:
```bash
service mysql restart
```

### Datenbank mit UFW absichern
Um Ihre Datenbank von außen abzusichern, können Sie das über die Firewall **UFW** machen. **UFW** (Uncomplicated Firewall) ist eine benutzerfreundliche Firewall für Linux, die es Ihnen erlaubt, Regeln für ein- und ausgehende Netzwerkverbindungen einfach zu verwalten. Sie bietet Schutz vor unbefugten Zugriffen, indem sie nur explizit erlaubte Ports und Verbindungen durchlässt. Das sollten Sie auch machen, auch wenn die Datenbanken nicht von außen erreichbar sind!

Dafür installieren Sie erstmals **UFW** auf Ihrem Server mit folgendem Befehl:
```bash
apt install ufw -y
```
* Danach geben wir die Standart Port nach außen offen ( SSH, HTTP, HTTPS ):
```bash
ufw allow 22
ufw allow 443
ufw allow 80
```
* Danach aktivieren wir die UFW (einfach mit **Y** bestätigen):
```bash
ufw enable
```

* Nun aktivieren wir UFW für die Datenbank. Ersetzen Sie dabei IHRE-IP mit Ihrer IP (Ihres Heim-PCs).
```bash
ufw allow from DEINE-IP to any port 3306
```
Nachdem Sie das eingefügt haben, kann nur die IP auf dem Server zugreifen, die in der Liste stehen.