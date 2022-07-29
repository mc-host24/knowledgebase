# Eine Domain zu MC-Host24 transferieren

Als Domaintransfer wird die Verlagerung einer DNS-Domain zu einem neuen Registrar bezeichnet. Eine Motivation für den Domain-Transfer ist z.B. die Unzufriedenheit bei einem Anbieter oder zu teure Preise. In der Regel wird nach Firmenübernahmen bzw. Fusionen der DNS durch Transfer aller Domains zu einem einzigen Registrar konsolidiert.

Im November 2004 hat ICANN Regeln für den Domaintransfer aufgestellt, die für alle Registrare verbindlich sind und die den Prozess vereinfachen und sicherer gestalten sollen. Ein Domaintransfer ändert nichts an den Besitzverhältnissen der betroffenen Domain. Letztendlich wird lediglich der Eintrag in der Registry-Datenbank geändert, der definiert, welcher Registrar für diese Domain und deren Inhaber zuständig ist.

## Der Ablauf

Ausgangspunkt ist immer der Endkunde, also der Domain-Inhaber. Sein erster Ansprechpartner wird der zukünftige Registrar sein, der sich dann über die zuständige Registry mit dem aktuellen Registrar in Verbindung setzt:

1. Der Registrant (Endkunde) autorisiert und legitimiert sich gegenüber dem zukünftigen Registrar.
2. Der Registrant beantragt beim aktuellen Registrar den Transfer für die zu verlagernde Domain.
3. Der zukünftige Registrar leitet den Antrag an die übergeordnete Registry weiter (ggf. nach zusätzlicher Rückbestätigung durch den Domaininhaber).
4. Die Registry kontaktiert den aktuellen Registrar und fordert ihn zur Zustimmung oder Ablehnung auf (erfolgt innerhalb von fünf Tagen keine Antwort, gilt das als Zustimmung).
5. Der aktuelle Registrar sendet eine E-Mail an die administrative Kontaktperson der Kunden.
6. Die administrative Kontaktperson bestätigt den Transfer (bleibt die Bestätigung aus, gilt das als Ablehnung).
7. Der aktuelle Registrar leitet die Bestätigung oder Ablehnung an die übergeordnete Registry weiter.
8. Die Registry führt den Transfer durch Änderung in ihrer Datenbank durch.

Wird der Transfer als Dienstleistung über einen Dritten (z. B. einen Hosting-Provider) abgewickelt, kann dieser als Mittler zwischen Registrant und Registrar wirken und dabei einzelne oder alle Interaktionen mit den beteiligten Registraren im Auftrag abwickeln. Der Registrant muss ihm lediglich die Unterlagen zur Legitimation und Autorisierung überlassen.

In der Praxis läuft dieser Prozess gewöhnlich vollautomatisch ab. Die einzigen manuellen Vorgänge sind die Formulierung des Transfer-Antrags (Schritt 2) und die Bestätigung (Schritt 6) durch den Endkunden. Die Kommunikation zwischen Registrar und übergeordnetem Registrar erfolgt meist per Extensible Provisioning Protocol.

Es gibt in einigen Fällen zusätzliche Sicherungsmaßnahmen, mit denen ein unautorisierter Domain-Transfer verhindert werden soll. Bei einigen Domains (z. B. .de, .com, .net, .org, .info, .biz, .cn, .us, .la, .pl, .ch, .name) ist die Angabe eines so genannten Autorisierungscodes (engl.: authorisation code) zur Einleitung eines Domain-Transfers erforderlich. Diese 6 bis 16 Zeichen umfassende Sequenz erhält man auf Anforderung vom aktuellen Registrar. Einige Domains (z. B. .com, .net) können sich im Status Registrar-Lock befinden. Bevor irgendwelche Änderungen möglich sind, muss der Domaininhaber den aktuellen Registrar veranlassen, den Status auf Active zu setzen.

## Konflikte

Der in der Theorie klar und einfach scheinende Transferprozess kann sich in der Praxis zu einem administrativen Albtraum entwickeln. Hauptgrund hierfür sind veraltete Informationen in der Domain-Datenbank. Hat etwa die administrative Kontaktperson die Firma des Domaininhabers bereits verlassen, ist eine Zustimmung zum Transfer (Schritt 6) nicht ohne weiteres möglich.

Ein weiteres potentielles Problem stellen falsch oder unzureichend positionierte Nameserver dar. Der aktuelle Registrar könnte beispielsweise akzeptiert haben, dass für eine Domain entgegen den Internetregeln nur ein einziger Nameserver existiert, der zukünftige verlangt aber mindestens zwei Nameserver und lehnt den Transfer daher ab.

Da ein Registrar an einer über ihn registrierten Domain zumeist nur wenig verdient (oftmals nur wenige Cent bis Euro pro Jahr), ist seine Bereitschaft, Konfliktfälle durch aufwändiges manuelles Nachbessern zu lösen, geschäftsmäßig gering. Das gilt besonders für den aktuellen Registrar, der ja einen zahlenden Kunden verliert.
