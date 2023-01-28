# SSH Setup

## Was ist SSH?
Mit `ssh` kann man sich mit seinem Server verbinden und Befehle ausführen

## Grundlegende Syntax
Mit
```bash
ssh <NUTZER>@<SERVER>
```
kann man sich mit seinem Server verbinden

## SSH Keys
Mit `ssh-keygen` kann man sich sogenannte SSH-Keys erstellen.
Diese kann man an Stelle eines Passworts nutzen um sich mit seinem Server zu verbinden.
Die SSH Keys werden anschließend in `C:/Users/<DEIN BENUTZERNAME>/.ssh` gespeichert.
Um diese SSH Keys tatsächlich nutzen zu können muss der sogenannte public key (erkennbar an der Endung `.pub`) zuerst auf den Server kopiert werden.
Dies kann man mit einem Tool namens `scp` erledigen:
```bash
scp C:/Users/<NUTZER>/.ssh/id_rsa.pub <SERVER-NUTZER>@<SERVER-IP>:~/.ssh
```
Nun sollte man sich mit
```bash
ssh <NUTZER>@<SERVER>
``` zum Server verbinden können ohne sein Passwort zu nutzen.

## WICHTIGDie IP-Adresse deines Hosts kopiere dir bitte heraus.
Auf keinen Fall den private key (`id_rsa`) weitergeben. **Wenn der Schlüssel kein Passwort hat kann jeder mit dem Schlüssel auf euren Server zugreifen!**

## Server alias
Um nicht jedes Mal die IP-Adresse des Servers eintippen zu müssen kann man sich auch einen alternativen Namen festlegen.
Diesen kann man festlegen in dem man die Datei `C:/Users/<NUTZER>/.ssh/config` editiert (falls die Datei nicht vorhanden ist einfach selbst erstellen):
```
Host <Alternativer-Name>
	HostName <Tatsächliche-IP-Adresse>
```
Von nun an kann man sich mit dem Server auch mit dem folgenden Befehl verbinden:
```bash
ssh <NUTZER>@<Alternativer-Name>
```

## Weitere Ressourcen zum Thema SSH
https://media.ccc.de/v/gpn20-8-besser-leben-mit-ssh - Interessanter Vortrag mit einigen Tips zu ssh
https://de.wikipedia.org/wiki/Secure_Shell - Erklärt gut die Geschichte und weiteren Funktionen von SSH
