# Docker-Container mit Traefik Reverse Proxy

Traefik ist ein moderner HTTP-Proxy und Load Balancer, der die Bereitstellung von Microservices vereinfacht.

Traefik integriert sich in Ihre bestehenden Infrastrukturkomponenten (Docker, Swarm-Modus, Kubernetes, Marathon, Consul, Etcd, Rancher, Amazon ECS, ...) und konfiguriert sich automatisch und dynamisch.

Wenn man Traefik auf Ihren Orchestrator richtet, sollte dies der einzige Konfigurationsschritt sein, den man dafür benötigt.

## Traefik v2 - Nutzungs-Beispiele

Den Docker-Provider und die Webbasierte Benutzeroberfläche öffnen:

<pre>
## traefik.yml

# Docker configuration backend
providers:
  docker:
    defaultRule: "Host(`{{ trimPrefix `/` .Name }}.docker.localhost`)"

# API and dashboard configuration
api:
  insecure: true
</pre>

Traefik starten:

<pre>
docker run -d -p 8080:8080 -p 80:80 \
-v $PWD/traefik.yml:/etc/traefik/traefik.yml \
-v /var/run/docker.sock:/var/run/docker.sock \
traefik:v2.5
</pre>

Einen Backend-Server namens test starten:

<pre>
docker run -d --name test traefik/whoami
</pre>

Zum Schluss lässt sich dann der <code>whoami</code>-Server mit Traefik auf dem Domainnamen test.docker.localhost erreichen:

<pre>
# $ curl --header 'Host:test.docker.localhost' 'http://localhost:80/'
$ curl test.docker.localhost
Hostname: 390a880bdfab
IP: 127.0.0.1
IP: 172.17.0.3
GET / HTTP/1.1
Host: test.docker.localhost
User-Agent: curl/7.65.3
Accept: */*
Accept-Encoding: gzip
X-Forwarded-For: 172.17.0.1
X-Forwarded-Host: test.docker.localhost
X-Forwarded-Port: 80
X-Forwarded-Proto: http
X-Forwarded-Server: 7e073cb54211
X-Real-Ip: 172.17.0.1
</pre>

Die Benutzeroberfläche im Web auf http://localhost:8080 wird dir eine Übersicht von allen Routern, Services und middlewares geben.
