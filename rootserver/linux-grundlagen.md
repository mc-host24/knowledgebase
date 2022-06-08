# Linux Grundlagen

## Die wichtigsten Befehle

(**l**ist) gibt unter Linux den Inhalt der Verzeichnisse

```bash
ls
```

(**c**hange **d**irectory) Wechsel der Verzeichnisse

```bash
cd
```

(**dir**ectory) Verzeichnisse auflisten

```bash
dir
```

(**r**e**m**ove) Dateien löschen

```bash
rm
```

Passwort ändern

```bash
passwd
```

(**s**ubstitute **u**ser) Benutzer wechseln

```bash
su
```

Fenster leeren

```bash
clear
```

Dateisystem und Speicherplatz anzeigen lassen

```bash
df
```

Wo bin ich?

```bash
pwd
```

Wer bin ich?

```bash
who
```

Eine Textdatei anzeigen oder erstellen

```bash
cat
```

Benutzer hinzufügen

```bash
adduser
```

## Dateirechte

Chmod

* Syntax: chmod XYZ datei

X: Besitzerrechte

Y: Gruppenrechte

Z: Rechte für andere Benutzer

|                                |   |
| ------------------------------ | - |
| Lesen, schreiben und ausführen | 7 |
| Lesen und Schreiben            | 6 |
| Lesen und ausführen            | 5 |
| Nur lesen                      | 4 |
| Schreiben und ausführen        | 3 |
| Nur schreiben                  | 2 |
| Nur ausführen                  | 1 |

## Nützliche Tools

* Nano Mit dem Prozessmanager "htop" kann man die laufenden Prozesse sowie die freien/belegten Systemressourecen anschauen. Installiert wird htop mit dem Command

```bash
apt install htop -y
```

![](../.gitbook/assets/HTOP.png)
