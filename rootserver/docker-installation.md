# Docker Installation

* Aktualisiere die Paketlisten & installiere die Updates.
```bash
apt update && apt upgrade -y
```

Achte auf dein Betriebssystem.
Solltest du nicht wissen, welches Betriebssystem du verwendest, kannst du dies mit dem Befehl
```bash
cat /etc/issue
```
nachschauen.

{% tabs %}
{% tab title="Debian" %}
* Benötigte Pakete für die Installation von Docker

```bash
apt install ca-certificates curl gnupg lsb-release -y
```

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```bash
apt update
```

```bash
apt install docker-ce docker-ce-cli containerd.io -y
```

{% endtab %}

{% tab title="Ubuntu" %}
* Benötigte Pakete für die Installation von Docker

```bash
sudo apt install ca-certificates curl gnupg lsb-release -y
```

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

{% endtab %}
{% endtabs %}

```bash
sudo apt update
```

```bash
sudo apt install docker-ce docker-ce-cli containerd.io -y
```

* Aktiviere den Docker Dienst
```bash
sudo systemctl start docker --now
```

* Füge deinen Benutzernamen zur Docker-Gruppe hinzu.
```bash
sudo usermod -aG docker $USER
```

# Docker Compose installieren

* Installiere Docker Compose Binärdatei Herunter
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

* Erteile die Berechtigung für die Compose Binärdatei
```bash
sudo chmod +x /usr/local/bin/docker-compose
```
