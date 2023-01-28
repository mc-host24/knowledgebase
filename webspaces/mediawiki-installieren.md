# MediaWiki 1.39.1 LTS auf deinem Webspace installieren

MediaWiki ist eine Software, mit der man sich eigene Wikis erstellen kann. Sie wird z.B. von der bekannten Wikipedia benutzt und bietet viele Features an.

## Einrichtung 
### Vorbereitung
Bevor MediaWiki installiert wird, sollten einige gewisse Vorbereitungen vorgenommen werden. Dazu gehört z.B. der Download der Software, die Einrichtung der zu verwendenden Datenbank (z.B. MariaDB) und der Mailserver für die E-Mail Adresse.

### Software
Die Software kann auf der offiziellen Webseite von MediaWiki heruntergeladen werden. Der Download für die ZIP-Datei ist hier zu finden: https://releases.wikimedia.org/mediawiki/1.39/mediawiki-1.39.1.zip
und der für die TGZ-Datei hier:
https://releases.wikimedia.org/mediawiki/1.39/mediawiki-1.39.1.tar.gz

Beim Download erhält man eine gepackte ZIP-Datei, welche auf dem lokalen Computer entpackt werden muss. Darin befindet sich dann ein Ordner. Dessen Inhalt wird benötigt und muss entweder per FTP oder Datei-Manager hochgeladen werden. In diesem Beispiel wird die Einrichtung mittels FTP gezeigt.

Nachdem man sich einen FTP-Account erstellt hat, verbindet man sich mit dem Webspace, navigiert ins httpdocs-Verzeichnis und lädt im Anschluss die Wordpress-Dateien hoch.

### Datenbank

Ohne eine Datenbank kann MediaWiki nicht richtig funktionieren. Deshalb ist die Anlage einer Datenbank sehr wichtig, damit alles richtig funktioniert und reibungslos läuft.

Die Datenbank kann ganz einfach angelegt werden. Einfach den Menüpunkt "Datenbanken" suchen und dort nach "Hinzufügen" bzw. "Erstellen" suchen. Jetzt wurde die Datenbank erfolgreich angelegt.

### E-Mail-Server

Um einen Account bei der Website zu registrieren wird ein Mailserver mit einer E-Mail-Adresse benötigt, damit die Registrierungs-Mails auch an die Benutzer verschickt werden können.

### Installation

Sind alle Vorbereitungsschritte erfüllt worden, kann mit der Installation von MediaWiki begonnen werden. Dafür muss man im Internetbrowser die Webseite aufrufen. Dort angelangt klickt man auf Los geht's!, um mit der Einrichtung anzufangen. Als erstes steht dann die Konfiguration der Datenbank an, welche bereits im Voraus in der Vorbereitung erstellt wurde. Die Datenbank-Informationen von der erstellten Datenbank müssen nun dort eingetragen werden. Klicke im Anschluss auf Senden und im folgenden Schritt auf Installation durchführen.

Nun benötigt MediaWiki noch weitere Informationen. Hier kann z.B. nun der Titel des Wikis, Benutzername, Passwort, Sprache und die E-Mail-Adresse angegeben werden. Wenn alle Felder ausgefüllt wurden, muss man im Anschluss auf MediaWiki installieren klicken. Die Installation wird dann innerhalb weniger Sekunden abgeschlossen und es öffnet sich das Login-Fenster. Dort kannst du dich nun mit deinem erstellten Account einloggen. Im Anschluss kannst du dein Wiki nach deinen Wünschen beliebig einrichten!
