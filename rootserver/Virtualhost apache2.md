# Virtualhost (Apache2)

## Apache2 Virtualhost

Installieren Sie die benötigten Pakete

```bash
apt install apache2 -y
```

Navigiere in die `sites-available` Datei

```bash
cd /etc/apache2/sites-available
```

Erstelle eine `.conf` Datei. Als Beispiel: `domain.de.conf`

```bash
touch domain.de.conf
```

Aktiviere nun Apache2 `rewrite` & `headers`

```bash
a2enmod rewrite
```

```bash
a2enmod headers
```

nun füge diesen code in deine `.conf` Datei ein:

```bash
<VirtualHost *:80>
        ServerName deinedomain.de
        DocumentRoot /var/www/dein_verzeichnis
RewriteEngine on
RewriteCond %{SERVER_NAME} =deinedomain.de
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>
```

Speicher die Datei mit `STRG + O` & danach mit `STRG + X`

Aktiviere die `.conf` Datei:

```bash
a2ensite domain.de.conf
```

Starte nun Apache2 neu:

```bash
systemctl restart apache2
```

### Domain SSL Verschlüsseln

{% hint style="danger" %}
Vergiss nicht, einen A-Record Eintrag für deine Domain/Sub-Domain zu machen. Diese sollte auf deinem Server verweisen, wo auch dein Certbot läuft.
{% endhint %}

Als Erstes benötigen wir das Paket `snapd`. Dies wird mit dem Command

```bash
apt install snapd
```

installiert.

falls snapd bereits installiert ist, stelle mit dem Command

```bash
snap install core; snap refresh core
```

sicher, dass snapd auf dem neusten Stand ist.

Nachdem diese erledigt ist, wird nun certbot installiert.

```bash
snap install --classic certbot
```

Damit der Certbot Command verwendet werden kann, gebe folgenden Command ein:

```bash
ln -s /snap/bin/certbot /usr/bin/certbot
```

Um das Zertifikat automatisch auf deinem Apache Webserver einrichten zu lassen, verwende folgenden Command:

```bash
certbot --apache
```

1. Gebe deine E-mail-Adresse ein
2. Akzeptiere die Terms of Service
3. kannst du die erstellte/Aufgelistete Domain oder Sub-Domain Auswhälen
4. Das Zertifikat ist jetzt auf deiner Domain
