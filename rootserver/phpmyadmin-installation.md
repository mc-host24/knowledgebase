# PhpMyAdmin Installation

* Aktualisiere die Paketlisten & installiere die Updates.

```bash
apt update && apt upgrade -y
```

* Installiere für die weitere Installation benötigte Pakete.

```bash
apt install ca-certificates nano lsb-release gnupg apt-transport-https curl unzip -y
```

Wähle dein Betriebssystem aus.
Falls du nicht weißt welches Betriebssystem du verwendest kannst du dies mit dem Befehl 
```bash
cat /etc/issue
```
{% tabs %}
{% tab title="Debian" %}
* Für die PHP 7.4 Installation benötigt man eine Paketquelle. Diese füge mit diesen Befehlen hinzu

```bash
curl -fsSL https://packages.sury.org/php/apt.gpg -o /usr/share/keyrings/php-archive-keyring.gpg
```

```bash
echo "deb [signed-by=/usr/share/keyrings/php-archive-keyring.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
```
{% endtab %}

{% tab title="Ubuntu" %}
* Für die PHP 7.4 Installation benötigt man eine Paketquelle. Diese füge mit diesen Befehlen hinzu

```bash
apt install software-properties-common -y
```

```bash
add-apt-repository ppa:ondrej/php
```
{% endtab %}
{% endtabs %}
