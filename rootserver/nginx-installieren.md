# nginx auf Rootserver installieren

Fast jeder Mensch auf dieser Erde kennt das Internet (auch Web genannt), wo viele Webseiten (z.B. auch diese hier) gehostet werden. Damit so eine Website aber auch überhaupt funktionieren kann, braucht sie einen Webserver, auf dem sie drauf laufen kann. Die beiden beliebtesten sind Apache2 sowie nginx und letzteres soll auf einem Rootserver installiert werden.

Zuerst muss beim System nach Updates gesucht werden. Dies macht man bei Linux mit dem folgenden Befehl:

<pre>
// Debian
sudo apt-get update

// Ubuntu
sudo apt update

// CentOS
sudo yum update

// OpenSUSE
sudo zypper update

// Fedora
sudo dnf upgrade --refresh
</pre>

Jetzt, wo das System überprüft wurde, kann Apache2 bzw. nginx installiert werden.

## Für Apache2:
<pre>
// Debian
sudo apt install apache2

// Ubuntu
sudo apt install apache2

// CentOS
sudo yum install httpd

// OpenSUSE
sudo zypper install httpd

// Fedora
sudo dnf install httpd
</pre>

## Für nginx:
<pre>
// Debian
sudo apt install nginx

// Ubuntu
sudo apt install nginx

// CentOS
sudo yum install nginx

// OpenSUSE
sudo zypper install nginx

// Fedora
sudo dnf install nginx
</pre>

Nachdem der Webserver installiert wurde, können die Website-Dateien hochgeladen werden. Dafür musst du dich über einen FTP-Client (z.B. FileZilla) mit deinem Webserver verbinden und im Verzeichnis <code>/var/www/html/</code> hochladen.

Bei nginx muss man die Dateien in ein anderes Verzeichnis <code>/usr/share/nginx/html</code> hochladen.

Wenn die Installation erfolgreich abgeschlossen wurde, sollte noch die Version überprüft werden. Dies geht ganz einfach mit den Befehlen <code>apache2 -v</code> oder <code>nginx -v</code>. Die folgende Ausgabe sollte erscheinen:

## Bei Apache2
<pre>
apache2 -v
Server version: Apache/2.4.41 (Ubuntu)
Server built:   XXXX-XX-XXTXX:XX:XX
</pre>

## Bei nginx
<pre>
nginx -V
nginx version: nginx/1.2.3
...
</pre>

Sollte dir diese Meldung angezeigt werden, so ist der Webserver erfolgreich installiert worden.
