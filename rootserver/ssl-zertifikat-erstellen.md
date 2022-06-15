# Wie erstelle ich auf meinem Rootserver mit Hilfe von Certbot ein SSL Zertifikat?


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

3. Wähle aus, ob eine Gemeinnützige Organisation (Electronic Frontier Foundation) deine E-Mail-Adresse bekommen darf.

4. Gebe deinen Domainnamen ein (z.B. mc-host24.de). Falls eine Subdomain vorhanden ist gebe diese mit an. (z.B. docs.mc-host24.de)

Das Zertifikat ist jetzt auf deinem Apache Webserver installiert.