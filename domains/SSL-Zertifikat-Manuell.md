***

# SSL-Zertifikat mit einer Mc-Host24-Domain erstellen

Diese Anleitung zeigt, wie du mit Certbot ein kostenloses SSL-Zertifikat von Let’s Encrypt für deine Mc-Host24-Domain erstellen kannst.

***

## Schritt 1 – Certbot installieren

```bash
sudo apt install certbot
```

> 💡 **Tipp:** Stelle sicher, dass dein Server auf Ubuntu oder Debian läuft und du Root- bzw. Sudo-Rechte hast.

***

## Schritt 2 – Zertifikat anfordern

```bash
certbot certonly --manual --preferred-challenges=dns \
--email your@mail.com \
--server https://acme-v02.api.letsencrypt.org/directory \
-d your.domain.de
```

> ℹ️ **Hinweis:**  
> - Du kannst bis zu 100 Subdomains in einem Zertifikat kombinieren.  
> - Wildcard-Zertifikate wie `*.domain.de` sind ebenfalls möglich.

***

## Schritt 3 – DNS-TXT-Eintrag bei Mc-Host24 erstellen

Nach Ausführung des Befehls zeigt Certbot eine Aufforderung wie diese:

```
Please deploy a DNS TXT record under the name:
_acme-challenge.deinedomain.de.

with the following value:
APAJAljI6NFSW0LDEINKEYRJ3Df:3DOvK38rLUwU2EY
```

Füge diesen TXT-Eintrag in den DNS-Einstellungen deiner Domain im Mc-Host24-Webinterface hinzu.


![](https://docs.mc-host24.de/docs/~gitbook/image?url=https%3A%2F%2F2840415198-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252Fzy2fgGeSHlVCNElBvc37%252Fuploads%252Fgit-blob-74b13c3c80fbf534f451d878cc0199237ce8e389%252Fwebspace-dns-eintraege.png%3Falt%3Dmedia&width=768&dpr=1&quality=100&sign=72fa4209&sv=2)


> ⚠️ **Wichtig:**  
> Trage den TXT-Eintrag exakt so ein, wie er in der Anweisung steht.  
> Bereits kleine Abweichungen führen dazu, dass die Validierung fehlschlägt.

***

## Schritt 4 – DNS-Eintrag überprüfen

Bevor du Enter drückst, prüfe, ob der Eintrag aktiv ist.  
Das kannst du mit der Google Admin Toolbox tun:

[https://toolbox.googleapps.com/apps/dig/#TXT/_acme-challenge.deinedomain.de](https://toolbox.googleapps.com/apps/dig/#TXT/_acme-challenge.deinedomain.de)

Wenn der Eintrag korrekt ist, erscheint unter dem Abschnitt „;ANSWER“ der eingetragene Textwert.

> 🕐 **Tipp:**  
> Es kann einige Minuten dauern, bis der DNS-Eintrag überall aktiv ist.

***

## Schritt 5 – Zertifikat erfolgreich erstellen

Wenn der DNS-Eintrag erkannt wurde, drücke Enter.  
Bei Erfolg erscheint eine Ausgabe wie diese:

```
Successfully received certificate.
Certificate is saved at: /etc/letsencrypt/live/deinedomain.de/fullchain.pem
Key is saved at:         /etc/letsencrypt/live/deinedomain.de/privkey.pem
This certificate expires on 2026-01-27.
```

> 📁 **Zertifikatspfade:**  
> - Zertifikat: `/etc/letsencrypt/live/deinedomain.de/fullchain.pem`  
> - Schlüssel: `/etc/letsencrypt/live/deinedomain.de/privkey.pem`

***

## Schritt 6 – Zertifikate erneuern

Let's Encrypt-Zertifikate sind etwa 90 Tage gültig.  
Vor Ablauf kannst du das Zertifikat mit demselben Befehl erneuern:

```bash
certbot certonly --manual --preferred-challenges=dns \
--email your@mail.com \
--server https://acme-v02.api.letsencrypt.org/directory \
-d your.domain.de
```



