# PhpMyAdmin Installation

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
* Für die PHP 7.4 Installation benötigt man eine Paketquelle. Diese füge mit diesen Befehlen hinzu

```bash
curl -fsSL https://packages.sury.org/php/apt.gpg -o /usr/share/keyrings/php-archive-keyring.gpg
```

```bash
echo "deb [signed-by=/usr/share/keyrings/php-archive-keyring.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
```
{% endtab %}

{% tab title="Ubuntu" %}
* Für die PHP 7.4 Installation benötigt man eine Paketquelle. Diese füge mit diesen Befehlen hinzu

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

* Für PhpMyAdmin benötigt man einen Webserver. Diesen installiert man wiefolgt:
```bash
apt install apache2 -y
```

* Aus der hinzugefügten PHP Quelle installieren wir nun php7.4 und weitere benötigte Pakete.
```bash
apt install php7.4 php7.4-zip php7.4-bz2 php7.4-cli php7.4-common php7.4-xsl php7.4-curl php7.4-opcache php7.4-gd php7.4-intl php7.4-json php7.4-mbstring php7.4-mysql php7.4-readline php7.4-xml libapache2-mod-php7.4 -y
```

* Als nächstes muss MySQL installiert werden.
```bash
apt install mariadb-server mariadb-client -y
```

Die MySQL Installation muss nun noch abgeschlossen werden.
{% tabs %}
{% tab title="Debian 10 & Ubuntu" %}
Gebe nun den Befehl 
```bash
mysql_secure_installation
``` 
ein. Bei der ersten Abfrage des aktuellen Passworts müssen Sie nichts eingeben, sondern einfach die Enter-Taste drücken. Bestätigen Sie die nächste Frage bzgl. der Änderung des Root-Passworts mit Enter. Nun müssen Sie ein Passwort für den Root-Benutzer des MariaDB-Servers vergeben. Während der Eingabe erscheinen keine Zeichen, das ist jedoch normal. Bestätigen Sie alle darauffolgenden Fragen (Löschung des anonymen Benutzers, Verbieten des externen Root-Logins aus Sicherheitsgründen, Entfernen der Testdatenbank und Aktualisieren der Rechte) ebenfalls mit Enter. Danach ist der MariaDB-Server fertig installiert und konfiguriert.

{% endtab %}

{% tab title="Debian 11" %}
Gebe nun den Befehl 
```bash
mysql_secure_installation
```
ein. Bei der ersten Abfrage des aktuellen Passworts müssen Sie nichts eingeben, sondern einfach die Enter-Taste drücken. Bestätigen Sie die nächste Frage bzgl. der Änderung des Root-Passworts mit Enter. Nun müssen Sie ein Passwort für den Root-Benutzer des MariaDB-Servers vergeben. Während der Eingabe erscheinen keine Zeichen, das ist jedoch normal. Bestätigen Sie alle darauffolgenden Fragen (Löschung des anonymen Benutzers, Verbieten des externen Root-Logins aus Sicherheitsgründen, Entfernen der Testdatenbank und Aktualisieren der Rechte) ebenfalls mit Enter. Danach ist der MariaDB-Server fertig installiert und konfiguriert.

{% endtab %}
{% endtabs %}

* Wechsel mit dem Befehl
```bash
cd /usr/share
```
in das Verzeichnis wo PhpMyAdmin installiert wird.

* Um PhpMyAdmin herunterzuladen führe folgenden Befehl aus
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

Rename das PhpMyAdmin Verzeichnis
```bash
mv phpMyAdmin-*-all-languages phpmyadmin
```

Vergebe die benötigten Rechte
```bash
chmod -R 0755 phpmyadmin
```

* Damit du PhpMyAdmin im Browser aufrufen kannst erstelle die Apache Konfigurations Datei.
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

* Apache reloade
```bash
systemctl reload apache2
```

