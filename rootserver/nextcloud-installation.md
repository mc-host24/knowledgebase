# Nextcloud, Apache2 und MySQL Installation

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
## Installation von Apache2
* Installiere den Apache2 Webserver
```bash
apt install apache2 -y
```
## Installation von PHP
* Installiere PHP8 sowie die PHP-Module
```bash
apt install php8.0 php8.0-cli php8.0-common php8.0-curl php8.0-gd php8.0-intl php8.0-mbstring php8.0-mysql php8.0-opcache php8.0-readline php8.0-xml php8.0-xsl php8.0-zip php8.0-bz2 libapache2-mod-php8.0 -y
```
## Installation von PHPMyAdmin
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
in das Verzeichnis, wo PhpMyAdmin installiert wird.

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

* Gebe dem Webnutzer die Berechtigung, auf das temporäre Verzeichnis zuzugreifen.
```bash
chown -R www-data:www-data /usr/share/phpmyadmin/tmp/
```

{% tabs %}
{% tab title="Debian 10 & Ubuntu" %}
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
{% endtab %}

{% tab title="Debian 11" %}
* Melde dich bei dem MySQL Server an

```bash
mysql -u root
```

* Erstelle einen neuen Benutzer. Trage bei "username" einen Benutzernamen und bei "password" ein Passwort ein.
```bash
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
```

* Dieser Befehl weißt deinem Nutzernamen alle Rechte, die man als Inhaber braucht
```bash
GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' WITH GRANT OPTION;
```

```bash 
exit
```
{% endtab %}
{% endtabs %}

## Installation von Nextcloud

* Navigiere zum path vom Web-Server
```bash 
cd /var/www/html
```

* Lade Nextcloud herunter
```bash 
wget https://download.nextcloud.com/server/releases/latest.tar.bz2
```

* Entpacke Nextcloud
```bash 
tar xfvj latest.tar.bz2
```

* Lösche das Nextcloud Archiv
```bash 
rm latest.tar.bz2
```

* Aktiviere Apache2 mod_rewrite
```bash 
a2enmod rewrite
```

* Starte Apache2 neu
```bash 
systemctl restart apache2
```

* Gebe dem Webserver das Besitzerrecht.
```bash 
chown -R www-data:www-data /var/www/html/nextcloud/
```

## Nextcloud Nutzer anlegen

![Gebe in deinem Browser deine IP/phpmyadmin ein.](https://bilderupload.org/image/a98a79993-screenshot-2022-06-17-173.png)

![Melde dich mit deinen PhpMyAdmin Nutzernamen und Password an, welchen du vorhin erstellt hast.](https://bilderupload.org/image/e58680326-screenshot-2022-06-17-173.png)

![Navigiere nun zum Punkt: Benutzerkonten](https://bilderupload.org/image/364580680-pupsl.png)

![Drücke auf Benutzerkonto hinzufügen](https://bilderupload.org/image/d1d680789-pupsanlegen.png)

![nun lege einen Benutzernamen und Password ein für Nextcloud an.
Wähle "Erstelle eine Datenbank mit gleichem Namen und gewähre alle Rechte" aus.
Scrolle runter und drücke auf "OK"](https://bilderupload.org/image/a7c980993-anlegenfertig.png)

![Nachdem der Benutzer und die Datenbank erfolgreich angelegt wurde, gebe in deinem Browser IP/nextcloud ein.](https://bilderupload.org/image/903c82182-nextcloud.png)

![Trage oben deinen Wunsch Benutzernamen und Passwort für Nextcloud ein.
Trage bei den unteren Feldern (Datenbank Informationen) deine MySQL Daten ein.
und drücke auf: "Installieren"](https://bilderupload.org/image/3d8e82457-nextcloudfertig.png)

# Nun ist die Installation von Nextcloud erfolgreich abgeschlossen
