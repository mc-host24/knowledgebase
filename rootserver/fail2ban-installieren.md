# fail2ban installieren

## Was ist fail2ban?

Fail2Ban ist ein Open-Source-Tool, das entwickelt wurde, um automatisierte Angriffe auf Server zu bekämpfen. 
Es überwacht Logdateien auf verdächtige Aktivitäten, wie z.B. Brute-Force-Angriffe auf SSH, FTP oder einen Webserver. 
Wenn es eine vordefinierte Anzahl von fehlgeschlagenen Anmeldeversuchen innerhalb kurzer Zeit erkennt, 
sperrt Fail2Ban automatisch die IP-Adresse des Angreifers für eine Weile, um weitere Angriffsversuche zu verhindern. 
Es ist eine praktische Maßnahme, um die Sicherheit von Systemen zu erhöhen.

{% hint style="warning" %}
**Wenn du Plesk auf deinem Rootserver nutzt, solltest du fail2ban über das Plesk Panel installieren.**
{% endhint %}

## Installation

* Paketlisten aktualisieren:

```bash
sudo apt update
```

* Fail2ban installieren:

```bash
apt install fail2ban
```

* Fail2Ban starten:

```bash
systemctl start fail2ban
```

* Auto-Start von Fail2Ban bei Systemstart aktivieren:

```bash
sudo systemctl enable fail2ban
```

## Konfiguration

 Die Konfigurationsdateien von Fail2Ban sind im Verzeichnis /etc/fail2ban zu finden. Die Standardkonfiguration ist in der Datei jail.conf festgelegt.
 Wenn du Änderungen an der Konfiguration vornehmen willst, kopiere die Standardkonfiguration mit dem folgenden Befehl:

```bash
cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```
Du kannst dann die Konfiguration mit folgendem Befehl bearbeiten:

```bash
nano /etc/fail2ban/jail.local
```

### Sperrzeit erhöhen für fehlgeschlagene Loginversuche 
Die Dauer ist hierbei in Sekunden angegeben. 10 Minuten entsprechen beispielsweise 600 Sekunden

```bash
bantime  = 600
```


Nun könnt ihr die Datei speichern und fail2ban mit diesem Befehl neustarten:

```bash
systemctl restart fail2ban
```

Fail2Ban protokolliert Aktionen und Maßnahmen in /var/log/fail2ban.log
Um den Log anzusehen, führe folgenden Befehl aus:

```bash
cat /var/log/fail2ban.log
```
