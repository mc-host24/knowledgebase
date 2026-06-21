Dieses Tutorial erklärt, wie man sich bei MC-Host24 einen Landwirtschafts-Simulator 22-Server konfigurieren kann.

# System-Anforderungen

Benötigt wird ein Windows-Server mit Windows-Server 2016 oder 2019 als Software. Der Prozessor sollte mindestens mit 2,4GHz getaktet sein und eine 64-Bit-Architektur haben. An Speicherplatz wird mindestens 2GB Arbeitsspeicher (4GB-6GB für [Mods](landwirtschafts-simulator22/mods-installieren.md) und 6GB SSD-Speicher benötigt. Auch braucht man eine eigene, offizielle Game-Lizenz und eine öffentliche IPv4 bzw. IPv6-Adresse dafür.

# Arbeitsschritte
## 1. Die Lizenz herunterladen

Es wird eine digitale Version des Landwirtschafts-Simulator 2022 benötigt, es darf keine Steam Version sein. Die digitale Version kann auf der Landwirtschafts-Simulator Webseite erworben werden. Nachdem die digitale Version erworben wurde, kann der Landwirtschafts-Simulator online gedownloadet werden, dazu einfach dem Link aus der Mail, die von Giants verschickt wurde, folgen.

## 2. Download des Servers

Als nächstes muss man sich mit Remote Desktop (RDP) zum Windows-Server verbinden. Nach der Verbindung muss man nochmals den Link aus der E-Mail aufrufen, um dort den Game Key einzugeben. Jetzt muss man den Download für die auf dem Server installierte Windows-Version auswählen. Anschließend wird die Datei heruntergeladen und sollte sich dann im Download Verzeichnis befinden. (Das Downloadverzeichnis kann abweichend sein)
Mit einem Doppelklick wird die Datei geöffnet und es kann die Setup.exe ausgeführt werden. Anschließend liest man die TOS und bestätigt sie. Danach kann die Installation als Standard oder Benutzerdefiniert erfolgen, in der Regel reicht Standard aus. Zum Abschluss klickt man auf installieren und der Landwirtschafts-Simulator 2022 wird nun installiert, dies kann einige Minuten dauern.
Sobald der Installationsvorgang beendet ist, erscheint folgende Meldung, welche mit "Fertigstellen" bestätigt werden kann.
Die Basis-Installation ist nun abgeschlossen.

## 3. Aktivierung des Servers

Nun muss der Landwirtschafts-Simulator gestartet werden. Auf dem Desktop sollte eine Verknüpfung liegen, falls nicht, kann er auch über das Windows Menü gestartet werden. Fehler bezüglich einer fehlenden GPU oder ähnliches können ignoriert bzw. mit Nein/Abbrechen geschlossen werden. Der Landwirtschafts-Simulator muss nur gestartet werden, um den Key eingeben zu können.
Nun muss in der Config des Dedicated Servers ein Login Name und Passwort gesetzt bzw. geändert/ausgelesen werden, damit ein Login in das Webinterface des Dedicated Servers möglich ist. Die Config ist in der Standardinstallation unter <code>C:\Program Files (x86)\Landwirtschafts-Simulator 2022</code> zu finden unter dem Namen "<code>dedicatedServer.xml</code>". Die Logindaten können frei angepasst werden.

## 4. Den Server starten

Um den Dedicated Server zu starten, muss im gleichen Verzeichnis, wo auch die <code>"dedicatedServer.xml"</code> liegt, die <code>"dedicatedServer.exe"</code> ausgeführt werden.
Anschließend kann das Webinterface via <code>https://SERVER-IP:8080</code> geöffnet werden.
Der Login ist mit den zuvor gesetzten/ausgelesenen Login Daten aus der <code>"dedicatedServer.xml"</code> möglich. Die weitere Konfiguration ist im Webinterface selbsterklärend und kann mit wenigen Klicks vorgenommen werden, ganz nach den persönlichen Wünschen.

## 5. Die Ports freigeben

Der Server soll natürlich öffentlich erreichbar sein um mit Freunden spielen zu können. Dazu müssen die Ports des Servers in der Windows Firewall freigeschaltet werden. Es müssen die Ports 10823 und 8080 freigegeben werden für das Protokoll TCP. 10823 ist dabei der Gameserverport und 8080 ist der Webport für das Webinterface, der Webport muss nur bei Bedarf freigegeben werden, eine Verwaltung kann auch weiterhin nur lokal auf dem Windows Server erfolgen via RDP.
Nach der Portfreigabe ist der Server öffentlich erreichbar, falls er gestartet wurde.

## 6. Verbindungsversuch

Das Spiel muss gestartet werden, damit man sich auf den Server, falls er online ist, verbinden kann. Jetzt muss man über „Server beitreten“ den Server-Browser aufrufen und auf der rechten Seite über den Server-/Spielnamen nach dem Server suchen. Danach muss man sich, falls es ein privater Server ist, nach der Passworteingabe mit dem Server verbinden. Hat alles geklappt, kann man auf dem Server spielen. Viel Spaß!

## 7. YouTube-Video

{% embed url="https://youtu.be/aAlAAhIIRoE" %}
