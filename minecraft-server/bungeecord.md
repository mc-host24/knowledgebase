# Ein BungeeCord-Servernetzwerk einrichten

Manche Minecrafft-Spieler hätten gerne ein Netzwerk oder haben bereits bestehende Server, aber keine Lust, immer manuell zwischen diesen zu wechseln? Dafür gibt es die kostenlose Minecraft Proxy Server Software BungeeCord und seinen Fork Waterfall. Auch gibt es noch eine Proxy Server Software, die Velocity heißt. Allerdings ist dort die Konfiguration ein bisschen anders wie bei BungeeCord oder Waterfall.

## 1. BungeeCord, Waterfall oder Velocity einrichten und passend konfigurieren

Um ein BungeeCord, Waterfall oder Velocity Netzwerk einzurichten, muss man sich als allererstes hier [BungeeCord](https://ci.md-5.net/job/BungeeCord), [Waterfall](https://papermc.io/downloads#Waterfall) oder [Velocity](https://papermc.io/downloads#Velocity) kostenlos herunterladen und mindestens zwei Server besitzen. Ansonsten lohnt sich kein BungeeCord, Velocity oder Waterfall Netzwerk. Nachdem das passiert ist, muss die [JAR-Datei geändert werden](minecraft-server/eigene-server-jar.md). Ist dies erledigt, so muss der Server einmal neugestartet werden. In diesem Beispiel haben wir drei Minecraft-Server, welche nun durch einen BungeeCord-Proxyserver verbunden werden sollen. Auch diese Proxy Softwares gehören zu denen, die beim erstmaligen Start eine sogenannte Konfigurationsdatei mit dem Namen "config.yml" generieren. So eine Konfigurationsdatei kann z.B. [hier](https://github.com/itzg/docker-bungeecord/blob/master/docs/config.yml) gefunden werden. [Dieser Artikel](https://www.spigotmc.org/wiki/bungeecord-configuration-guide/) erklärt alle wichtigen und nützlichen Funktionen sowie jede einzelne Zeile der <b>config.yml</b>. Um unsere drei Server aus dem obigen Beispiel einzutragen, muss nun in der Konfigurationsdatei bei "servers:" folgendes eingetragen werden

<p>
  servers:
    beispiel1:
      motd: ERSTES BEISPIEL
      address: beispiel1.de:11111
      restricted: true
     beispiel2:
      motd: ZWEITES BEISPIEL
      address: beispiel2.de:22222
      restricted: false
     beispiel3:
      motd: DRITTES BEISPIEL
      address: beispiel3.de:33333
      restricted: false
</p>

<b>MOTD</b> ist der Text, der dem Spieler in der Serverliste angezeigt wird. <b>ADDRESS</b> ist die IP-Adresse, mit der man sich mit dem Server verbinden wird. Ports werden hier auch unterstützt und <b>RESTRICTED</b> ist dafür da, um das Netzwerk z.B. nur auf Freunde zu beschränken. Falls dieser Wert auf true ist, können nur die Spieler beitreten, denen man zuvor z.B. mit [LuckPerms](https://luckperms.net) die Berechtigung <code>bungeecord.server.name</code> gegeben hat. Hierbei muss "name" durch den Servernamen, den man zuvor in der Konfigurationsdatei eingetragen hat, ersetzen.

## 2. Plugins installieren

Bei BungeeCord, Waterfall und Velocity installiert man Plugins auf die gleiche Art und Weise wie bei einem ganz normalen PaperMC Server entweder per Drag & Drop oder per Spiget Api.

## 3. Das Netzwerk betreten und zwischen den Servern wechseln

Nachdem alles richtig konfiguriert wurde, betritt man nun das Netzwerk, in dem man hinten an die IP-Adresse :25577 dranhängt. Jetzt dauert es einige Sekunden, bis man das Netzwerk betreten hat. Um nun zwischen den Servern zu wechseln, muss man zuerst die hinzugefügten Server aus der Konfigurationsdatei reinschauen. Danach muss man ingame im Chat den Befehl /server  NAME eingeben. Falls man nun alles richtig gemacht hat, kann man ab sofort nun auf seinem eigenen BungeeCord Netzwerk spielen. Viel Spaß dabei!
