# Apache2 Weiterleitung zum Link

Installieren Sie die benötigten Pakete
``` bash
apt install apache2 -y
```

Navigiere in die .conf datei
``` bash
cd /etc/apache2/sites-available
```

Erstelle eine Beliebige datei. Als Beispiel:
{% tabs %}
{% tab title="Domain" %}
* Wenn du es nur mit deiner Domain machen möchtest empfehlen wir diese Struktur:

```bash
touch domain.de.conf
```
{% endtab %}

{% tab title="Sub-Domain" %}
* Wenn du es nur mit deiner Sub-Domain machen möchtest empfehlen wir diese Struktur:

```bash
touch sub.domain.de.conf
```
{% endtab %}
{% endtabs %}


Aktiviere nun Apache2 rewrite
```bash
a2enmod rewrite
```

nun füge diesen code ein:

{% tabs %}
{% tab title="Domain" %}
```bash
<VirtualHost *:80>
        ServerName domain.de
        Redirect 301 / https://beispiel.de
</VirtualHost>
```
{% endtab %}

{% tab title="Sub-Domain" %}

```bash
<VirtualHost *:80>
        ServerName sub.domain.de
        Redirect 301 / https://beispiel.de
</VirtualHost>
```
{% endtab %}
{% endtabs %}

Nun Aktiviere die Folgende datei, die du erstellt hast.

{% tabs %}
{% tab title="Domain" %}
```bash
a2ensite domain.de.conf
```
{% endtab %}

{% tab title="Sub-Domain" %}

```bash
a2ensite sub.domain.de.conf
```
{% endtab %}
{% endtabs %}

Starte Apache2 neu
```bash
systemctl restart apache2
```

## Wichtig! vergiss nicht einen A-Record Eintrag für deine Domain/Sub-Domain zu machen. Diese sollte auf deinem Server verweisen, wo auch dein Certbot läuft.

## Die Domains oder Sub-Domains einen Zertifikat austellen

Als erstes benötigen wir das Paket "snapd". Dies wird mit dem Command 
```bash
apt install snapd
```
installiert.

falls snapd bereits installiert ist, stelle mit dem Command 
```bash
snap install core; snap refresh core
```
sicher, dass snapd auf dem neusten Stand ist.

Nachdem das erledigt ist wird nun certbot installiert.

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

1. Gebe  deine E-mail-Adresse ein

2. Akzeptiere die Terms of Service

3. kannst du die erstellte/Aufgelistete Domain oder Sub-Domain Auswhälen

4. Das Zertifikat ist jetzt auf deiner Domain
