1. Programmieraufgabe

Programmierparadigmen
LVA-Nr. 194.023
2025/2026 W
TU Wien

Kontext
Bienen leisten einen entscheidenden Beitrag zur Vermehrung von Blütenpflanzen und sind für die Nahrungsmittelproduktion unverzichtbar. Imker streichen gerne heraus, dass ihre Honigbienen zu den allerwichtigsten
Nutztieren zählen und die Nahrungsmittelproduktion ohne sie drastisch
zurückgehen würde. Ergebnisse aktueller Untersuchungen schüren jedoch
Zweifel an solchen Darstellungen. Für einen Überblick siehe:
https://www.fibl.org/fileadmin/documents/shop/1633-wildbienen.pdf

Etwa 78% aller Blütenpflanzenarten der gemäßigten Breiten sind für ihre
Bestäubung auf Insekten wie Bienen, Wespen, Fliegen und Käfer angewiesen, unter den wichtigsten Kulturpflanzen 80%. Dafür am wichtigsten
sind Bienen, die in Mitteleuropa mit etwa 750 Arten vertreten sind. Den
Großteil der Bestäubungsleistung übernehmen Wildbienen (dazu zählen
solitäre Bienen und Hummeln) sowie zu einem kleinen Teil Schwebfliegen. Honigbienen erbringen höchstens ein Drittel der Bestäubungsleistung. Wildbienen erhöhen den Fruchtansatz landwirtschaftlicher Kulturen sogar dort, wo Honigbienen häufig sind. Honigbienen können die
Bestäubungsleistung durch Wildbienen ergänzen, aber nicht ersetzen. Einige Kulturpflanzen wie Rotklee, Luzerne oder Tomate sind auf spezialisierte Wildbienenarten angewiesen, da Honigbienen sie meiden.
Wildbienen sind gefährdet (25% bis 68% der Arten) und müssen durch
gezielte Maßnahmen gefördert werden. Die Erhaltung blüten- und kleinstrukturreicher Lebensräume hat höchste Priorität. Vor allem eine enge
Nachbarschaft von Nahrungs- und Nistressourcen (z. B. besonntes Totholz
oder vegetationsarme Bodenstellen) und ein kontinuierliches Blütenangebot sind von entscheidender Bedeutung.

Aufgabe:
Simulation von Blütenpflanzen- und Wildbienenpopulationen
Zur Förderung von Wildbienen wird ein Teil einer landwirtschaftlichen
Fläche für den Bewuchs mit verschiedenen Blütenpflanzen reserviert. Über
Simulationen soll geklärt werden, welche Zusammensetzungen der Pflanzenarten erfolgversprechend sind. Ausgehend von einer Wildbienenpopulation und Populationen verschiedener Blütenpflanzen wird simuliert, wie
sich diese Populationen über einen langen Zeitraum entwickeln, wobei die
Entwicklungen von vorgegebenen Eigenschaften der Blütenpflanzen und
zufällig generierten Witterungsverläufen abhängen.
Eine Simulation kann die immense Komplexität tatsächlicher Vorgänge in der Natur nicht mit vertretbarem Aufwand nachahmen. Wir müssen
daher mit einem grob vereinfachten Modell arbeiten:
Jahresverlauf: Zu simulieren sind jährliche Vegetationsperioden von 240
Tagen (März bis Oktober). In dieser Zeit wird täglich eine Neubewertung vorgenommen. Das restliche Jahr bildet eine Ruhephase.
Die Bewertung der Ruhephase erfolgt in einem einzigen Schritt.
1

Themen:
Aufbau der Zusammenarbeit in der Gruppe,
Einrichten einer
Arbeitsumgebung,
Modularisierung,
nominale Abstraktion

Ausgabe:
13. 10. 2025

Abgabe (Deadline):
20. 10. 2025, 13:00 Uhr

Abgabeverzeichnis:
Aufgabe1-3
Hochladen ins GitRepository mittels push
auch eingebundene
Pakete hochladen
(außer Standard-Pakete)

Programmaufruf:
java Test

Grundlage:
Kapitel 1 des Skriptums

Witterung: Die Witterung wird während der Vegetationsperiode täglich durch die Sonnenscheindauer d und Änderung der Bodenfeuchte
(Niederschlag bzw. Austrocknen) an diesem Tag simuliert. Vereinfachend soll d eine Zufallszahl zwischen 0 und 12 sein (Tageslänge immer gleich). Ab Beginn der Vegetationsperiode aufsummierte Werte
der Sonnenscheindauer ergeben die Sonnenstunden h. Die Bodenfeuchte f mit 0 ≤ f ≤ 1 wird am Beginn der Vegetationsperiode
zufällig gewählt und täglich zufällig um bis zu 10% verändert.
Wildbienenpopulation: Diese wird abstrakt durch eine (nicht unbedingt ganze) Zahl x mit x ≥ 0 dargestellt. Näherungsweise kann
man sie als Anzahl gesunder Individuen beliebiger Wildbienenarten
betrachten. Während der Vegetationsperiode wird x täglich angepasst: Sei n das Nahrungsangebot durch blühende Pflanzen (siehe
unten). Ist n ≥ x, wird x um 3% erhöht. Andernfalls (n < x) wird
x um ((6 · n/x) − 3)% erhöht bzw. verringert. Zu Beginn der Simulation ist ein Anfangswert für x gegeben. Während einer Ruhephase
wird x mit einer Zufallszahl zwischen 0.1 und 0.3 multipliziert, um
zu simulieren, dass viele Wildbienen den Winter nicht überstehen.
Blütenpflanzenpopulationen: Jede Art von Blütenpflanzen bildet jeweils eine eigene Population. Jede Population wird abstrakt durch
drei Zahlen yi , bi und si beschrieben, wobei i über die Arten läuft:
• yi mit yi ≥ 0 bezeichnet die Wuchskraft, das ist die näherungsweise Zahl der Wildbienen, die während der Vollblüte durch
die Pflanzenpopulation täglich Nahrung finden.
• bi mit 0 ≤ bi ≤ 1 ist der Anteil, der in Blüte steht.
• si mit 0 ≤ si ≤ 1 ist die Qualität der Samenentwicklung.
Das oben verwendete Nahrungsangebot n entspricht i (yi · bi ), also
der Summe von yi multipliziert mit bi für alle Arten i. Zu Beginn
der Vegetationsperioden sind bi und si gleich 0. Anfangswerte für
yi sind zu Beginn der Simulation gegeben. In Ruhephasen wird yi
+
mit si und einer Zufallszahl zwischen c−
i und ci multipliziert, um
−
die Vermehrung zu simulieren. Dabei sind ci und c+
i für die Pflanzenart i typische Konstanten. Tägliche Anpassungen von yi , bi und
si während Vegetationsperioden beruhen ebenso auf Konstanten:
P

• Die Feuchtegrenzen fi− und fi+ mit 0 < fi− < fi+ < 1 definieren den günstigen Bereich der Bodenfeuchte. Im Fall von
fi− /2 < f < fi− oder fi+ < f < 2 · fi+ (ungünstiger Bereich),
wird yi um 1% reduziert. Gilt sogar f ≤ fi− /2 oder 2 · fi+ ≤ f
(sehr ungünstiger Bereich), wird yi um 3% reduziert.
−
+
+
• Die Blühgrenzen h−
i und hi mit 0 < hi < hi stehen für die
Sonnenstunden, ab denen die Blüte einsetzt bzw. endet. Die
Blühintensität qi mit 0 < qi < 1/15 ist ein Faktor, der angibt,
+
wie rasch die Blüte einsetzt bzw. endet. Gilt h−
i ≤ h < hi
(Blüte setzt ein), wird bi pro Tag um qi · (d + 3) erhöht, bis bi
das Maximum von 1 erreicht, wobei d die Sonnenscheindauer
an diesem Tag ist. Gilt h+
i ≤ h (Blüte endet), wird bi täglich
um qi · (d + 3) verringert, bis bi das Minimum von 0 erreicht.

2

−
• Die Bestäubungswahrscheinlichkeit pi (0 < pi < 1/(h+
i − hi ))
ist die Wahrscheinlichkeit, mit der eine Blüte bei ausreichend
vielen Bienenbesuchen innerhalb einer Sonnenstunde (und zu
einem kleinen Teil auch ohne Sonne) einen Samen ausbildet.
Ausreichend viele Bienenbesuche gibt es bei x ≥ n (Bienenpopulation x mindestens so groß wie Nahrungsangebot n); dann
erhöht sich si pro Tag um pi · bi · (d + 1). Andernfalls erhöht
sich si pro Tag um pi · bi · (d + 1) · x/n.

Für jeden Simulationslauf sind also folgende Parameter festzulegen:
• Anzahl der zu simulierenden Jahre,
• Anfangswert der Wildbienenpopulation x,
• für jede Blütenpflanzenart (Index i läuft über die Arten):
– Anfangswert der Wuchskraft yi ,
+
– für die Art typische Vermehrungsgrenzen c−
i und ci ,

– für die Art günstige Feuchtegrenzen fi− und fi+ ,
+
– für die Art typische Blühgrenzen h−
i und hi ,

– für die Art typische Blühintensität qi ,
– für die Art typische Bestäubungswahrscheinlichkeit pi .
Ergebnisse jedes Simulationslaufs enthalten den Wert der Wildbienenpopulation x und für jede Blütenpflanzenart i die Wuchskraft yi jeweils am
Ende der Ruhephase nach der letzten simulierten Vegetationsperiode.
Das Ziel besteht darin, eine stabile Menge an Blütenpflanzenarten
zu finden, die am Ende von Simulationsläufen über viele Jahre zu einer
großen Wildbienenpopulation führt. „Stabil“ bedeutet dabei, dass die yi
zwar von Jahr zu Jahr (auch stark) schwanken können, aber keine Art
(beinahe) ausstirbt oder (beinahe) ständig nur wächst. Im Idealfall liegt
yi für alle i am Ende der Simulation in derselben Größenordnung wie die
Anfangswerte. Die Parameter der einzelnen Pflanzenarten sollen möglichst unterschiedlich sein, um eine gewisse Robustheit gegenüber zufällig
weniger günstiger Witterung zu erreichen.

Welche Aufgabe zu lösen ist
Programm. Entwickeln Sie ein Java-Programm, das Simulationsläufe
wie oben beschrieben durchführt. Konkret sollen drei Gruppen von Simulationsparametern (also vor allem unterschiedliche Gruppen von Blütenpflanzenarten) festgelegt werden, die möglichst stabil sind. Jede Gruppe
soll zwischen 10 und 25 Blütenpflanzenarten umfassen. Für jede Gruppe sollen 10 Simulationsläufe mit unterschiedlicher Witterung (also mit
unterschiedlichen Zufallswerten) über Zeiträume von jeweils 25 Jahren
durchgeführt werden. Die Parameter und Simulationsergebnisse sind in
möglichst übersichtlicher Weise in Textform auszugeben. Danach, deutlich von den Ergebnissen der eigentlichen Simulationsläufe abgesetzt, sollen zur Überprüfung der korrekten Vorgehensweise für einen Simulationslauf jährliche Zwischenergebnisse und für ein Jahr tägliche Zwischenergebnisse mit allen Zahlen, die Zustände beschreiben, ausgegeben werden.
3

Testen. Testen Sie Ihr Programm sorgfältig, auch bezüglich der Plausibilität von Simulationsergebnissen. Sorgen Sie dafür, dass nach dem
Programmstart keine Benutzerinteraktion (das heißt, keine Eingabe über
die Tastatur oder Maus) nötig ist, sondern einfach nur die nötigen Ausgaben gemacht werden. Das Programm soll (nach neuerlicher Übersetzung aller vorhandenen .java-Dateien) mittels java Test vom Verzeichnis Aufgabe1-3 aus aufrufbar sein. Sie können natürlich davon ausgehen,
dass .class-Dateien an passenden Stellen angelegt werden, aber Sie müssen vor allem bei Verwendung von Paketen für die Ausführbarkeit durch
den vorgegebenen Aufruf im vorgegebenen Verzeichnis sorgen.
Kommentare. Betrachten Sie jede Definition und Deklaration einer Methode als nominale Abstraktion. Beschreiben Sie diese Abstraktionen
durch kurze, aber informative Kommentare. Versehen Sie auch jede Klasse und jedes Interface mit entsprechenden Kommentaren. Eine JavaKlasse kann Elemente unterschiedlicher Modularisierungseinheiten enthalten (Modul, Klasse, Objekt). Beschreiben Sie in den Kommentaren
deutlich, welche Elemente zu welchen Modularisierungseinheiten gehören
und welche Abstraktionen hinter den Modularisierungseinheiten stecken.
Sorgen Sie für eine gute Programmstruktur mit mehreren Klassen.
Neben Programmtext soll die Datei Test.java als Kommentar am
Dateianfang eine kurze, aber verständliche Beschreibung der Aufteilung
der Arbeiten auf die einzelnen Gruppenmitglieder enthalten – wer hat
was gemacht. Beschreibungen wie die folgende reichen nicht: „Alle haben
mitgearbeitet.“ Die Arbeitsaufteilung auf die einzelnen Gruppenmitglieder wird in jeder Aufgabe beschrieben werden müssen. Bitte machen Sie
das sorgfältig (keinesfalls jemand vergessen), weil sich eine stark unterschiedliche Belastung einzelner Gruppenmitglieder über mehrere Aufgaben hinweg auf die Beurteilung auswirken kann.1

Programmname „Test“
aus gutem Grund gewählt

im richtigen Verzeichnis
ausführbar?

Abstraktionen und
Modularisierungseinheiten
kurz beschreiben
(siehe Skriptum)

Arbeitsaufteilung kurz,
verständlich beschreiben

Wie die Aufgabe zu lösen ist
Der Programmtext Ihrer Lösung soll möglichst einfach sein und keine unnötige Funktionalität haben. Er soll wiederverwendbar sein, da die nächste Aufgabe auf Teilen davon aufbaut. Vermeiden Sie jedoch Vorgriffe,
das heißt, schreiben Sie keine Programmteile aufgrund der Vermutung,
dass diese Teile in der nächsten Aufgabe verlangt sein könnten.
Zufallszahlen spielen eine große Rolle, aber auch fest vorgegebene Annahmen. Es kommt auf ein ausgewogenes Verhältnis zwischen algorithmischen Vorgaben, festgelegten Werten und Zufallswerten an. Um gute
Einstellungen zu finden, wird es notwendig sein, mit verschiedenen Werten und Vorgehensweisen zu experimentieren. Bei Simulationen geht es
häufig, nicht nur in dieser Aufgabe darum, passende Parametrisierungen
1

Durch Krankheit oder sonstige Vorkommnisse ist es immer möglich, dass eine Person nicht bei jeder Aufgabe gleich intensiv mitarbeiten kann. Daher hat eine ungleichmäßige Arbeitsaufteilung bei einer einzelnen Aufgabe noch keine direkte Konsequenz.
Es kann aber auch in diesem Fall sein, dass Ihr_e Tutor_in oder die LVA-Leitung nach
einer Ursache dafür fragt. Wenn sich über mehrere Aufgaben hinweg zeigt, dass immer
wieder eine Person deutlich mehr oder weniger macht als die anderen Gruppenmitglieder, wird die Beurteilung für einzelne Gruppenmitglieder unterschiedlich ausfallen.
Dabei werden aber auch die von Ihnen genannten Gründe eine Rolle spielen.

4

einfach halten

experimentieren

zu finden, sodass Simulationsergebnisse das möglichst gut wiedergeben,
was wir in der Realität vorfinden.
Diese Aufgabe hilft Ihren Tutor_innen, Ihre Kenntnisse sowie die Zusammenarbeit in der Gruppe einzuschätzen. Bitte sorgen Sie in Ihrem eigenen Interesse dafür, dass jedes Gruppenmitglied etwa in gleichem Maße
mitarbeitet. Sonst könnten Sie bei einer Fehleinschätzung wertvolle Zeit
verlieren. Scheuen Sie sich bitte nicht, Tutor_innen um Hilfe zu bitten,
falls Sie bei der Lösung der Aufgabe Probleme haben oder keine brauchbare Zusammenarbeit in der Gruppe zustande kommt.

alle arbeiten mit

Warum die Aufgabe diese Form hat
Umfang und Schwierigkeitsgrad der Aufgabe wurden so gewählt, dass die
eigentliche Programmierung bei guter Organisation und entsprechendem
Vorwissen nicht zu viel Zeit in Anspruch nimmt, aber eine Einarbeitung
in neue Themen nötig ist und Diskussionsbedarf entsteht. Nutzen Sie die
Gelegenheit, um die Aufgabenverteilung und interne Abläufe innerhalb
der Gruppe zu organisieren. Details der Aufgabe bleiben bewusst offen:
• Sie sollen in der Gruppe diskutieren, wie Sie die Aufgabe verstehen
und welche Lösungswege geeignet erscheinen.
• Sie sollen sich daran gewöhnen, dass Aufgaben nicht vollständig spezifiziert sind, aber trotzdem Vorgaben eingehalten werden müssen.
• Sie sollen sich eine eigene brauchbare Faktorisierung überlegen und
sich dabei vorerst einmal nur von Abstraktionen leiten lassen.
• Sie sollen auch die Verantwortung für die Korrektheit Ihrer Lösung
(so wie Sie sie selbst verstehen) übernehmen, indem Sie entsprechende Tests durchführen.

Allgemeine Informationen zur Übung
Folgende Informationen betreffen diese und auch alle weiteren Aufgaben.

Was bei der Lösung der Aufgabe zu beachten ist
Unter der Überschrift „Wie die Aufgabe zu lösen ist“ finden Sie Hinweise darauf, wie Sie die Lösung der Aufgabe vereinfachen können und
welche Fallen Sie umgehen sollen, erfahren aber auch, welche Aspekte
bei der Beurteilung als wichtig betrachtet werden. In der ersten Aufgabe
kommt es beispielsweise auf die Einfachheit der Lösung an, aber auch darauf, wie gut die gewählten Algorithmen und angenommenen Werte bzw.
Zufallswerte zusammenpassen. Das heißt, in späteren Aufgaben können
Ihnen bei solchen Hinweisen etwa auch für unnötig komplizierte oder umfangreiche Lösungen Punkte abgezogen werden, weil Sie sich nicht an
die Vorgaben gehalten haben. Außerdem gilt natürlich alles, was in der
Aufgabe beschrieben ist. Beispielsweise müssen Kommentare die gewählten Abstraktionen verdeutlichen und beschreiben, welche Inhalte als Teil
welcher Modularisierungseinheiten anzusehen sind. Unterschiedliche Aufgaben haben unterschiedliche Schwerpunkte. Die nächste Aufgabe wird
5

Schwerpunkte beachten

nicht nach dem gleichen Schema beurteilt wie die vorige. Richten Sie sich
daher nach der jeweiligen Aufgabenstellung.
Ein häufiger Fehler besteht darin, eine Aufgabe nach Gefühl zu lösen
ohne zu verstehen, worauf es ankommt. Meist bezieht sich die Aufgabe
auf ein Thema, das zuvor theoretisch behandelt wurde. Versuchen Sie,
eine Beziehung zwischen der Aufgabenstellung und dem davor behandelten Stoff herzustellen. Achten Sie darauf, Fachbegriffe nicht nur umgangssprachlich zu interpretieren, sondern so wie im Skriptum beschrieben. Die
ersten Aufgaben sind vielleicht auch ohne Skriptum lösbar, bei späteren
Aufgaben würde ein Ignorieren des Skriptums wahrscheinlich zu Fehlern
führen. Als Hilfestellung sind in jeder Aufgabenstellung Teile des Skriptums genannt, in denen die relevantesten Themen behandelt werden, bei
komplizierten Themen oft nur wenige Seiten.
Versuchen Sie nicht, Teile der Aufgabenstellung durch Tricks oder
Spitzfindigkeiten zu umgehen. Beispielsweise gibt es immer wieder Lösungsversuche, in denen die Test-Klasse nur „Test erfolgreich“ ausgibt,
statt sinnvolle Tests durchzuführen. Solche Versuche werden durch händische Beurteilungen mit hoher Wahrscheinlichkeit erkannt. Spätere Aufgaben enthalten oft Schwierigkeiten, die mit Allgemeinwissen alleine oder
über aufgabenbezogene Web-Recherchen bzw. mit Hilfe von KI kaum zu
lösen sind. Gerade in solchen Fällen ist davon abzuraten, die Schwierigkeiten durch Tricks zu umgehen. Hinweise zur richtigen Lösung lassen
sich im Skriptum und auf den Vorlesungsfolien finden.
Ihre Lösung, bestehend aus .java-Dateien, muss am Tag der Abgabe
um 13:00 Uhr pünktlich im Git-Repository Ihrer Gruppe stehen. Übersetzte .class-Dateien sollen nicht ins Repository gestellt werden, da sie
die Zusammenarbeit in der Gruppe erschweren und vor der Beurteilung
ohnehin neu generiert werden. Zugangsinformationen zum Repository erhalten Sie in Kürze. Informationen zum Umgang mit dem Repository
finden Sie in TUWEL. Es wird empfohlen, rechtzeitig vor der Deadline
die Lösung auf dem Übungsrechner auszuprobieren und die Daten dabei durch pull aus dem Repository zu laden. So können Sie typische
Fehler bei der Abgabe (z.B. auf push vergessen, Lösung im falschen Verzeichnis, falsche package- und include-Anweisungen, Klassen aus NichtStandard-Paketen verwendet und nicht mit abgegeben) sowie Inkompatibilitäten aufgrund unterschiedlicher Versionen und Betriebssystemeinstellungen (z. B. Dateinamen mit Umlauten sowie neueste Sprach-Features
nicht unterstützt) erkennen und beseitigen.

Was Ihr_e Tutor_in von Ihnen wissen möchte
Ihr_e Tutor_in wird Ihnen in Kürze eine Mail schreiben, um sich vorzustellen und um Informationen über Sie zu bitten. Geben Sie diese Informationen möglichst bald, damit die für Sie am besten geeignete Form
der Betreuung gewählt werden kann. Unabhängig von der Form der Betreuung kann natürlich jedes Gruppenmitglied jederzeit konkrete Fragen
an Tutor_innen richten. Scheuen Sie sich bitte nicht, sich auch mit organisatorischen oder gruppeninternen Problemen, die Sie möglicherweise
nicht selbst lösen können, an Tutor_innen zu wenden. Früh im Semester
sind Probleme einfacher lösbar als im weit fortgeschrittenen Semester.

6

strukturiert vorgehen

keine Spitzfindigkeiten

ausprobieren


