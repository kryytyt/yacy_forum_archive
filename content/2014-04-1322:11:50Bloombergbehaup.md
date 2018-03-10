Bloomberg behauptet, die NSA habe Heartbleed schon \...
=======================================================

Date: 2014-04-13 22:11:50

[Bloomberg behauptet, die NSA habe Heartbleed schon seit Jahren
exploited](http://www.bloomberg.com/news/2014-04-11/nsa-said-to-have-used-heartbleed-bug-exposing-consumers.html).
Die Quellenlage scheint mehr als dünn zu sein, und ich halte das auch
für eher unwahrscheinlich, weil selbst heute bei weitem noch nicht alle
auf OpenSSL 1.0.1 umgestellt haben. Der Bug ist überhaupt erst seit
OpenSSL 1.0.1 dabei. Vor zwei Jahren hätte das ein paar Nerds betroffen,
niemanden relevanten. Vor zwei Jahren einen Exploit gehabt haben, das
mag sein.

Aber die Kernbotschaft, egal ab wann Geheimdienste das exploited haben,
ist: Geheimdienste arbeiten gegen ihre eigene Bevölkerung, nicht für
sie. Die Geheimdienste wussten davon und haben nichts gesagt.

Oh und eine Sache noch: Das sieht jetzt hier aus wie eine
Bankrotterklärung von Open Source. Das stimmt nicht. Der Bug wurde von
zwei Leuten gleichzeitig gefunden und gemeldet. Einmal von einer
Security-Firma, die eine Testsuite für SSL-Bugs programmiert hat. Die
hätte das auch bei einem Nicht-Open-Source-SSL gefunden. Aber der andere
Finder war ein Google-Angestellter, der einen Quellcode-Audit gemacht
hat. Den hätte es so bei einem Nicht-Open-Source-SSL nicht gegeben. Wir
haben hier also die Chancen direkt verdoppelt, solche Bugs zu finden.
Wer weiß, was in Kommerzsoftware noch so für Untiefen lauern.

Meiner Erfahrung nach variiert die Codequalität bei Open Source und bei
kommerzieller Software immens, und der Durchschnitt liegt ungefähr auf
einem vergleichbaren Niveau. Man kann nicht davon ausgehen, dass
kommerzielle Software grundsätzlich ein höheres Niveau hat.

Übrigens stört mich an der Debatte ein bisschen, dass so wenig Leute
daraus Konsequenzen ziehen. Wir benutzen alle die ganze Zeit Open Source
Software, ohne dafür zu zahlen, und wir benutzen Kommerzsoftware und
bezahlen dafür. Dann wundern wir uns, dass die Hersteller von
Kommerzsoftware Geld haben, um davon Audits machen zu lassen, aber die
Open Source-Leute warten müssen, bis Google mal vorbeikommt.

Eine mögliche Konsequenz aus dem aktuellen Geschehen könnte sein, dass
man mal einen Fonds macht, in den Benutzer von Open Source-Software
einzahlen, und mit dem dann Qualitätssicherungsmaßnahmen bezahlt werden,
für die Freiwillige bei den jeweiligen Projekten nicht die Motivation
aufbringen. Das meint natürlich Security-Audits, aber es meint auch
sowas wie ordentliche Testsuiten basteln; Dokumentation bereitstellen.

**Update**: [Die US-Regierung
dementiert](https://twitter.com/sinderbrand/status/454723060231184384/photo/1).
Was sollen die auch sonst sagen. Sie behaupten sogar, dass sie alle
Lücken reporten, die sie finden. Ja nee, klar.