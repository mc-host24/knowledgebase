# Cronjobs (zeitgesteuerte Aufgaben)

Cronjobs sind eine Funktion auf Linux-Systemen, die es ermöglicht, Aufgaben zu automatisieren und zu einem bestimmten Zeitpunkt oder in regelmäßigen Abständen auszuführen. Sie sind besonders nützlich für Kunden, die nicht mit Rootservern vertraut sind, da sie die Möglichkeit bieten, wiederkehrende Aufgaben ohne manuelle Eingriffe durchzuführen.

## Crontab

Die zeitgesteuerten Aufgaben werden in der "Crontab" Tabelle verwaltet. Diese Tabelle enthält eine Liste der geplanten Cronjobs. Dabei werden zuerst die Minuten (0 bis 59), dann die Stunden (0 bis 23), der Tag (1 bis 31), der Monat (1 bis 12), der Wochentag (1 bis 7) und schließlich der auszuführende Befehl definiert.

Ein einfaches Beispiel für einen Cronjob-Eintrag in der Crontab könnte wie folgt aussehen:

<details>

<summary>Cronjob Beispiel</summary>

```
0 10 * * * Befehl
```

Dieser Eintrag besagt, dass der Befehl "Befehl" jeden Tag um 10:00 Uhr ausgeführt werden soll. Die einzelnen Felder können auch durch ein Sternchen (*) oder durch spezifische Werte ersetzt.
</details>

## Spezifische Werte

- Ein Sternchen (*) gibt an, dass der Cronjob zu jeder beliebigen Zeit für das entsprechende Feld ausgeführt werden soll.
- Eine spezifische Zahl oder Zahlenbereich kann angegeben werden. Zum Beispiel bedeutet "5,10,15" für das Feld der Minuten, dass der Cronjob zu den Minuten 5, 10 und 15 ausgeführt wird.
- Der Bindestrich (-) wird verwendet, um einen Bereich anzugeben. Zum Beispiel bedeutet "1-5" für das Feld der Stunden, dass der Cronjob von Stunde 1 bis Stunde 5 ausgeführt wird.
- Der Schrägstrich (/) wird verwendet, um Intervalle anzugeben. Zum Beispiel bedeutet "*/15" für das Feld der Minuten, dass der Cronjob alle 15 Minuten ausgeführt wird.

Darüber hinaus gibt es noch einige spezielle Optionen für Cronjobs:

- @reboot ermöglicht die Ausführung eines Cronjobs beim Systemstart.
- @yearly, @monthly, @weekly und @daily sind vordefinierte Zeitintervalle, die entsprechend einmal pro Jahr, Monat, Woche oder Tag ausgeführt werden.