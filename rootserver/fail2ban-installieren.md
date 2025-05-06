Hier ein Kleines tutorial wie man fail2ban installiert.


Um die erste frage gleich zu beantworten was eigentlich ist genau fail2ban?


Fail2Ban ist ein Open-Source-Tool, das entwickelt wurde, 
um automatisierte Angriffe auf Computer zu bekämpfen. 
Es überwacht Logdateien auf verdächtige Aktivitäten, wie z.B. Brute-Force-Angriffe auf SSH oder Webserver. 
Wenn es eine vordefinierte Anzahl von fehlgeschlagenen Anmeldeversuchen innerhalb kurzer Zeit erkennt, 
sperrt Fail2Ban automatisch die IP-Adresse des Angreifers für eine Weile, um weitere Angriffsversuche zu verhindern. 
Es ist eine praktische Maßnahme, um die Sicherheit von Systemen zu erhöhen.



* Paketlisten aktualisieren

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

* Fail2Ban bei Systemstart automatisch starten:
```bash
sudo systemctl enable fail2ban
```

* Die Konfigurationsdateien von Fail2Ban sind im Verzeichnis /etc/fail2ban zu finden. Die Standardkonfiguration ist in der Datei jail.conf festgelegt.
```bash
cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```

```bash
nano /etc/fail2ban/jail.local
```

* Sperrzeit erhöhen für fehlgeschlagene Login versuche 

* Die dauer ist hierbei in sekunden angegeben 600 sekunden = 10 Minuten

```bash
bantime  = 600
```


* Nun könnt ihr die datei Speichern und fail2ban neustarten

```bash
systemctl restart fail2ban
```

* Fail2Ban protokolliert Aktionen und Maßnahmen in /var/log/fail2ban.log. Den Log anzusehen

```bash
cat /var/log/fail2ban.log
```
