2. Programmieraufgabe

Programmierparadigmen
LVA-Nr. 194.023
2025/2026 W
TU Wien

Kontext
Die Simulation aus der ersten Programmieraufgabe ist viel zu oberflächlich. Hauptsächlich geht es darum, Simulationen besser an die Realität
in der Natur anzupassen und zuverlässigere Ergebnisse zu erzielen, ohne
den Aufwand unnötig in die Höhe zu treiben. Verbesserungen sollen vor
allem in folgende Richtungen gehen:
• Das Umfeld genauer betrachten und alle als wesentlich erachteten
Faktoren in die Simulation einbeziehen (Modell vervollständigen).
• Beziehungen zwischen den Elementen des Modells genauer analysieren und darstellen (Modell verfeinern).
• Simulationsergebnisse mit in der Natur ermittelten Werten in Einklang bringen (Rückkopplung und Justierung von Parametern).

Themen:
Aufwandsabschätzung,
Programmiereffizienz,
Überblick über
prozedurale und
objektorientierte
Programmierung

Ausgabe:
20. 10. 2025

Abgabe (Deadline):

Welche Aufgabe zu lösen ist

27. 10. 2025, 13:00 Uhr

Simulation verbessern. Die Lösung der 1. Aufgabe ist deutlich zu verbessern. In jede der drei unter „Kontext“ genannten Richtungen sind
Verbesserungen nötig. Es ist nicht vorgegeben, wie diese Verbesserungen
genau ausschauen sollen. Die folgenden drei Absätze weisen auf Verbesserungspotentiale hin, schreiben aber nicht vor, was genau zu tun ist.

Abgabeverzeichnis:

Modell vervollständigen. Das Modell könnte so vervollständigt werden:

Programmaufruf:

• Es gibt sehr viele Arten von Wildbienen, teilweise auf ganz bestimmte Blütenpflanzen spezialisiert, mit unterschiedlichen Anforderungen an Nistplätze und in unterschiedlichen Zeiträumen aktiv.
Das Modell soll zwischen diesen Arten unterscheiden und auf ihre
Lebensbedingungen Rücksicht nehmen.
• Wildbienen reagieren empfindlich auf Entfernungen zwischen Nistund Nahrungsressourcen. Es reicht also nicht, irgendeinen Teil einer großen landwirtschaftlichen Fläche für Blütenpflanzen vorzusehen, sondern es müssen kleinräumige Strukturen gebildet werden,
in denen Bereiche mit blühenden Pflanzen nicht weit entfernt sind.
Entfernungen zwischen Nistplätzen und Nahrungsquellen sollen in
die Simulation einbezogen werden.
• Wildbienen reagieren empfindlich auf Störungen und Veränderungen der Umweltbedingungen. Es wird kaum möglich sein, Umweltbedingungen über so lange Zeiträume, die simuliert werden sollen,
konstant zu halten. Daher sollen Veränderungen von Umweltbedingungen in die Simulation einbezogen werden. Das betrifft beispielsweise auch Feldfruchtfolgen (zur Bodenschonung in aufeinander folgenden Jahren unterschiedliche Kulturpflanzen), die als Störungen
betrachtet werden können.
1

Aufgabe1-3

java Test

Grundlage:
Skriptum,
Abschnitt 2.1 und 2.2

• Wildbienen sind nicht die einzigen Bestäuber von Blütenpflanzen.
Die Bestäubungsleistung kann teilweise von anderen Insekten, etwa
Honigbienen und Schwebfliegen übernommen werden, auch wenn
diese Bestäuber weniger effektiv sind. Vereinfacht kann man die
Anwesenheit dieser Bestäuber als gegeben annehmen, aber auch eine Simulation der Lebensgewohnheiten anderer Insekten kann sinnvoll sein. Die Anwesenheit von Honigbienen kann gezielt beeinflusst
werden, was auch in die Simulation einfließen soll.
• Andere Bestäuber sind nicht nur teilweiser Ersatz für Wildbienen,
sondern auch Nahrungskonkurrenten, die die Verfügbarkeit von Blütennektar reduzieren. Das sollte simuliert werden. Wildbienen sind
durch ihren hohen Spezialisierungsgrad sehr effektive Bestäuber, für
die Pflanzen bei gleicher Bestäubungsleistung weniger Nektar produzieren müssen als für andere Bestäuber. Es bringt einer Pflanze
daher Vorteile, von einer Wildbiene bestäubt zu werden, was zu
einer etwas besseren Wuchskraft führen kann.
• Pflanzen entwickeln sich nicht nach einem fixen Schema, wie in der
1. Aufgabe angenommen. Unterschiedliche Pflanzen haben unterschiedliche Strategien. Zumindest die Temperatur ist ein Faktor,
der bezüglich Wachstum und Blühzeitpunkt berücksichtigt werden
sollte. Manche Pflanzen blühen mehrfach und können mehrmals im
Jahr Früchte entwickeln. Auch nahe beieinander wachsende Pflanzen können ganz unterschiedlich besonnt sein, wodurch die Sonnenstunden kein besonders gut geeignetes Mittel zur Synchronisation
des Blühbeginns sind. Viele Pflanzen können sich über chemische
Substanzen koordinieren oder den Blühbeginn von der Anwesenheit von Insekten abhängig machen, genau so wie Wildbienen ihre
Aktivitäten vermutlich an das Vorhandensein von Blüten anpassen.
• In praktisch keinem Fall trifft die Annahme zu, dass die Qualität
und Menge von Samen von der Wachstumskraft am Ende der Vegetationsperiode abhängt. Samen bilden sich oft viel früher und
Pflanzen sterben danach ab oder gehen in einen anderen Modus
über, in dem sie sich auf die Ruhephase vorbereiten. Hinter der Vermehrung und Wuchskraft vergleichsweise langlebiger Blütenpflanzen wie Kirsch- oder Apfelbäumen stecken ganz andere Mechanismen als hinter einjährigen Pflanzen. In Bezug auf die Vermehrung
sollen wesentlich ausgefeiltere Mechanismen modelliert werden.
Modell verfeinern. Im Modell aus der 1. Aufgabe sind viele Zahlen fix
einkodiert, etwa die Änderung der Wildbienenpopulation abhängig vom
Nahrungsangebot. Derart fixierte Änderungen gibt es in der Natur nicht.
Wir könnten das Modell vervollständigen, indem wir etwa das Fortpflanzungsverhalten unterschiedlicher Wildbienenarten im Detail simulieren.
Aber so genaue Simulationen würden den Aufwand immens in die Höhe
treiben. Es bleibt uns nichts anderes übrig, als mit groben Annäherungen
an die Realität zu arbeiten. Wir können jedoch dafür sorgen, dass kleinste
Änderungen der Daten keine großen Auswirkungen nach sich ziehen und
genauere Ausformungen an Stellen, an denen sie sich als sinnvoll erweisen,
ermöglicht werden. Das Modell könnte z. B. so verfeinert werden:
2

• Statt mit einfachen gleichverteilten Zufallszahlen in gewissen Wertebereichen soll mit Wahrscheinlichkeitsverteilungen gearbeitet werden, die der Natur abgeschaut sind. Wertebereiche werden damit
meist größer, aber die gewählten Werte sind realistischer.
• Änderungen bestimmter Werte sollen nicht linear mit einem fixen
Faktor oder Prozentsatz erfolgen, sondern in Abhängigkeit von der
Größe, durch die die Änderung veranlasst wurde. Beispielsweise soll
sich die Wuchskraft einer Pflanze bei geringfügiger und kurzzeitiger
Überschreitung der Feuchtegrenzen nur geringfügig auswirken, bei
starker oder lang anhaltender Überschreitung dagegen stark, mit
kontinuierlichen Verläufen statt sprunghaften Änderungen.
• Unterschiedliche Wildbienenarten und Blütenpflanzen haben unterschiedliche Lebensgewohnheiten. Es soll möglich sein, das Modell
modular so zu erweitern, dass Simulationen der Lebensgewohnheiten einzelner Populationen hinzugefügt und auch wieder entfernt
werden können, ohne die Struktur des restlichen Modells anpassen zu müssen. Beispielsweise können die Lebensgewohnheiten in
Java-Klassen beschrieben sein, die ein gemeinsames Interface implementieren; Instanzen dieses Interfaces (also Objekte) können in
die Simulation eingebunden werden.
• So wie Lebensgewohnheiten von Populationen als Objekte zur Simulation hinzugefügt werden können, sollen auch Ereignisse als Objekte zur Simulation hinzugefügt werden können. Beispielsweise könnte es Klassen und entsprechende Objekte geben, die die Auswirkungen gelegentlicher Naturereignisse (Gewitter, Sturm, Hangrutschung, . . . ) oder sonstiger Störungen (Mahd, Ernte, Fruchtwechsel, . . . ) simulieren. Auch Wahrscheinlichkeitsverteilungen sollen auf
diese Weise flexibel austauschbar sein.
• Wenn wir schon dabei sind, Schnittstellen zur Erweiterung des Modells anzubieten, können wir das gesamte Modell gleich modular
aufbauen, sodass alle simulierten Populationen, Ereignisse, etc. über
Objekte eingebunden werden. Entscheidend ist dabei, eine möglichst flexible Form der Kommunikation zwischen den einzelnen Modularisierungseinheiten zu ermöglichen (also die „richtigen“ Methoden in den Interfaces vorzusehen), sodass die Struktur des Modells
der Vervollständigung und Verfeinerung nicht im Weg steht.
Modell justieren. Ohne Bezug zur Realität wären Simulationen sinnlos. In einem gut strukturierten Modell soll es möglich sein, Parameter
so anzupassen, dass Simulationsergebnisse gut zu Beobachtungen in der
Realität passen. Der Begriff „Parameter“ ist dabei in einem weiten Sinn
zu verstehen, nicht nur als Methodenparameter. Parameter können in der
Simulation verwendete elementare Werte, aber etwa auch Wahrscheinlichkeitsverteilungen sein. Wir können dafür sorgen, dass das Modell besser
justierbar wird und wir können reale Daten einbeziehen:
• In einigen Fällen kennen wir die Natur recht genau und können
daher auch mit genauen realen Daten arbeiten. Ein Beispiel ist die
Tageslänge abhängig von Standort und Jahreszeit.
3

• Wir können die Witterung nicht nur abstrakt simulieren, sondern
reale Wetterdaten vergangener Jahre als Grundlage verwenden.
• Auch ohne jahrelange Feldversuche können wir auf viele bekannte
Daten zurückgreifen. Beispielsweise sind typische Blütezeiten realer
Blütenpflanzen leicht zu eruieren und wir können überprüfen, ob
diese Pflanzen auch in der Simulation zur richtigen Zeit blühen und
die Simulation bei Bedarf anpassen.
• Alle für uns interessanten mathematischen Funktionen auf realen
Zahlen können beliebig genau durch Polynome angenähert werden.
Praktisch reichen für unsere Zwecke Polynome niedriger Potenzen.
Jedes Modell lässt sich so parametrisieren, wie wir es in der Realität
beobachten, wenn wir jede Einflussgröße als Polynom betrachten,
dessen Koeffizienten für alle niedrigen Potenzen wir beliebig einstellen können. Auf diese Weise können wir für Justierbarkeit sorgen.
• Parameter sind nicht nur reale Zahlen oder Funktionen auf realen
Zahlen. Wenn wir Objekte beliebiger Klassen (bzw. von Unterklassen bestimmter Typen) als Parameter einsetzen können, haben wir
weitere Möglichkeiten, die es erlauben, Teile des Modells beliebig
genau an die Realität anzunähern.
• Unabhängig von der eigentlichen Simulation können wir Parameter (idealerweise als Polynome betrachtet) als Korrekturwerte der
Ergebnisse vorsehen. Damit lassen sich leicht alle gewünschten Ergebnisse einstellen. Allerdings bedeutet das auch, dass wir etwas
simulieren, was sich in der Realität sicher nicht so abspielt.
• Viele Systeme und Modelle zeigen chaotisches Verhalten, wobei winzige Änderungen große Auswirkungen haben. So lange sich die Simulation ähnlich chaotisch verhält wie die Realität, ist an der Simulation nichts falsch. Aber die Simulation sollte kein chaotisches Verhalten zeigen, das in der Realität nicht beobachtbar ist. Wir können
die Simulation dahingehend analysieren, wo chaotisches Verhalten
auftritt und die Simulationsgenauigkeit dort gezielt erhöhen.
Funktionsumfang. Bestimmen Sie selbst den Funktionsumfang Ihres
Programms. Das Programm soll möglichst viel der nötigen (vorgeschlagenen oder selbst gefundenen) Funktionalität abdecken und über Testfälle
überprüfen. Jedoch sollte zumindest je eine Maßnahme getroffen werden,
um das Modell zu vervollständigen, zu verfeinern und zu justieren oder
justierbar zu machen.
Testen Das Programm soll wie in der 1. Programmieraufgabe nach neuerlicher Übersetzung mittels java Test vom Verzeichnis Aufgabe1-3 aus
aufrufbar sein und die selbst gewählte Funktionalität überprüfen. Tests
sollen ohne Benutzerinteraktion ablaufen, sodass Aufrufer keine Testfälle
auswählen oder Testdaten eintippen müssen.

4

Funktionsumfang
selbst wählen

im richtigen Verzeichnis
testen

Paradigmen und Kommentare Neben nominaler Abstraktion dürfen
Sie auch Lambda-Abstraktion einsetzen. Jedoch soll jede nominale Abstraktion mit Kommentaren versehen sein, die die Abstraktion erläutern.
Setzen Sie Programmierstile des objektorientierten und des prozeduralen Paradigmas gemischt ein. Bitte streuen Sie in Ihr Programm an mindestens 5 relevanten Stellen je einen Kommentar ein, der mit „STYLE:“
beginnt und eine Erklärung enthält, welchem Paradigma der an dieser
Stelle verwendete Programmierstil entspricht und woraus das ersichtlich
ist. Abstraktionen müssen zum Paradigma passen. Dort, wo ein objektorientierter Stil verwendet wird, achten Sie bitte darauf, dass der betreffende Programmteil ausschließlich durch Abstraktionen verständlich ist
sowie der Klassenzusammenhalt hoch und die Objektkopplung schwach
ist. Sorgen Sie dafür, dass auch Untertypbeziehungen vorkommen. An
Grenzen, an denen Stile unterschiedlicher Paradigmen aneinanderstoßen,
machen Sie bitte klar, wie die Paradigmen zusammenwirken.
Neben Programmtext soll die Datei Test.java als Kommentar am
Dateianfang die Grobstruktur und den (geplanten) Funktionsumfang der
Lösung zusammenfassen sowie eine kurze, aber verständliche Beschreibung der Aufteilung der Arbeiten auf die einzelnen Gruppenmitglieder
enthalten (wer tatsächlich was gemacht hat, nicht die geplante Aufteilung), nicht nur für die erste Aufgabe, sondern auch für diese.

nominale Abstraktion
nur mit Kommentaren
Paradigmen erläutern
(mind. 5 Stellen)

Klassenzusammenh. hoch,
Objektkopplung schwach,
Untertypbeziehungen

beschreiben: Struktur,
Funktionsumfang,
Aufgabenaufteilung

Wie die Aufgabe zu lösen ist
Die oben aufgezählten Vorschläge zur Verbesserung der Simulation sind
als Anhaltspunkte gedacht. Sie können Punkte weglassen, abändern oder
durch andere sinnvoll erscheinende Verbesserungen ersetzen.
Eine Schwierigkeit besteht in der richtigen Abschätzung des Umfangs
der Arbeiten. Planen Sie nach Ihren Fähigkeiten möglichst viel ein, das
Sie in der vorgesehenen Zeit zum Abschluss bringen können – das heißt,
so viel Sie können, aber nicht mehr. Als groben Anhaltspunkt sollten Sie
(jedes Gruppenmitglied) etwa elf mit intensiver Arbeit gefüllte Stunden
investieren, keinesfalls mehr als fünfzehn. Versuchen Sie, so effizient wie
möglich zu arbeiten und rasch zu einer brauchbaren Lösung zu kommen.
Ignorieren Sie Details, die Ihnen unwichtig erscheinen. Bedenken Sie, dass
Sie Ihre Lösung durch Testfälle überprüfen sollen und planen Sie Zeit für
die Entwicklung der Testfälle und die Fehlerbeseitigung ein.
Erstellen Sie zuerst ein Konzept Ihrer geplanten Arbeiten. Schicken
Sie es frühzeitig an Ihre_n Tutor_in. Sie werden so bald wie möglich
erfahren, ob das Konzept ausreicht oder Änderungen nötig sind.
Eine Schwierigkeit ist der gleichzeitige Umgang mit mehreren Paradigmen. Sie müssen das prozedurale und objektorientierte Paradigma
verwenden und den Übergang zwischen den Paradigmen in Kommentaren nachvollziehbar beschreiben. Lesen Sie Unterscheidungskriterien im
Skriptum nach. Es wird dazu geraten, die Anzahl der Übergänge zwischen den Paradigmen klein zu halten. Im objektorientierten Teil ist auf
hohen Klassenzusammenhalt, schwache Objektkopplung und die Verwendung von Untertypbeziehungen zu achten.
Für die ersten drei Aufgaben weisen Tutor_innen Sie einige Zeit nach
der Abgabe bei Bedarf auf konkrete Fehler hin und bittet um Beseitigung.
Dies wirkt sich nur dann auf Ihre Beurteilung aus, wenn Sie der Bitte nicht
5

Konzept an Tutor_in

Paradigmen kombinieren

nachkommen. Sie sollten selbst (auch ohne Feedback) ein Gefühl für die
Qualität Ihrer Lösungen entwickeln. Wegen der großen Zahl erwarteter
Fehler können Tutor_innen nicht auf jede Kleinigkeit eingehen.

Warum die Aufgabe diese Form hat
Bei allen anderen Aufgaben geht es darum, am Ende eine vollständige
und perfekte Lösung abzuliefern. In dieser Aufgabe kann man ein solches
Ziel zwar anstreben, aber nicht erreichen. Unter Einhaltung der Bedingungen ist es unmöglich, eine perfekte Lösung zu produzieren. Vielmehr
geht es darum, dass Sie Ihre eigenen Fähigkeiten und Grenzen beim Programmieren unter Zeitdruck als Einzelperson und Gruppe kennenlernen.
Sie sollen selbst erkennen, wo Ihre Stärken liegen und zu welchen Arten
von Fehlern Sie eher neigen (auf allen Ebenen von der Problemanalyse
bis hin zum Testen ebenso wie hinsichtlich der Zusammenarbeit in der
Gruppe). Im Hinblick darauf gibt es keine richtigen und falschen Lösungen. Es ist aber erkennbar, wie sehr Sie sich darum bemüht haben, eine
beinahe unlösbare Aufgabe so gut wie möglich zu lösen.
Das Feedback durch die Tutor_innen wird genau darauf abzielen:
Haben Sie sich ausreichend darum bemüht, in möglichst vielen Bereichen
etwas Machbares zu machen, oder sind in zu vielen Bereichen keine Ansätze erkennbar? In letzterem Fall werden Tutor_innen Nachbesserungen
verlangen, aber nicht, wenn aus Zeitdruck irgendwelche kleine Fehler passiert sind, mit denen bei einer solchen Aufgabe immer zu rechnen ist.
Sie sollen möglichst große Freiheit bei der Lösung der Aufgabe haben
und selbst die Verantwortung für alles übernehmen. Niemand schreibt
Ihnen vor, wie die Aufgabenstellung genau zu verstehen ist.
Diese Aufgabe stellt hohe Anforderungen an jedes Gruppenmitglied
und die Zusammenarbeit in der Gruppe – eine Nagelprobe für das Funktionieren der Gruppe und zum Aufdecken möglicher Schwachstellen.
Nebenbei bietet es sich an, die Aufgabe zur Vertiefung eines überblicksartigen Verständnisses von Paradigmen einzusetzen. Der Schwerpunkt liegt auf der objektorientierten Programmierung (bei einem intuitiven Zugang) im Unterschied zur prozeduralen Programmierung.

6


