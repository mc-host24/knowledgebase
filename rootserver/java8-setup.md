# Setup Java 8


Installieren Sie die benötigten Pakete
``` bash
apt install apt-transport-https ca-certificates wget dirmngr gnupg software-properties-common -y
```

Fügen Sie den Publickey für das Java 8 Repository hinzu und hinterlegen das Repository auf Ihrem Server

``` bash
wget -qO - https://adoptopenjdk.jfrog.io/adoptopenjdk/api/gpg/key/public | apt-key add - && add-apt-repository --yes https://adoptopenjdk.jfrog.io/adoptopenjdk/deb/
```

Aktualisieren Sie die Paketquellen

``` bash
apt update
```

Installieren Sie Java8

``` bash
apt install adoptopenjdk-8-hotspot -y
```

Mit diesem Befehl kannst du die Version überprüfen

``` bash
java -version
```
Beispielausgabe:
```
openjdk version "1.8.0_292"
OpenJDK Runtime Environment (AdoptOpenJDK)(build 1.8.0_292-b10)
OpenJDK 64-Bit Server VM (AdoptOpenJDK)(build 25.292-b10, mixed mode)
```
