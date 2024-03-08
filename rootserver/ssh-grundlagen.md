# SSH Setup

## Was ist SSH?
`SSH` (Secure Shell) ist ein Protokoll, das eine sichere Verbindung ermöglicht, um auf entfernte Computer zuzugreifen und Befehle auszuführen, indem es Verschlüsselung und Authentifizierung verwendet. Es dient dazu, Datenübertragungen und Interaktionen zwischen Computern über unsichere Netzwerke wie das Internet abzusichern.

## Grundlegende Syntax
Mit folgendem Command
```bash
ssh <NUTZER>@<SERVER-IP>
```
kann eine Verbindung zu deinem Server aufgebaut werden.

## SSH Keys
Mit `ssh-keygen` können sogenannte SSH-Keys erstellt werden.
Diese können an Stelle eines Passworts genutzt werden, um sich mit einem Server zu verbinden.
Diese SSH Keys werden anschließend in `C:/Users/<DEIN BENUTZERNAME>/.ssh` gespeichert.
Um diese SSH Keys nutzen zu können muss der sogenannte "public key" (erkennbar an der Endung `.pub`) zuerst auf den Server kopiert werden.
Dies kann man mit einem Tool wie `scp` erledigen:
```bash
scp C:/Users/<NUTZER>/.ssh/id_rsa.pub <SERVER-NUTZER>@<SERVER-IP>:~/.ssh
```
Nun sollte man sich mit
```bash
ssh <NUTZER>@<SERVER-IP>
```
zum Server verbinden können, ohne ein Passwort zu nutzen.

## WICHTIG: Die IP-Adresse deines Hosts kopiere dir bitte heraus.
Auf keinen Fall den private key (`id_rsa`) weitergeben. **Wenn der Schlüssel kein festgelegtes Passwort besitzt, kann jeder mit dem Schlüssel auf deinen Server zugreifen!**

## Server-Alias
Um nicht jedes Mal die IP-Adresse eines Servers eintippen zu müssen, kann auch ein alternativer Name (englisch: alias) festlegt werden.
Dieser kann gesetzt werden, indem `C:/Users/<NUTZER>/.ssh/config` wie folgend editiert wird (falls die Datei nicht vorhanden ist einfach selbst erstellen):
```
Host <Alternativer-Name>
	HostName <Tatsächliche-IP-Adresse>
```
Von nun an kann man sich mit dem Server auch mit dem folgenden Befehl verbinden:
```bash
ssh <NUTZER>@<Alternativer-Name>
```

## Weitere Ressourcen zum Thema SSH
[media.ccc.de](https://media.ccc.de/v/gpn20-8-besser-leben-mit-ssh) - Interessanter Vortrag mit einigen Tipps zu SSH
<br>
[wikipedia.org](https://de.wikipedia.org/wiki/Secure_Shell) - Erklärt gut die Geschichte und weiteren Funktionen von SSH
