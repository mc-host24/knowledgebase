# nginx Reverse Proxy

Zuhause und in vielen KMUs dürfte die Situation wohl ähnlich sein: Man besitzt einen Internetanschluss mit einer festen oder einer dynamischen IP, der per DynDNS-Dienst über einen Domainnamen erreichbar ist. Durch Portforwarding im Router kann man einzelne Geräte (z.B. Webserver) ins öffentliche Netz bringen, jeden Port jedoch nur einmal benutzen. Man müsste also für zwei Webserver zwei unterschiedliche Ports verwenden und diese beim Aufruf auch so mit angeben. Durch einen Reverse-Proxy kann man jedoch kurze sprechende Adressen verwenden, um die verschiedene Server im internen Netz per Subdomain erreichbar zu machen. In etwa so:

blog.beispielseite.de -> 192.168.236.12 (WordPress auf Server 1)
wiki.beispielseite.de -> 192.168.236.23 (Mediawiki auf Server 2)
Beide Server sind über den Standard-Port 80, bzw. 443 erreichbar sein und können durch die aufgerufene Adresse (Subdomain) blog.beispielseite.de, bzw. wiki.beispielseite.de unterschieden werden.

## Voraussetzungen

Auf das Thema DynDNS möchte ich an dieser Stelle nicht weiter eingehen. Es gibt unsagbar viele Dienste und Möglichkeiten, das umzusetzen. Damit das Konzept so aufgeht, sollte man möglichst einen Domain-Anbieter nutzen, der einen eigenen DynDNS-Dienst bereitstellt. Ich setze nachfolgend voraus, dass die zu verwendenen Subdomains, in meinem Fall blog.indibit.de und wiki.indibit.de, zuverlässig auf den Internetanschluss zeigen, hinter dem sich die Server befinden.

Weiterhin setze ich voraus, dass es bereits ein Linux-System gibt, auf dem wir gleich Nginx als Reverse-Proxy installieren.

Und ich setze voraus, dass das Portforwarding grundsätzlich klappt, ihr wisst, was das ist und wie ihr das in eurem Router einrichtet. Könnt ihr auch gleich machen – die Ports 80 und 443 auf den Linux-Server weiterleiten, auf dem wir Nginx installieren und der damit zum Reverse-Proxy wird.

Für einen Test wäre es sinnvoll, wenn die Server, die sich hinter dem Reverse-Proxy befinden, schon funktionsfähig wären und deren Webseiten im lokalen Netzwerk erreichbar sind.

# Nginx installieren

Als Grundsystem benutze ich eine Virtuelle Maschine mit Ubuntu 20.04 LTS, die eine feste IP (192.168.236.3) im internen Netz zugeordnet bekommen hat. Auf der Kommandozeile setzen wir folgende Befehle ab:

System auf den aktuellen Stand bringen:

<pre>
$ sudo apt update
$ sudo apt upgrade
</pre>

Nginx installieren:
<pre>
$ sudo apt install nginx nginx-extras
</pre>

Nach Abschluss der Installation sollte der Webserver nun online sein, was sich einfach überprüfen lässt, indem man die IP-Adresse in den Browser eintippt. Es zeigt sich die Standardseite von Nginx:

Reverse-Proxy konfigurieren

Wir befinden uns wieder auf der Kommandozeile. Nginx soll in unserem fall nicht als Webserver fungieren, sondern als Reverse-Proxy, daher schalten wir die Standardseite ab…

<pre>
$ sudo unlink /etc/nginx/sites-enabled/default
</pre>

… und erzeugen eine neue Konfiguration

<pre>
$ cd /etc/nginx/sites-available
$ sudo nano reverse-proxy.conf
</pre>

Hier definieren wir die beiden Server in sogenannten Server-Blocks und sagen Nginx, was er machen soll.

<pre>
server {
        server_name blog.indibit.de;
        location / {
                proxy_pass      http://192.168.236.12;
        }
}
server {
        server_name wiki.indibit.de;
        location / {
                proxy_pass      http://192.168.236.23;
        }
}
</pre>

Wir verlassen den Editor und speichern die Änderungen. Anschließend aktivieren wir die Konfiguration,…

<pre>
$ sudo ln -s /etc/nginx/sites-available/reverse-proxy.conf /etc/nginx/sites-enabled/reverse-proxy.conf
</pre>

…schauen, ob sie ok ist…

<pre>
$ sudo nginx -t
</pre>

…und wenn dem so ist, schalten wir den Reverse-Proxy scharf:

<pre>
$ sudo nginx -s reload
</pre>

Es passiert nun folgendes:

Der Besucher gibt in seinem Browser eine der beiden Adressen (blog.beispielseite.de oder wiki.beispielseite.de) ein. Über den DNS-Server seines Internetanbieters und den DynDNS-Eintrag bei meinem Domainanbieter landet diese Anfrage nun an meinem Internetanschluss. Mein Router leitet diese Anfrage (Port 80, da Webbrowser) an den Reverse-Proxy weiter. Der Reverse-Proxy wertet nun aus, welche Adresse der Besucher im Browser eingegeben hat und leitet diese Anfrage an den entsprechenden internen Server weiter. Hat der Besucher also wiki.indibit.de eingegeben, so wird die Anfrage an 192.168.236.23 weitergeleitet. Hat er hingegen blog.indibit.de eingegeben, wird die Anfrage an 192.168.236.12 weitergeleitet.

Im Prinzip war es das schon. Wenn man keinen Fehler gemacht hat, funktioniert das System sofort.
