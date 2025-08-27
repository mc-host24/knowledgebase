# Mit (S)FTP auf Rootserver verbinden

Da auf deinem Rootserver standardmäßig kein normaler FTP-Server installiert ist, verbindest du dich über **SFTP** mit deinem Rootserver, um direkt Dateien mittels eines Datei-Browsers verwalten zu können.

Dazu benötigst du auch hier einen ganz normalen FTP-Client deiner Wahl, wie z.B. [WinSCP](https://winscp.net/eng/download.php) oder [Winrar](https://winrar.de/download.php).

Nach der Installation des FTP-Clients auf deinem Computer, kannst du das Programm direkt starten und wirst aufgefordert die Anmeldedaten zu deinem Server anzugeben.

* Als **Serveradresse/IP** gibst du ganz normal die IP-Adresse deines Rootservers an.
* Der **Benutzername** ist `root`, also derselbe Benutzer, welchen du beim SSH-Login angibst.
* Dementsprechend nutzt du als **Passwort** das Passwort deines `root`-Benutzers, welches du, falls du es nicht geändert hast, auf der [Meine-Server](https://mc-host24.de/myservers#rootserver)-Seite findest.
* Da es sich hier um SFTP (SSH-FTP) handelt, nutzt du als **Port** deinen SSH-Port, welcher standardmäßig, insofern du ihn nicht geändert hast, `22` ist.

![Hier siehst du ein Verbindungsbeispiel aus WinSCP](../.gitbook/assets/sftp-verbinden.png)