# Wordpress 6.1.1 auf einem Webspace installieren

WordPress ist das meist verwendete freie Content-Management-System weltweit. Es wurde ab 2003 von Matthew Mullenweg als Software für Weblogs programmiert und wird als Open-Source-Projekt permanent weiterentwickelt. In dieser Anleitung erklären wir, wie diese Software auf dem Webspace installiert werden kann.

# Einrichtung
## Vorbereitung

Bevor man WordPress installiert, sollte man einige gewisse Vorbereitungen vornehmen. Dazu gehört z.B. das Besorgen der Software, die Einrichtung der zu verwendenden Datenbank (z.B. MariaDB) und der Mailserver (E-Mail Adresse).

## Software

Die Software kann auf der offiziellen Webseite von WordPress heruntergeladen werden. Der Download dazu ist hier zu finden: https://de.wordpress.org/download/

Beim Download erhält man eine gepackte ZIP-Datei, welche auf dem lokalen Computer entpackt werden muss. Darin befindet sich dann ein Ordner. Dessen Inhalt wird benötigt und muss entweder per FTP oder Datei-Manager hochgeladen werden. In diesem Beispiel wird die Einrichtung mittels FTP gezeigt.

Nachdem man sich einen FTP-Account erstellt hat, verbindet man sich mit dem Webspace, navigiert ins <b>httpdocs</b>-Verzeichnis und lädt im Anschluss die Wordpress-Dateien hoch.

## Datenbank

Ohne eine Datenbank kann WordPress nicht richtig funktionieren. Deshalb ist die Anlage einer Datenbank sehr wichtig, damit alles richtig funktioniert und reibungslos läuft.

Die Datenbank kann ganz einfach angelegt werden. Einfach den Menüpunkt "Datenbanken" suchen und dort nach "Hinzufügen" bzw. "Erstellen" suchen. Jetzt ist die Datenbank angelegt worden.

## E-Mail-Server

Um einen Account bei der Website zu registrieren wird ein Mailserver mit einer E-Mail-Adresse benötigt, damit die Registrierungs-Mails auch an die Benutzer verschickt werden können.

## Installation

Sind alle Vorbereitungsschritte erfüllt worden, kann mit der Installation von WordPress begonnen werden. Dafür muss man im Internetbrowser die Webseite aufrufen. Dort angelangt klickt man auf Los geht's!, um mit der Einrichtung anzufangen. Als erstes steht dann die Konfiguration der Datenbank an, welche bereits im Voraus in der Vorbereitung erstellt wurde. Die Datenbank-Informationen von der erstellten Datenbank müssen nun dort eingetragen werden. Klicke im Anschluss auf Senden und im folgenden Schritt auf Installation durchführen.

Nun benötigt WordPress noch weitere Informationen. Hier kann z.B. nun der Titel der Webseite, Benutzername, Passwort, und die E-Mail-Adresse angegeben werden. Wenn alle Felder ausgefüllt worden sind, muss man im Anschluss auf WordPress installieren klicken. Die Installation wird dann innerhalb weniger Sekunden abgeschlossen und es öffnet sich das Login-Fenster. Dort kannst du dich nun mit deinem erstellten Account einloggen. Im Anschluss kannst du dein WordPress nach deinen Wünschen beliebig einrichten!
