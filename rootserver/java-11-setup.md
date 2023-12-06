# Setup Java 11 Debian & Ubuntu

Wichtig ist, dass Sie zuerst Paketliste von Ihrem Debian Betriebssystem aktualisieren und mögliche Updates installieren. Dies können Sie mit einem einfachen Befehl durchführen:
``` bash
apt update && apt upgrade -y
```

Installieren Sie Java11

``` bash
apt install openjdk-11-jre-headless -y
```

Mit diesem Befehl kannst du die Version überprüfen

``` bash
java -version
```
Beispielausgabe:
```
openjdk version "11.0.21" 2023-10-17
OpenJDK Runtime Environment (build 11.0.21+9-post-Debian-1deb11u1)
OpenJDK 64-Bit Server VM (build 11.0.21+9-post-Debian-1deb11u1, mixed mode, sharing)
```
