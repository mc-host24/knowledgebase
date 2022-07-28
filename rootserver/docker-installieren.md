# Installation von Docker auf einem Rootserver

Virtualisierung ist etwas wichtiges und ist heutzutage deshalb überall vertreten. Dabei ist es z.B. sehr wichtig, dass die Infrastruktur ggf. einfach erweiterbar ist und dabei noch eine Zentrale Management-Oberfläche bietet. 

## Was ist Docker?

Docker ist eine leichtgewichtige Open-Source Virtualisierungssoftware um Dienste bzw. Anwendungen isoliert auf einem einzelnen System bereitzustellen. Im Gegensatz zu richtigen Virtuellen Maschinen wird hierfür kein extra Betriebssystem emuliert bzw. gehostet, sondern explizit nur eine Anwendungsumgebung innerhalb des Hostsystemes. Das ist nicht nur allgemein Ressourcen sparend, sondern verursacht gleichzeitig im Vergleich zur Voll Virtualisierung einen niedrigen Overhead.

## Wie installiere ich es?

Als allererstes muss überprüft werden, ob das Betriebssystem, welches auf deinem Root-Server läuft, Docker-fähig ist. Dafür braucht man eine Linux-Kernel-Version ab 3.10 oder höher, man kann es auch mit uname -r überprüfen.

Als nächstens müssen wir den GPG-Key also die Schlüsseldatei von Docker zu unserem System hinzufügen:
apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

Anschließend fügen wir Docker zu unseren Paketquellen hinzu, sodass wir das Paket via apt-get installieren können. 
echo "deb https://apt.dockerproject.org/repo debian-jessie main" >> /etc/apt/sources.list.d/docker.list 

Sobald dies erledigt ist, kann Docker heruntergeladen werden. Dabei ist wichtig, dass "apt-get" die Berechtigung hat, Pakete von HTTPS-Seiten herunterzuladen. Jetzt sollten die folgenden Befehle ausgeführt werden:

- apt-get update && apt-get install docker-engine (Updatet die Paketquellen und lädt Docker komplett runter) 
- systemctl start docker (Startet den Docker Service) 
- systemctl enable docker (Autostart beim Bootvorgang von der Distribution) 

Wenn das alles erledigt wurde, solltest du einmal checken, ob Docker läuft: 
systemctl status docker

Wenn das so aussieht und dort bei Active (running) steht, wurde Docker komplett ohne Probleme Installiert. 
Mit einem docker run hello-world kann man dann checken ob Docker auch korrekt ausgeführt wird.

Die Ausgabe sollte so aussehen:

Nun kannst du einfach los legen und Docker verwenden.
