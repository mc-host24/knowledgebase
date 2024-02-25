# Linux Grundlagen

## Die wichtigsten Befehle

(**l**ist) < **ls** > gibt unter Linux den Inhalt der Verzeichnisse an, **-h** gibt in Kombination mit **-l** die Größe in einem für Menschen besser lesbaren Format aus , **-a** listet auch versteckte Dateien und Verzeichniseinträge wie . und .. auf
```bash
ls -lha
```

(**c**hange **d**irectory) Wechsel der Verzeichnisse

```bash
cd
```

(**dir**ectory) Verzeichnisse auflisten

```bash
dir
```

(**r**e**m**ove) Dateien löschen

```bash
rm
```

Passwort ändern

```bash
passwd
```

(**s**ubstitute **u**ser) Benutzer wechseln

```bash
su
```

Fenster leeren

```bash
clear
```

Dateisystem und Speicherplatz anzeigen lassen

```bash
df
```

Wo bin ich?

```bash
pwd
```

Wer bin ich?

```bash
who
```

Eine Textdatei anzeigen oder erstellen

```bash
cat
```

Benutzer hinzufügen

```bash
adduser
```

Updates herunterladen

```bash
apt-get update
```

Updates verarbeiten

```bash
apt-get upgrade -y
```

## Dateirechte

Chmod

* Syntax: chmod XYZ datei

X: Besitzerrechte

Y: Gruppenrechte

Z: Rechte für andere Benutzer

|                                |   |
| ------------------------------ | - |
| Lesen, schreiben und ausführen | 7 |
| Lesen und Schreiben            | 6 |
| Lesen und ausführen            | 5 |
| Nur lesen                      | 4 |
| Schreiben und ausführen        | 3 |
| Nur schreiben                  | 2 |
| Nur ausführen                  | 1 |

## Nützliche Tools

### htop

![htop](../.gitbook/assets/HTOP.png)

Mit dem Prozessmanager "htop" kann man die laufenden Prozesse sowie die freien/belegten Systemressourcen anschauen. Installiert wird htop mit dem Command

```bash
apt install htop -y
```
Nach der Installation kann htop mit dem Command

```bash
htop
```
verwenden.

### btop

![btop](https://auroa.link/uploads/auroa/1296c2d4-9c69-435e-958b-0b242d8ecd32.jpg)

Mit dem Prozessmanager "btop" kann man die laufenden Prozesse sowie die freien/belegten Systemressourcen anschauen. Installiert wird btop mit dem Command:

```bash
apt install btop -y 
```

Alternativ kannst du es auch über Snap installieren.

```bash
apt install snapd -y && snap install btop 
```


Nach der Installation kann htop mit dem Command

```bash
btop
```
verwenden.

### netstat ( zusatz:  **-tulpen** )

![netstat](../.gitbook/assets/netstat.png)

Mit dem Diagnose-Werkzeug "netstat" kann man verschiedene Informationen über den Status der Netzwerkschnittstelle(n) abrufen.
Installiert wird netstat mit dem Command
```bash
apt install net-tools -y
```

Mit dem Command
```bash
netstat -ltnp | grep -w ':25565'
```
kann man z.B. nachschauen, von welchem Service der Port 25565 aktuell verwendet wird.

Mit dem Command: 

```bash
netstat -tulpen
```
Kannst du dir alle Aktuellen offene Ports anschauen, ebenfalls welcher Port mit welcher IP gebunden ist.
Ebenfalls wird dir dann angezeigt, welcher Service denn Port verwendet.

![netstat](https://auroa.link/uploads/auroa/817c6729-8412-4556-b89c-6d41743bb192.jpg)


### ncdu

Mit dem Tool "ncdu" kann man die Disk Usage analysieren.
Installiert wird ncdu mit dem Command
```bash
apt install ncdu
```
Verwendet man den Command 
```bash
ncdu /
```
bekommt man solch eine Anzeige:

![Grüner Programmcode in schwarzem Terminal vom Programm ncdu](../.gitbook/assets/ncdu.png)

Navigiert wird mit den Pfeiltasten. Um in ein Verzeichnis rein zu gehen drücke "Enter".

* Mit der Taste "d" können Dateien oder Verzeichnisse gelöscht werden.
* Mit der Taste "i" kannst du dir Informationen zu der aktuell ausgewählten Datei anzeigen lassen
* Mit der Taste "b" landest du mit der Shell in dem ausgewählten Ordner.
* Mit der Taste "q" beendest du ncdu

### ufw

Mit dem Programm "ufw" kannst du Ports auf deinem Server verwalten. Dabei nutzt "ufw" das Programm "[iptables](https://de.m.wikipedia.org/wiki/Iptables)", um die Ports zu sperren/freizuschalten.

Installiert wird ufw mit dem Command:
```bash
apt install ufw
```
Um Ports freizuschalten, verwende:
```bash
ufw allow 80
```
_(Hiermit schaltest du Port "80" (Webserver/HTTP) frei.)_

Um einen Port zu schließen, nutze:
```bash
ufw deny 80
```
_(Hiermit blockierst du Port "80" (Webserver/HTTP).)_

Um UFW zu aktivieren, verwende: 
```bash
ufw enable
```

Um UFW zu deaktivieren, nutze:
```bash
ufw disable
```

Um alle freigegebenen Ports anzusehen, nutze:
```bash
ufw status
```
