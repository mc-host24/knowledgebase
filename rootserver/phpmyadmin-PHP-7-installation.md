## PhpMyAdmin, PHP 7,  Apache2 und MySQL Installation

## Falls Sie es noch nicht getan haben, laden Sie das Programm [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) herunter.
Verbinden Sie sich mithilfe von PuTTY via SSH mit Ihrem Root- oder vServer. Hierfür öffnen Sie PuTTY und geben im Textfeld "Host Name (or IP address)" 
die Domain oder IP-Adresse Ihres Servers ein. Klicken Sie anschließend unten auf "OK".

* Aktualisieren Sie nun Ihre Paketlisten und Installieren Sie jetzt möglicherweise verfügbare Updates der auf Ihrem Server bereits installieren Pakete mit dem Befehl.

```bash
apt update && apt upgrade -y
```

* Als nächstes installieren Sie Pakete, die für die weiteren Installationen benötigt werden, mit folgendem Befehl: 

```bash
apt install ca-certificates apt-transport-https lsb-release gnupg curl nano unzip -y
```

Wähle dein Betriebssystem aus.
Solltest du nicht wissen, welches Betriebssystem du verwendest, kannst du dies mit dem Befehl nachschauen.
```bash
cat /etc/issue
```


{% tabs %}
{% tab title="Debian" %}
* Fügen Sie die für die Installation von PHP 7 benötigte Paketquelle hinzu:

```bash
curl -fsSL https://packages.sury.org/php/apt.gpg -o /usr/share/keyrings/php-archive-keyring.gpg
```

```bash
echo "deb [signed-by=/usr/share/keyrings/php-archive-keyring.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
```
{% endtab %}

{% tab title="Ubuntu" %}
* Füge die Paket-Quelle für die PHP 7.4 Version hinzu.

```bash
apt install software-properties-common -y
```

```bash
add-apt-repository ppa:ondrej/php
```
{% endtab %}
{% endtabs %}

* Aktualisieren Sie nun erneut Ihre Paketlisten mit dem Befehl 
```bash
apt update
```

* Installieren Sie den Apache2-Webserver sowie weitere benötigte Pakete mit folgendem Befehl: 
```bash
apt install apache2 -y
```

* Installieren Sie anschließend PHP 7 sowie einige wichtige PHP-Module. Der Befehl hierfür lautet: 
```bash
apt install php7.4 php7.4-cli php7.4-common php7.4-curl php7.4-gd php7.4-intl php7.4-json php7.4-mbstring php7.4-mysql php7.4-opcache php7.4-readline php7.4-xml php7.4-xsl php7.4-zip php7.4-bz2 libapache2-mod-php7.4 -y
```

* Installiere MySQL
```bash
apt install mariadb-server mariadb-client -y
```

Schließe die MySQL Installation ab
{% tabs %}
{% tab title="Debian 10 & Ubuntu" %}
Geben Sie nun den Befehl 
```bash
mysql_secure_installation
``` 
ein. Bei der ersten Abfrage des aktuellen Passworts müssen Sie nichts eingeben, sondern einfach die Enter-Taste drücken. Bestätigen Sie die nächste Frage bzgl. der Änderung des Root-Passworts mit Enter. Nun müssen Sie ein Passwort für den Root-Benutzer des 
MariaDB-Servers vergeben. Während der Eingabe erscheinen keine Zeichen, das ist jedoch normal. Bestätigen Sie alle darauffolgenden Fragen (Löschung des anonymen Benutzers, Verbieten des externen Root-Logins aus Sicherheitsgründen, 
Entfernen der Testdatenbank und Aktualisieren der Rechte) ebenfalls mit Enter. Danach ist der MariaDB-Server fertig installiert und konfiguriert.

{% endtab %}

{% tab title="Debian 11" %}
Geben Sie nun den Befehl 
```bash
mysql_secure_installation
```
 ein. Bei der ersten Abfrage des aktuellen Passworts müssen Sie nichts eingeben, sondern einfach die Enter-Taste drücken. Geben Sie bei der anschließenden Frage bzgl. des Wechsels zur Unix-Socket-Authentifizierung **'n'** ein und drücken Sie die Enter-Taste. 
 Bestätigen Sie die nächste Frage bzgl. der Änderung des Root-Passworts mit Enter. Nun müssen Sie ein Passwort für den Root-Benutzer des MariaDB-Servers vergeben. Während der Eingabe erscheinen keine Zeichen, das ist jedoch normal. Bestätigen Sie alle darauffolgenden 
 Fragen (Löschung des anonymen Benutzers, Verbieten des externen Root-Logins aus Sicherheitsgründen, Entfernen der Testdatenbank und Aktualisieren der Rechte) ebenfalls mit Enter. Danach ist der MariaDB-Server fertig installiert und konfiguriert.

{% endtab %}
{% endtabs %}

* Wechseln Sie mit dem Befehl 
```bash
cd /usr/share
```
in das Verzeichnis, in dem phpMyAdmin installiert wird.

* Um phpMyAdmin herunterzuladen, führen Sie nun den Befehl aus
```bash
wget https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-all-languages.zip -O phpmyadmin.zip
```

* Entpacken Sie das soeben heruntergeladene Archiv mit dem folgenden Befehl: 
```bash
unzip phpmyadmin.zip
```

* Entfernen Sie das heruntergeladene Archiv, welches nun bereits entpackt ist, mit dem Befehl
```bash
rm phpmyadmin.zip
```

* Anschließend müssen Sie den Namen des entpackten Verzeichnisses zu **"phpmyadmin"** umbenennen. Dies machen Sie mit folgendem Befehl: 
```bash
mv phpMyAdmin-*-all-languages phpmyadmin
```

* Vergeben Sie anschließend die benötigten Rechte auf das phpMyAdmin-Verzeichnis mithilfe des Befehls 
```bash
chmod -R 0755 phpmyadmin
```

* Erstellen Sie nun eine Apache2-Konfigurationsdatei für phpMyAdmin, indem Sie den Befehl ausführen.
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
Speichern Sie Ihre Änderungen der Konfiguration, indem Sie **STRG + X, danach die "Y"-Taste und anschließend Enter** drücken.

* Aktivieren Sie die soeben hinzugefügte Apache2-Konfigurationsdatei mit dem Befehl 
```bash 
a2enconf phpmyadmin 
``` 
und führen daraufhin den Befehl 
```bash 
systemctl reload apache2
``` 
zum Neuladen des Apache2-Webservers aus.


* Erstellen Sie das temporäre Verzeichnis, welches phpMyAdmin benötigt, indem Sie den Befehl ausführen.
```bash 
mkdir /usr/share/phpmyadmin/tmp/
```

* Geben Sie dem Webserver-Benutzer nun die benötigten Besitzerrechte für dieses temporäre Verzeichnis mithilfe des Befehls 
```bash
chown -R www-data:www-data /usr/share/phpmyadmin/tmp/
```


## Hinweis: Bis einschließlich Debian 10 sowie unter Ubuntu können Sie sich aus Sicherheitsgründen mithilfe der Passwort-Authentifizierung beim MariaDB-Server standardmäßig nicht als Root-Nutzer anmelden (z.B. über phpMyAdmin). Unter Debian 11 ist dies jedoch möglich. Falls Sie nicht Debian 11 verwenden, führen Sie die nachfolgenden Schritte durch, um die Root-Anmeldung mittels Passwort zu erlauben.


* Bis einschließlich Debian 10 oder für Ubuntu:
1. Melden Sie sich in PuTTY mithilfe des Befehls am MariaDB-Server an.
```bash
mysql -u root
```
2.Führen Sie die Befehle aus. Hiermit ändern Sie das Authentifizierungsplugin des Root-Benutzers vom UNIX-Socket wieder auf die Standard-Authentifizierung.
```bash
UPDATE mysql.user SET plugin = 'mysql_native_password' WHERE user = 'root' AND plugin = 'unix_socket'; 
FLUSH PRIVILEGES;
```
3. Beenden Sie die MariaDB-Konsole abschließend mit dem Befehl.
```bash
exit
```
Ihr Apache2-Webserver inkl. PHP 8, MariaDB-Server und phpMyAdmin ist nun einsatzbereit. Das Web-Verzeichnis befindet sich standardmäßig unter **"/var/www/html/"**. Die phpMyAdmin-Weboberfläche erreichen Sie, indem Sie hinter der IP-Adresse oder Domain Ihres Servers im Browser **"/phpmyadmin"** anhängen. 
Dort können Sie sich jetzt am MariaDB-Server anmelden.

## Datenbank von außen erreichbar machen

Standardmäßig erlaubt eine MySQL-Datenbank nur Zugriffe durch den eigenen Server (`localhost`). Um ebenso Zugriffe von außerhalb zu erlauben, musst du mit
```bash
nano /etc/mysql/mariadb.conf.d/50-server.cnf
```
in die Konfigurationsdatei deiner Datenbank und den Punkt `bind-adress = 127.0.0.1` auf `0.0.0.0` ändern, sodass es am Ende folgendermaßen aussieht:
```bash
bind-adress = 0.0.0.0
```
Speichern Sie Ihre Änderungen der Konfiguration, indem Sie **STRG + X, danach die "Y"-Taste und anschließend Enter** drücken.
 
Danach musst du lediglich deine Datenbank neustarten, sodass die Änderungen wirksam werden (`service mysql restart`).


# Datenbank mit UFW absichern
Um deine Datenbank von außen abzusichern, kannst du das über die FireWall **UFW** machen:

Dafür installierst du dir erstmals **UFW** auf deinem Server mit folgendem Befehl:
```bash
apt install ufw -y
```
Danach geben wir die Standart Port nach außen offen ( SSH, HTTP, HTTPS ):
```bash
ufw allow 22
ufw allow 443
ufw allow 80
```
Danach aktivieren wir die UFW:
```bash
ufw enable
```
einfach mit **Y** bestätigen

![UFW ENABLE](https://auroa.link/uploads/auroa/2248f9ee-ae01-4e6f-bb51-085b2074ae34.jpg)

Nun Aktivieren wir UFW für die Datenbank:
```bash
ufw allow from DEINE-IP to any port 3306
```
Nach dem du das eingefügt hast kann nur die IP auf dem Server zugreifen die in der Liste steht
