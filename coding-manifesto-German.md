# ProPublica News Apps Desk Coding Manifesto

_Von Jeff Larson and Scott Klein, ProPublica_
_Deutsche Übersetzung: Mirko Lorenz_

*Hilf dabei mit, diese Übersetzung so gut wie möglich zu machen. Über Github können Änderungen gemeinsam erfolgen. 

Dies ist ein Manifest für kluges Programmieren innerhalb einer Nachrichtenorganisation. Wir vermeiden dabei allgemeine Aussagen, die über den Bereich hinausreichen, mit dem wir uns auskennen: Journalistische Arbeit unter Zeitdruck mit Nutzung von Programmiercode. Deine Ergebnisse oder Erfahrungen in anderen Bereichen können andere sein. 

Es gibt viele Leitfäden für das Programmieren. Manche sind besser als andere. Einige Vorgaben und Regeln sind wichtiger als andere und sind es wert, beherzigt zu werden. 

Zum Beispiel mögen wir folgende Regel: Programmiercode hat zwei wesentliche Nutzer -- den Compiler und andere Programmierer. Denk daran, dass dein Code irgendwann von anderen Menschen verstanden werden kann. Versuche, so umfassend wie möglich und innerhalb vernünftiger Grenzen und mit Blick auf deinen Abgabetermin Code zu schreiben, der von anderen Entwicklern nachvollzogen werden kann, im Gegensatz zu Programmiercode, der seinen Zweck auf anderen Wegen erreicht. Wenn deine Anwendung immer wieder Veränderungen auf Veränderung erzeugt, ist sie kaputt.

Wichtiger noch als die Etablierung eines gemeinsamen Stils ist die Etablierung eines gemeinsamen Standards für Sicherheit, Kompatibilität und Performance. Schreib Code, der sicher ist, der getestet und optimiert wurde.

Hier sind einige „Best Practices“, denen du folgen solltest: 

Wenn möglich, nutze [Varnish](http://de.wikipedia.org/wiki/Varnish). Alles, was von Varnish ausgeliefert wird, ist schneller als der Code, den du schreiben kannst. Du wirst eine Menge Zeit sparen, wenn Du wenig Aufwand auf Code verwendest, der eh nur von einem einzigen Nutzer gesehen wird, bevor er dann von Varnish in den Cache gezogen wird. Verwende lieber mehr Konzentration auf alle Elemente, die nicht im Cache aufgenommen werden können. 

Alle HTTP-Requests an deine News-Applikation sollten weniger als eine Sekunde brauchen. Die Gesamtgröße einer Seite, inklusiver aller Assets, sollte nicht über 1,5 Megabyte hinausgehen. Selbst diese Größe ist eigentlich schon zu groß. 

Halte dich an Vorgaben und Verfahren für Sicherheit. Setze Patches sofort um, ohne das vor dir herzuschieben. 

Jedes Speicher- und Backup-Konzept, zu dem nicht Übungen für die Wiederherstellung gehören, sind reine Annahmen und könnten im Ernstfall nicht funktionieren. [via](http://shop.oreilly.com/product/9781565926424.do)

Schreib keinen Code, der zukünftige Funktionalitäten vorhersehen soll.

Vermeide es, das Projekt zu vergolden. Journalisten arbeiten unter einer Deadline. Du schreibst keinen Code für die Ewigkeit. 

Beginne früh und oft, die wichtigsten Ausspielplattformen zu testen, insbesondere alle die auf denen du nicht entwickelst. Geh davon aus, dass deine Nutzer keinen wunderschönen Apple-Monitor haben. Schau dir dein Projekt auf einem billigen, älteren Monitor als Zweitbildschirm an und überprüfe alles noch mal in dieser Ansicht. 

Einige Plattformen brauchen besondere Aufmerksamkeit:

Wenn eine Anwendung nicht auf IE8 und darüber funktioniert, ist sie kaputt. 
Wenn eine Anwendung auf einem Mobilgerät abstürzt oder nicht funktioniert, weil sie von auf besondere, nur in PC-Browsern verfügbare Bedienkonzepte setzt, ist sie kaputt.
Wenn eine Anwendung nicht [„responsive“](http://de.wikipedia.org/wiki/Responsive_Webdesign) für verschiedene Bildschirmgrößen ist, könnte sie kaputt sein. Manchmal sind kleine Bildschirme aber auch einfach zu klein. 

Alle Elemente deines Codes sollten eine konkrete Aufgabe haben und den jeweiligen Zustand bewahren. Stell Dir jedes Objekt als eine kleine [Maschine](http://worrydream.com/EarlyHistoryOfSmalltalk/) vor, die eine konkrete Aufgabe hat und mit anderen Objekten über ein Interface kommuniziert. 

Objekte mit einer einfachen, nach außen gerichteten API ermöglichen es Software tatsächlich „soft“ zu sein. 

In JavaScript solltest du auf [Events](http://backbonejs.org/#Events) setzen, die von anderen Objekten abonniert werden können, das ist besser als direkte Aufrufe, wenn das möglich ist. 

Arbeite an Funktionen in einzelnen Strängen und verknüpfe diese mit der Master-Version when die Funktionen vollständig und einsetzbar sind. 

Jede Applikation sollte auf dem Root-Level eine README-Datei anbieten, die erklärt wie die Applikation aufgebaut ist. Diese Anleitungen sollten sich an erfahrene Entwickler richten, die wissen, wie man deine Applikation technisch einrichten, andererseits aber möglicherweise sonst nichts über die Applikation wissen. Die Datei sollte Auskunft darüber geben, wie man Daten in die Applikation einspielt und auf welche Zusatzsoftware die Software in der Entwicklung und späteren Produktion angewiesen ist, ebenso worauf nach der Installation noch zu achten ist. Stell Dir den Leser dieser README-Anleitung als erschöpften, unter Druck arbeitenden Sysadmin vor, der gerade mit einem Komplettausfall des ganzen Systems zu kämpfen hat. Wenn möglich, füge einen Set-Up Datei hinzu, die alle wesentlichen Instruktionen und Kommentare in einem Shell-Script enthält, das die [Einrichtung](http://robots.thoughtbot.com/post/41439635905/bin-setup) übernimmt. Oder nutze einfach [Make](http://bost.ocks.org/mike/make/).

Wiederhol Dich nicht

Tritt nicht irgendwelchen Glaubensrichtungen des Programmierens bei und halte Dich von zu engen Doktrinen fern, die dann Entscheidungen für Dich treffen. Zu viele Tests lassen vermuten, dass mit dem Code irgend etwas nicht stimmt. Teste die Teile deines Codes die getestet werden sollten, letztlich aber ist die Deadline wichtiger als eine Auszeichnung für besondere Code-Qualität.  
