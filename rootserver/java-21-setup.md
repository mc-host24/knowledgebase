# Setup von Java 21 auf Debian 12 Rootservern

Zuerst muss die Paketliste des Rootservers aktualisiert werden. Dies kann mit dem folgenden Befehl gemacht werden:

``` bash
apt update && apt upgrade -y
```

Die Installation von Java 21 erfolgt mit diesem Befehl:

``` bash
sudo apt install openjdk-21-jdk
```

Falls Java manuell installiert werden soll, muss zuerst die [Debian-Package](https://download.oracle.com/java/21/latest/jdk-21_linux-x64_bin.deb) über diese Befehle heruntergeladen werden:

``` bash
wget https://download.oracle.com/java/21/latest/jdk-21_linux-x64_bin.deb
sudo dpkg -i jdk-21_linux-x64_bin.deb
java -version
```

Die Java-Version kann mit diesem Befehl überprüft werden:

``` bash
java -version
```

Die Ausgabe vom Terminal sieht dann so aus:

```
openjdk version "21.0.4" 2023-10-17
OpenJDK Runtime Environment (build 21.0.4+9-Debian-1deb11u1)
OpenJDK 64-Bit Server VM (build 21.0.4+9-Debian-1deb11u1, mixed mode, sharing)
```
