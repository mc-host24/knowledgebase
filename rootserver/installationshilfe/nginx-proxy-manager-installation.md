# Nginx Proxy Manager Installation

!!! Wichtig !!!
Falls ihr Docker nicht installiert habt, folgt der Docker Installation:
{% embed url="https://docs.mc-host24.de/docs/rootserver/docker-installation" %}


* Aktualisiere die Paketlisten & installiere die Updates.
```bash
apt update && apt upgrade -y
```

* Erstelle ein Verzeichnis für ```Nginx Proxy Manager```
```bash
mkdir ~/nginx-proxy
```

* Navigiere ins Verzeichnis
```bash
cd ~/nginx-proxy
```

* Erstelle Verzeichnisse für Benutzerdaten und SSL-Zertifikate.
```bash
mkdir {data,letsencrypt}
```

* Erstelle nun eine Compose Datei
```bash
nano docker-compose.yml
```

* Füge nun diesen Code ein
```bash
version: '3'
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      - '80:80'
      - '81:81'
      - '443:443'
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```

* Bringe dein ```Nginx Proxy Manager``` zum laufen
```bash
docker-compose up -d
```

* Die Website kannst du unter http://127.0.0.1:81 oder mit der Public adresse mit dem port ```81``` ereichen.
* Die Standart daten zum anmelden sind:
```bash
Email:    admin@example.com
Password: changeme
```
