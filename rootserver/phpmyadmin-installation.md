# PhpMyAdmin, Apache2 und MySQL Installation

* Aktualisiere die Paketlisten & installiere die Updates.

```bash
apt update && apt upgrade -y
```

* Installiere für die weitere Installation benötigte Pakete.

```bash
apt install ca-certificates nano lsb-release gnupg apt-transport-https curl unzip -y
```

Wähle dein Betriebssystem aus.
Solltest du nicht wissen, welches Betriebssystem du verwendest, kannst du dies mit dem Befehl
```bash
cat /etc/issue
```
nachschauen.

{% tabs %}
{% tab title="Debian" %}
* Füge die Paket-Quelle für die PHP7.4 Version hinzu.

```bash
curl -fsSL https://packages.sury.org/php/apt.gpg -o /usr/share/keyrings/php-archive-keyring.gpg
```

```bash
echo "deb [signed-by=/usr/share/keyrings/php-archive-keyring.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
```
{% endtab %}

{% tab title="Ubuntu" %}
* Füge die Paket-Quelle für die PHP7.4 Version hinzu.

```bash
apt install software-properties-common -y
```

```bash
add-apt-repository ppa:ondrej/php
```
{% endtab %}
{% endtabs %}

* Aktualisiere noch einmal die Paketlisten
```bash
apt update
```

* Installiere den Apache2 Webserver
```bash
apt install apache2 -y
```

* Installiere PHP7.4 sowie die PHP-Module
```bash
apt install php7.4 php7.4-zip php7.4-bz2 php7.4-cli php7.4-common php7.4-xsl php7.4-curl php7.4-opcache php7.4-gd php7.4-intl php7.4-json php7.4-mbstring php7.4-mysql php7.4-readline php7.4-xml libapache2-mod-php7.4 -y
```

* Installiere MySQL
```bash
apt install mariadb-server mariadb-client -y
```

Schließe die MySQL Installation ab
{% tabs %}
{% tab title="Debian 10 & Ubuntu" %}
Gebe den Befehl 
```bash
mysql_secure_installation
``` 
ein. Bei der ersten Abfrage des aktuellen Passworts drücke einfach "Enter". Bestätige die nächste Frage bzgl. der Änderung des Root-Passworts mit "Enter". Nun musst du ein Passwort für den Root-Benutzer des MariaDB-Servers vergeben. Während der Eingabe erscheinen keine Zeichen, das ist jedoch normal. Bestätige alle darauffolgenden Fragen (Löschung des anonymen Benutzers, Verbieten des externen Root-Logins aus Sicherheitsgründen, Entfernen der Testdatenbank und Aktualisieren der Rechte) ebenfalls mit "Enter".

{% endtab %}

{% tab title="Debian 11" %}
Gebe den Befehl 
```bash
mysql_secure_installation
```
ein. Bei der ersten Abfrage des aktuellen Passworts drücke einfach "Enter". Gebe bei der anschließenden Frage bzgl. des Wechsels zur Unix-Socket-Authentifizierung "n" ein und drücke die "Enter"-Taste. Bestätige die nächste Frage bzgl. der Änderung des Root-Passworts mit "Enter". Nun musst du ein Passwort für den Root-Benutzer des MariaDB-Servers vergeben. Während der Eingabe erscheinen keine Zeichen, das ist jedoch normal. Bestätige alle darauffolgenden Fragen (Löschung des anonymen Benutzers, Verbieten des externen Root-Logins aus Sicherheitsgründen, Entfernen der Testdatenbank und Aktualisieren der Rechte) ebenfalls mit "Enter".

{% endtab %}
{% endtabs %}

* Wechsel mit dem Befehl
```bash
cd /usr/share
```
in das Verzeichnis wo PhpMyAdmin installiert wird.

* Lade PhpMyAdmin herunter
```bash
wget https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-all-languages.zip -O phpmyadmin.zip
```

* Entpacke das Archiv
```bash
unzip phpmyadmin.zip
```

* Entferne das heruntergeladene Archiv
```bash
rm phpmyadmin.zip
```

Nenne das PhpMyAdmin Verzeichnis um
```bash
mv phpMyAdmin-*-all-languages phpmyadmin
```

Vergebe die benötigten Rechte
```bash
chmod -R 0755 phpmyadmin
```

* Erstelle die Apache Konfigurationsdatei
```bash
echo "Alias /phpmyadmin /usr/share/phpmyadmin

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
</Directory>" >> /etc/apache2/conf-available/phpmyadmin.conf
```

* Aktiviere die Apache Konfigurationsdatei
```bash
a2enconf phpmyadmin
```

* Reloade den Apache Service
```bash
systemctl reload apache2
```

* Erstelle das Temporäre Verzeichnis für PhpMyAdmin
```bash 
mkdir /usr/share/phpmyadmin/tmp/
```

* Gebe dem Webnutzer die Berechtigung auf das temporäre Verzeichnis zuzugreifen.
```bash
chown -R www-data:www-data /usr/share/phpmyadmin/tmp/
```

## Bis einschließlich Debian 10 oder Ubuntu

* Melde dich bei dem MySQL Server an
```bash
mysql -u root
```

* Stelle das Authentifizierungsplugin des Root-Benutzers von UNIX auf die Standardauthentifizierung um.
```bash
UPDATE mysql.user SET plugin = 'mysql_native_password' WHERE user = 'root' AND plugin = 'unix_socket';
```
```bash 
FLUSH PRIVILEGES;
```

Du kannst PhpMyAdmin nun mit deiner IP-Adresse oder Domain /phpmyadmin aufrufen.