# Setup Java 17 Debian

Wichtig ist, dass Sie zuerst Paketliste von Ihrem Debian Betriebssystem aktualisieren und mögliche Updates installieren. Dies können Sie mit einem einfachen Befehl durchführen:
``` bash
apt update && apt upgrade -y
```

Falls Sie Java-17 auf Debian 11 o. 12 installieren möchten, können Sie dies mit einem einfachen Befehl durchführen:
``` bash
apt install openjdk-17-jre-headless -y
```

Falls Sie allerdings gerne Java-17 auf Debian-10 installieren möchten, führen Sie bitte folgenden Befehl durch:
``` bash
apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 73C3DB2A && echo "deb http://ppa.launchpad.net/linuxuprising/java/ubuntu focal main" | tee /etc/apt/sources.list.d/java.list && apt update && apt install oracle-java17-installer -y
```

Mit diesem Befehl kannst du die Version überprüfen

``` bash
java -version
```
Beispielausgabe:
```
openjdk version "17.0.9" 2023-10-17
OpenJDK Runtime Environment (build 17.0.9+9-Debian-1deb11u1)
OpenJDK 64-Bit Server VM (build 17.0.9+9-Debian-1deb11u1, mixed mode, sharing)
```


# Setup Java 17 Ubuntu

Wichtig ist, dass Sie zuerst Paketliste von Ihrem Debian Betriebssystem aktualisieren und mögliche Updates installieren. Dies können Sie mit einem einfachen Befehl durchführen:
``` bash
apt update && apt upgrade -y
```

Sobald Sie alle Packages aktualisiert haben, müssen Sie als nächstes das Software-Properties-Common Package installieren, um die Paketquellen besser verwalten zu können:
``` bash
apt install software-properties-common -y
```

Danach fügen Sie Java zu Ihrer Repository, um Java-17 in Ihrer Paketliste identifizieren zu können:

``` bash
add-apt-repository ppa:linuxuprising/java
```
mit **Enter** bestätigen

Anschließend müssen Sie wieder Ihre Paketliste aktualisieren:
``` bash
apt update && apt upgrade -y
```

Sobald Sie Ihre Paketliste aktualisiert haben, so können Sie problemlos nun Java-17 vollständig installieren:
``` bash
apt install oracle-java17-installer -y
```
Dann jeweils Bestätigen 


Mit diesem Befehl kannst du die Version überprüfen

``` bash
java -version
```
Beispielausgabe:
```
java version "17.0.6" 2023-01-17 LTS
Java(TM) SE Runtime Environment (build 17.0.6+9-LTS-190)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.6+9-LTS-190, mixed mode, sharing)
```
