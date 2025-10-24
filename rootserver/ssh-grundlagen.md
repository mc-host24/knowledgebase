# SSH Setup

## Was ist SSH?
Mit `ssh` kann man sich mit seinem Server verbinden und Befehle ausführen

## Grundlegende Syntax
Mit
```bash
ssh <NUTZER>@<SERVER>
```
kann man sich mit seinem Server verbinden.

Wenn du einen Rootserver bei mc-host24 nutzt, kannst du mit `ssh root@<Rootserver-IP>` auf deinen Server zugreifen.

## SSH Keys
Mit `ssh-keygen` kann man sich sogenannte SSH-Keys erstellen.
Diese kann man anstatt eines Passworts nutzen, um sich mit seinem Server zu verbinden.

Um z. B. einen SSH-Key des Typs `rsa` zu erstellen, führe Folgendes aus:
```bash
ssh-keygen -t rsa
```
Beim Erstellen können alle Fragen einfach durch mehrmaliges Enter übersprungen werden.
Letztendlich wird die Ausgabe etwa so aussehen:
```
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\NUTZER/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in C:\Users\NUTZER/.ssh/id_rsa
Your public key has been saved in C:\Users\BENUTZER/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:xtfYMWr37hjNlpqEvEcVCRvQbvjncasYwmcssKyqXHM NUTZER@windows-dell-xe016
The key's randomart image is:
+---[RSA 3072]----+
|          .oo. . |
|            .oo  |
|           o+  . |
|       .  .=oo.  |
|       .S =o+.   |
|      ..++.oo+o..|
|   o E o +o*oo*o.|
|. . o .   =o+B.. |
| o....    .o+o+  |
+----[SHA256]-----+
```
Dies erstellt anschließend zwei Dateien unter `C:/Users/<DEIN BENUTZERNAME>/.ssh`:
- `id_rsa` ist dein "private key", diesen solltest du unter keinen Umständen weitergeben
- `id_rsa.pub` ist dein "public key", mit dieser Datei kann verifiziert werden, dass du im Besitz des private keys bist, ohne dass du deinen private key herausgeben musst
Die SSH-Keys werden anschließend in `C:/Users/<DEIN BENUTZERNAME>/.ssh` gespeichert.
Um diese SSH-Keys tatsächlich nutzen zu können, muss der sogenannte public key (erkennbar an der Endung `.pub`) zuerst auf den Server kopiert werden.
Dies kann man mit einem Tool namens `scp` erledigen:
```bash
scp C:/Users/<NUTZER>/.ssh/id_rsa.pub <SERVER-NUTZER>@<SERVER-IP>:~/.ssh/authorized_keys
```
Nun sollte man sich mit
```bash
ssh <SERVER-NUTZER>@<SERVER>
```
zum Server verbinden können, ohne sein Passwort zu nutzen.

{% hint style="danger" %}
Auf keinen Fall den Private Key (`id_rsa`) weitergeben! **Der Schlüssel hat kein Passwort oder zusätzliche Sicherheitsmaßnahmen. Jeder mit dem Private Key kann auf euren Server zugreifen!**
{% endhint %}

### Häufige Fehler
#### No such file or directory bei scp
```
scp: dest open ".ssh/authorized_keys": No such file or directory
scp: failed to upload file ./a.pub to ~/.ssh/authorized_keys
```
**Lösung**:
Verbinde dich mit dem Server
```bash
ssh <NUTZER>@<SERVER>
```
und erstelle das `.ssh` Verzeichnis:
```
mkdir ~/.ssh
chmod 700 ~/.ssh
```
Führe anschließend den `scp` Befehl erneut aus

#### Ich habe den Schlüssel hochgeladen, werde aber immer noch nach einem Passwort gefragt

Stelle sicher, dass:
- Die lokale Schlüsseldatei unter `C:\USERS\<NUTZER>\.ssh\id_rsa` gespeichert ist, mit `-i <SCHLÜSSELDATEI>` angegeben ist, oder ein Server-Alias mit einem `IdentityFile` benutzt wird
- Die `authorized_keys` die korrekten Berechtigungen hat:
	Führe dafür Folgendes auf deinem Server aus:
	```bash
	chmod 600 ~/.ssh/authorized_keys
 	```

## Server-Alias
Um nicht jedes Mal die IP-Adresse des Servers eintippen zu müssen, kann man sich auch einen alternativen Namen festlegen.
Diesen kann man festlegen, indem man die Datei `C:/Users/<NUTZER>/.ssh/config` editiert (falls die Datei nicht vorhanden ist, einfach selbst erstellen):
```
Host <Alternativer-Name>
	HostName <Tatsächliche-IP-Adresse>
```
Von nun an kann man sich mit dem Server auch mit dem folgenden Befehl verbinden:
```bash
ssh <NUTZER>@<Alternativer-Name>
```

## Weitere Ressourcen zum Thema SSH
[CCC: Besser leben mit SSH](https://media.ccc.de/v/gpn20-8-besser-leben-mit-ssh) - Interessanter Vortrag mit einigen Tipps zu SSH
[Wikipedia](https://de.wikipedia.org/wiki/Secure_Shell) - Erklärt gut die Geschichte und weiteren Funktionen von SSH
