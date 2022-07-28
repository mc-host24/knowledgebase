# MongoDB Installation

* Aktualisiere die Paketlisten & installiere die Updates.

```bash
apt update && apt upgrade -y
```

* Installiere für die weitere Installation benötigte Pakete.

```bash
apt-get install curl apt-transport-https software-properties-common gnupg2 -y
```

* Installiere nun den GPG-Schlüssel und fügst ihn mit dem folgenden Befehl hinzu: 
```bash
wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | apt-key add -
```

* nun fügst du die MongoDB-Repository mit folgendem Befehl zur APT-Quellenlistendatei hinzu:
```bash
echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 main" | tee /etc/apt/sources.list.d/mongodb-org.list
```

* Als Nächstes aktualisierst du das Repository und installierst den MongoDB-Server
```bash
apt-get update -y
```
```bash
apt-get install mongodb-org -y
```

* Starte nun MongoDB-Dienst und aktiviere ihn
```bash
systemctl start mongod
```
```bash
systemctl enable mongod
```

* Verbinde dich nun mit dem MongoDB-Shell
```bash
mongo
```

* Erstelle eine Datenbank mit mit dem namen Admin
```bash
use admin
```

* Als Nächstes erstellst du einen Benutzer admin und legst ein Passwort fest
```bash
db.createUser(
{
user: "admin",
pwd: "Dein_Sicheres_Passwort",
roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
}
)
```

* Drücke ```STRG + D``` um die Shell zu verlassen und bearbeite als nächstes die MongoDB-Konfigurationsdatei
```bash
nano /etc/mongod.conf
```

* Füge diese zeile hinzu um die Authentifizierung zu aktivieren
```bash
security:
 authorization: enabled
```

* Speichere die Datei mit ```STRG + O``` danach verlasse die datei mit ```STRG + X``` und starte MongoDB neu:
```bash
systemctl restart mongod
```
