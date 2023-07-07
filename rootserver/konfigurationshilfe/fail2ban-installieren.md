# SSH mittels Fail2Ban absichern

Die Absicherung des SSH-Servers unter Linux ist von entscheidender Bedeutung, um potenzielle Sicherheitslücken zu schließen. Eine bewährte Methode zur Verbesserung der Sicherheit besteht darin, Fail2Ban zu verwenden, eine Software, die automatisch schädliche oder verdächtige Verbindungen blockiert.

Hier sind die Schritte zur Einrichtung von Fail2Ban, um den SSH-Server abzusichern:

1. Fail2Ban installieren:
    1. Öffne das Terminal auf deinem Linux-System.
    2. Führe den Befehl ```sudo apt-get install fail2ban``` aus, um Fail2Ban zu installieren.
    3. Warte, bis die Installation abgeschlossen ist.
2. Konfigurationsdatei anpassen:
    1. Navigiere zum Verzeichnis ```/etc/fail2ban/```.
    2. Öffne die Datei ```jail.conf``` oder ```jail.local``` (falls vorhanden) mit einem Texteditor.
    3. Suche nach der Sektion ```[sshd]``` und passe die Einstellungen an deine Bedürfnisse an und fügen Sie in diesem Bereich ```enabled=true``` hinzu um Fail2Ban zu aktivieren. Du kannst beispielsweise die maximale Anzahl von Versuchen ```maxretry``` und die Sperrzeit ```bantime``` festlegen.
    4. Speichere die Änderungen und schließe die Datei.
3. Fail2Ban-Dienst neu starten:
    1. Führe den Befehl ```sudo service fail2ban restart``` aus, um den Fail2Ban-Dienst neu zu starten.
    2. Überprüfe, ob der Dienst erfolgreich gestartet wurde, indem du den Status mit dem Befehl ```sudo service fail2ban status``` überprüfst.

Die Verwendung von Fail2Ban in Verbindung mit einer angemessenen Konfiguration bietet einen zusätzlichen Schutz vor Brute-Force-Angriffen und anderen bösartigen Aktivitäten auf deinem SSH-Server.