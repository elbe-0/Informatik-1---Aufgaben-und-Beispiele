# Mission MotoTec - Design-Dokument

## Konzept

Refactoring aller Informatik-I-Aufgaben zu einer durchgehenden Storyline: **"Mission MotoTec"**.

Die Studierenden sind IT-Notfallteam der **MotoTec GmbH**, einer Autofabrik nach IT-Totalausfall. Werksleiterin **Ingrid Kemper** (erfahren, pragmatisch, trocken-humorvoll) fuehrt sie durch die Rettung. Jede Aufgabe = ein konkretes Problem in der Fabrik, das geloest werden muss.

### Narrative Struktur pro Notebook

1. **Briefing** (Markdown, 3-5 Saetze): Lage in der Fabrik
2. **Dialog mit Frau Kemper** (kursiv/zitiert): Konkrete Aufgabe und Motivation
3. **Aufgabe**: Programmieraufgabe im Fabrik-Kontext
4. **Debriefing** (Pflicht): Kemper kommentiert das Ergebnis, fasst das Gelernte zusammen

### Loesungs-Notebooks

Fuer jede Aufgabe wird ein separates Loesungs-Notebook im Fabrik-Kontext erstellt (analog zu den bestehenden `_Lsg`-Notebooks). Die Loesung enthaelt denselben narrativen Rahmen (Briefing, Kemper-Dialog) plus vollstaendig kommentierte Musterloesung.

### Akzeptanzkriterien

- Aufgaben machen Spass (Krimi-/Rettungsstory, Problemloesung als Motivation)
- Vermitteltes Wissen bleibt identisch (1:1-Mapping jeder Originalaufgabe)
- Schwierigkeitsgrad vergleichbar (gleiche Progression 1/5 -> 4/5)
- Sinnvolle Kontext-Integration (jedes Thema hat natuerlichen Grund in Fabrikrettung)

---

## Story-Arc

| Kapitel | Titel | Fabrik-Phase | Stimmung | Kemper-Tonfall |
|---|---|---|---|---|
| 1 | Blackout | Systeme hochfahren | Hektisch, Dunkelheit, Grundlagen | Angespannt, knapp, bestimmt: "Keine Zeit fuer Erklaerungen. Terminal an." |
| 2 | Fehlkalibrierung | Sensoren reparieren | Methodisch, Diagnose | Ruhiger, analytisch: "Gut, dass das Terminal laeuft. Jetzt systematisch." |
| 3 | Fertigungsstrasse ausser Kontrolle | Produktionslogik fixen | Aufbauend, Kernarbeit | Fordernd, aber anerkennend: "Das ist das Herzstueck. Konzentration." |
| 4 | Lagerchaos | Lager organisieren | Ordnung, Komplexitaet | Genervt ueber das Chaos, pragmatisch: "Da drin sieht's aus wie Kraut und Rueben." |
| 5 | Code-Review | Eigenen Code professionalisieren | Professionalisierung | Mentor-Modus: "Funktioniert ist nicht genug. Jetzt machen wir's richtig." |
| 6 | Investoren-Pitch | Daten auswerten, Fabrik retten | Finale, Triumph | Aufgeregt-motiviert, dann stolz: "Morgen kommen die Geldgeber. Das ist unsere Chance." |

---

## Kapitel 1: "Blackout" (IDE-Einfuehrung)

**Briefing:** Die Fabrikhalle ist dunkel. Kein System reagiert. Frau Kemper steht mit Taschenlampe am Hauptterminal.

**Kemper-Stimmung:** Angespannt und knapp. Keine Zeit fuer Smalltalk.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 1.1 | Hello World, Begruessung (Original enthaelt auch `def`/`return` - wird hier bewusst entfernt, da Funktionen erst Kapitel 5) | Terminal hochfahren: Bootsequenz, Techniker-Name eingeben, Statusmeldung ausgeben. Rein prozedural, keine Funktionen. | `print()`, `input()`, Strings |
| 1.2 | Zwei Zahlen eingeben & addieren | Stromversorgung pruefen: Spannungswerte per `input()` eingeben, String-Problem entdecken | `input()`, `int()`, String vs. Integer |
| 1.3 | Steuerzeichen | Statusanzeige reparieren: Ein ASCII-Art-Dashboard mit Escape-Zeichen formatieren, Ladebalken mit `\r` fuer Systemstart | `\n`, `\t`, `\r`, `\b`, `print(end="")` |
| 1.4 | Escape-Zeichen Aufgabe | System-Dashboard: Fabriksystem-Uebersicht (Strom/Wasser/Netzwerk je mit Status) als formatiertes ASCII-Layout mit `\t` und `\n` in einem einzigen `print()` ausgeben | `\t`, `\n`, Formatierung |

**Schwierigkeit:** 1/5

**Debriefing-Beispiel:** Kemper: *"Terminal laeuft. Erster Schritt geschafft. Aber das war der einfache Teil."*

---

## Kapitel 2: "Fehlkalibrierung" (Variablen & Datentypen)

**Briefing:** Terminal laeuft, aber Sensoren liefern falsche Werte. Temperatur als Text, negative Drehzahlen. Irgendjemand hat die Konfiguration verhunzt.

**Kemper-Stimmung:** Ruhiger als Kapitel 1, systematisch-analytisch. *"Eins nach dem anderen."*

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 2.1 | Auskommentieren, Dokumentation | Maschinendiagramm bereinigen: Ein `matplotlib`-Plot zeigt Maschinendaten, aber mit falschen/ueberfluessigen Elementen (z.B. Testdaten, falsche Achsenbeschriftung, Debug-Linie). Durch gezieltes Auskommentieren bestimmter Code-Zeilen veraendert sich die Grafik - Studierende sehen visuell den Effekt von Kommentaren. Plus: Code-Dokumentation mit Header-Kommentar. Kemper: *"Das Diagramm sieht aus wie Kraut und Rueben. Raumt das auf - und dokumentiert was ihr gemacht habt."* | `#`, mehrzeilige Kommentare, Doku-Header, visuelles Feedback durch `matplotlib` |
| 2.2 | Datentyp aendert sich | Warum spinnt der Sensor? Variable `drehzahl` ist `int`, nach Division durch Korrekturfaktor ploetzlich `float`. Studierende untersuchen mit `type()` warum die Weiterverarbeitung fehlschlaegt. | `type()`, `int`/`float`, implizite Typaenderung |
| 2.3 | Variablen-Beispiele | Maschinenpass rekonstruieren: Maschinendatenbank ist weg. Variablen neu anlegen: `maschinen_id = 1042` (int), `max_temp = 85.5` (float), `bezeichnung = "Presswerk Alpha"` (str) | Variablen, `int`, `float`, `str` |
| 2.4 | Explizite Typumwandlung | Sensordaten reparieren: Temperatursensor liefert `"72.4"` als String. Damit kann nicht gerechnet werden. Problem finden, explizit konvertieren. | `float()`, `int()`, `str()`, `type()` |
| 2.5 | Bibliotheken: math, random, time (Demo) | Werkzeugkasten aktivieren (Demo-Notebook): `math.sqrt()` fuer Toleranzberechnung, `random.randint()` fuer Testsimulation, `time.sleep()` + `time.strftime()` fuer Logeintraege mit Zeitstempel. Reines Demonstrations-Notebook, keine Aufgabe. | `import`, `math`, `random`, `time` |
| 2.6 | Neu (aus PowerPoint-Skript) | Zylinderberechnung: Kemper: *"Der Roboterarm braucht eine neue Dichtung. Schreibt mir ein Programm das den Radius entgegennimmt und Umfang sowie Flaeche des Querschnitts berechnet."* Nutzer gibt Radius ein, Programm berechnet mit `math.pi` Umfang (2 * pi * r) und Flaeche (pi * r²) und gibt beides aus. | `math.pi`, `input()`, `float()`, Berechnungen |
| 2.7 | Neu (aus PowerPoint-Skript) | Zylinderberechnung mit Verzoegerung: Programm aus 2.6 erweitern - Flaeche wird 2 Sekunden nach dem Umfang ausgegeben. Kemper: *"Die Anzeige soll die Werte nacheinander anzeigen, nicht alles auf einmal. Baut eine Verzoegerung ein."* | `time.sleep()` |
| 2.8 | Neu (aus PowerPoint-Skript) | Zylinderberechnung mit Zeitstempel: Programm aus 2.7 erweitern - bei jeder Ausgabe wird die aktuelle Uhrzeit mit ausgegeben. Kemper: *"Jede Berechnung muss protokolliert werden. Mit Zeitstempel."* | `time.strftime()`, `time.localtime()` |
| 2.9 | Zufallszahlen plotten | Stresstest: Maschine laeuft wieder, aber ist sie stabil? 10 simulierte Temperaturwerte (random 50-90) ueber die Zeit messen und plotten. Kemper: *"Zeigt mir ob die Temperatur stabil bleibt oder ob wir ein Problem haben."* | `random`, `matplotlib`, `while`, `time.sleep()` |

**Schwierigkeit:** 1.5/5

---

## Kapitel 3: "Fertigungsstrasse ausser Kontrolle" (Operatoren & Kontrollstrukturen)

**Briefing:** Maschinen laufen, aber Fertigungslogik ist zerschossen. Autos werden falsch sortiert, Qualitaetskontrolle winkt alles durch, Roboter arbeiten in Endlosschleifen. Kemper: *"Das hier ist das Herzstueck der Fabrik. Wenn die Steuerungslogik nicht stimmt, produzieren wir Schrott."*

**Kemper-Stimmung:** Fordernd, erkennt aber auch gute Arbeit an. Das ist der groesste Brocken.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 3.1 | Quersumme, teilbar-durch-5, kombinierte Bedingung | Seriennummer-Pruefung: 3-stellige Auto-Seriennummer eingeben. (a) Quersumme berechnen (Pruefziffer). (b) Teilbar durch 5? -> Sondermodell. (c) Teilbar durch 5 UND > 100? -> Exportmodell. | `//`, `%`, `if/else`, `and`, `int(input())` |
| 3.2 | Loesungen 3.1 | Loesungen Seriennummer-Pruefung | identisch |
| 3.3 | Operatorrangfolge vorhersagen | Fehldiagnose Sortiermaschine: Die Sortierlogik enthaelt komplexe Bedingungen. Studierende muessen vorhersagen was die Maschine tut, BEVOR sie den Code ausfuehren. Kemper: *"Die Sortiermaschine schickt SUVs in die Kleinwagen-Spur. Schaut euch die Bedingungen an."* | Operatorrangfolge, `**`, `//`, `%`, `and`/`or` |
| 3.4 | if/elif Verhalten + Einrueckung | Roboterarm-Steuerung debuggen: Verschachtelte `if/elif`-Ketten steuern den Roboterarm. Warum greift er daneben? Code-Verhalten vorhersagen, Einrueckungsfehler finden. | `if/elif/else`, Einrueckung |
| 3.5 | Magic 8-Ball | Maschinen-Orakel: Die alte CNC-Maschine "Helga" hat eine Macke - wenn man sie nach der Teilequalitaet fragt, gibt sie zufaellige, teils absurde Antworten (z.B. "Frag mich nochmal nach der Mittagspause", "Teil ist so gut, ich wuerde meinen Porsche draus bauen", "Ergebnis unklar, Kaffeemaschine ist auch kaputt"). Humorvolle Zufallsantworten per `if/elif`-Kette. | `random.randint()`, `if/elif` |
| 3.6 | Taschenrechner | Materialkalkulator: Zwei Materialmengen und eine Rechenoperation eingeben (+, -, *, /). Kemper: *"Die Einkaufsabteilung braucht ein Tool um Materialbedarfe schnell zu berechnen."* | `input()`, `if/elif`, Arithmetik |
| 3.7 | Schere-Stein-Papier-Echse-Spock | Pausenraum-Duell: In der Mittagspause hat das Werkstatt-Team ein eigenes Streit-Schlichtungsspiel entwickelt: Schraubenschluessel-Schaltplan-Sicherung-Kabel-Multimeter (5 Optionen, asymmetrische Regeln, identische Spielmechanik wie das Original). Kemper: *"Bei uns wird das fair entschieden. Auch wer den letzten Kaffee bekommt."* Das Spiel bleibt ein Spiel - nur im Fabrik-Pausenraum verortet. | `random`, verschachtelte Bedingungen, Spiellogik |
| 3.8 | break/continue vorhersagen | Fliessband-Steuerung analysieren: Code-Snippets mit `break`/`continue` in einer Fliessband-Schleife. Welche Autos werden uebersprungen? Wann stoppt das Band? | `break`, `continue` |
| 3.9 | Alle Teiler einer Zahl | Schichtplanung: Kemper: *"Wir haben X Mitarbeiter. In wie viele gleichgrosse Teams kann ich die aufteilen?"* Alle ganzzahligen Teiler berechnen. | `for`, `range()`, `%` |
| 3.10 | Wie oft durch 2 teilbar | Halbierungsmaschine: Ein Stahlblock wird wiederholt halbiert. Wie oft kann man halbieren, bis er nicht mehr teilbar ist? | `while`, `//`, Zaehler |
| 3.11 | Zinsberechnung (Sparen ueber 50 Jahre, 7%) | Ruecklagen-Rechner: MotoTec legt monatlich Geld fuer neue Maschinen zurueck. Wie entwickelt sich das Kapital ueber 50 Jahre bei 7% jaehrlicher Rendite? Mit Eingabevalidierung fuer die monatliche Rate (50-300 EUR). Kemper: *"Rechnet mir das durch, bevor ich zur Bank gehe."* WICHTIG: Mathematik identisch zum Original = Kapitalaufbau durch regelmaessiges Sparen, NICHT Kredit-Tilgung. | `while`, Zinseszins, Eingabevalidierung |
| 3.12 | Debugger (Primzahlen mit Fehlern) | Notfall-Patch: Ein ehemaliger Mitarbeiter hat eine Funktion zur Chargenprufung geschrieben - voller Bugs (C-Syntax wie `int n =`, fehlender Doppelpunkt, `=` statt `==`, falscher Zaehler). Kemper: *"Der Typ hat Java programmiert, kein Python. Findet alle Fehler."* Story minimal halten, Fokus auf Fehlersuche. | Syntax-/Logikfehler, Debugging, `while`, `if`, `%` |

**Schwierigkeit:** 2.5-3/5

---

## Kapitel 4: "Lagerchaos" (Strings & Listen)

**Briefing:** Die Produktion laeuft halbwegs, aber das Lager ist eine Katastrophe. Etiketten falsch, Regale durcheinander, niemand weiss wo was steht. Kemper: *"Bevor wir ausliefern koennen, muss das Lager stimmen. Jedes Teil, jedes Regal, alles muss inventarisiert und auffindbar sein."*

**Kemper-Stimmung:** Genervt ueber das Chaos, pragmatisch. *"Da drin sieht's aus wie Kraut und Rueben."*

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 4.1 | String-Ops: "Strauss, & Co., Levi" -> "Levi Strauss & Co." rekonstruieren | Etiketten reparieren: Zulieferer-Datenbank hat fehlerhafte Eintraege. Aus `"GmbH, MotoTec, Zulieferer"` den korrekten Namen `"MotoTec Zulieferer GmbH"` rekonstruieren (Slicing, Reordering) plus `replace("ae", "ä")` fuer Umlaute. Kemper: *"Die Zulieferer-Datenbank ist Muell. Repariert die Eintraege."* | String-Indexing, Slicing, `len()`, `find()`, `replace()` |
| 4.2 | 1D-Listen Aufgabe 7_1: 4 Automarken-Variablen -> Liste | Teilelager digitalisieren: Vier einzelne Teile-Variablen (`teil1 = "Kolben"` etc.) in eine Liste ueberfuehren und ausgeben. Kemper: *"Einzelne Zettel am Regal sind vorbei. Ab jetzt digitale Inventarliste."* | `list`, `for x in list`, `print()` |
| 4.3 | 1D-Listen Aufgabe 7_2: Erstes Element loeschen, zweites per Eingabe ersetzen | Teilelager bearbeiten: Erstes Teil wurde verbaut -> loeschen. Zweites Teil ist falsch erfasst -> per `input()` korrigieren. | `pop()`, `remove()`, Indexing, `input()` |
| 4.4 | 1D-Listen Aufgabe 7_3: Funktion zum Suchen und Ersetzen in Liste | Teilelager durchsuchen: Funktion schreiben die ein Teil im Lager sucht und gegen ein neues ersetzt. Kemper: *"Wenn der Zulieferer wechselt, muessen wir alle Teile dieses Typs umbuchen."* | `index()`, Funktion, `for`-Schleife, Listen-Methoden |
| 4.5 | 2D-Listen: Schachbrett interaktiv befuellen | Lagerhalle als 8x8-Raster: Die Lagerhalle hat 8 Reihen mit je 8 Regalplaetzen. Teile interaktiv einlagern (Typ + Reihe + Spalte eingeben). Nach jeder Einlagerung: Lagerplan anzeigen. | 2D-Listen, List-Comprehension, verschachtelte `for`, `while`, `input()`, `clear_output()` |
| 4.6 | Weissen Koenig finden | Teil suchen: Wo steht ein bestimmtes Teil im Lager? Mit verschachtelten Schleifen das gesamte Raster durchsuchen. Kemper: *"Finde mir den Turbolader. Sofort."* | Verschachtelte `for`-Schleifen, Vergleich |
| 4.7 | Weissen Koenig verschieben | Teil umlagern: Teil an alter Position entfernen (`"0"` setzen), an neuer Position einlagern. Kemper: *"Der Turbolader muss in Regal 3-7, naeher an der Montagelinie."* | 2D-Zugriff, Position loeschen/setzen |

**Schwierigkeit:** 3-3.5/5

---

## Kapitel 5: "Code-Review" (Funktionale Programmierung)

**Briefing:** Die Systeme laufen. Die Fabrik produziert wieder. Aber Frau Kemper hat den Code gesichtet, den das Notfallteam in den letzten Wochen geschrieben hat - und ist nicht begeistert. Kemper: *"Euer Notfall-Code funktioniert. Aber funktionieren reicht nicht. Bevor die Investoren kommen, wird das sauber gemacht. Modular. Wartbar. Wenn ich hier jemanden einstelle, muss der das lesen koennen."*

**Kemper-Stimmung:** Mentor-Modus. Nicht mehr Krisenmodus, sondern Professionalisierung. Fordert Qualitaet ein, nicht nur Funktion.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 5.1 | Falscher Funktionsaufruf (falsche Argumente) | Roboterarm-Fehler: Der Aufruf der Roboterarm-Funktion schlaegt fehl. Warum? Falsche Anzahl Parameter. Kemper: *"Lest die Fehlermeldung. Die sagt euch genau was falsch ist."* | `def`, Parameter, `TypeError`, `NameError` |
| 5.2 | Debugger - Programmfluss verfolgen | Ablaufverfolgung: Mit dem Debugger durch die Maschinensteuerung steppen und den Programmfluss verstehen. Sequentieller Ablauf vs. Funktionsaufruf. | Debugger, Programmablauf |
| 5.3 | Taschenrechner als Funktion refactoren | Materialkalkulator 2.0: Den Kalkulator aus Kapitel 3 (Aufgabe 3.6) in eine Funktion `berechne_material(a, b, op)` refactoren. Kemper: *"Den gleichen Code an 5 Stellen? Das ist genau das Problem. Einmal schreiben, ueberall nutzen."* | `def`, `return`, Refactoring, Modularisierung |
| 5.4 | Dezimal zu Binaer | Fehlercodes entschluesseln: Die Maschinensteuerung gibt Fehlercodes als Dezimalzahlen aus, aber das technische Handbuch listet sie als Bitmasken (binaer). Funktion schreiben die konvertiert. Kontext: Industriesteuerungen nutzen tatsaechlich Bitmasken fuer Statusflags und Fehlercodes. | `while`, Liste, `insert()`, `//`, `%` |
| 5.5 | Datum/Zeit-Funktionen | Schichtprotokoll: Zwei Funktionen schreiben - `get_aktuelle_zeit()` gibt aktuelle Zeit zurueck, `zeit_ausgabe(zeit)` schreibt sie formatiert ins Schichtprotokoll. Kemper: *"Jede Aktion muss protokolliert werden. Mit Zeitstempel."* | `datetime`, Funktionen mit `return` |
| 5.6 | Variablengueligkeit local/global | Mysterioeser Bug: Eine Funktion soll zwei Maschinenwerte tauschen (z.B. Soll- und Ist-Temperatur), aber nach dem Aufruf sind sie unveraendert. Warum? Studierende analysieren lokale vs. globale Variablen. Kemper: *"Der Letzte der hier `global` benutzt hat, hat die ganze Linie lahmgelegt. Versteht warum."* | `global`, lokaler Scope, Parameterweitergabe |

**Hinweis:** `Z99_PIN_eingabe.ipynb` aus dem Original wird nicht uebernommen - es ist ein Fragment/Konzeptdemonstration zur Funktionssyntax, das durch die vollstaendigen Aufgaben 5.1a-e abgedeckt wird.

**Schwierigkeit:** 3.5/5

---

## Kapitel 6: "Investoren-Pitch" (Dateien, Pandas, Visualisierung)

**Briefing:** Die Fabrik laeuft wieder! Aber die Investoren wollen Beweise. Daten, Zahlen, Grafiken. Kemper: *"Morgen kommen die Geldgeber. Wenn die keine ueberzeugenden Daten sehen, war alles umsonst. Das ist eure letzte Mission."*

**Kemper-Stimmung:** Aufgeregt-motiviert. Weiss, dass alles auf dem Spiel steht. Am Ende: stolz.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 6.1 | Dateien lesen: Vokale in Beschreibung.txt zaehlen + Bar Chart | Qualitaetsbericht analysieren: Die alte Qualitaetsabteilung hat einen Textbericht hinterlassen (`Beschreibung.txt`). Zeile fuer Zeile einlesen, Vokale pro Zeile und gesamt zaehlen, als Balkendiagramm darstellen. Kemper: *"Irgendwo in diesem Bericht stecken die Infos die wir brauchen. Parst das."* | `open()`, `read()`, `readlines()`, `close()`, `str.count()`, `matplotlib` |
| 6.2 | Dateien schreiben: Leetspeak-Konverter | Notfall-Kodierung: Die Maschinenlogs muessen schnell unleserlich gemacht werden, bevor die Konkurrenz sie sieht. Einfache Zeichenersetzung (A->4, B->8, O->0 etc.) und in neue Datei schreiben. Kemper: *"Keine echte Verschluesselung, aber besser als Klartext auf dem Schreibtisch."* Expliziter Hinweis: Dies ist KEINE echte Kryptographie, nur String-Manipulation. | `open("w"/"a")`, `write()`, `replace()`-Ketten, `datetime` |
| 6.3 | Pandas: autos.csv + sales.csv | Produktionsdaten auswerten: `autos.csv` enthaelt die Daten aller produzierten Fahrzeuge. Filtern: Verbrauch < 6l/100km, nach CO2 sortieren, Durchschnittsverbrauch pro Marke. Plus `sales.csv`: Umsatz > 100 filtern, nach Stadt gruppieren, Durchschnittsumsatz berechnen. Kemper: *"Die Investoren wollen wissen: Was haben wir produziert? Was verkauft sich?"* | `pd.read_csv()`, `DataFrame`, Filter, `sort_values()`, `groupby()`, `mean()` |
| 6.4 | Plotly: 2D + 3D Visualisierung | Investor-Dashboard: Maschinentemperaturen aus `temperatures.csv` ueber Zeit als interaktive Plotly-Grafik, 3D-Scatter (Datum x Temperatur x Feuchtigkeit pro Standort). Kemper: *"Wenn die morgen reinkommen, will ich ein Dashboard das beeindruckt. Nicht Excel."* | `plotly.express.line()`, `scatter_3d()`, `pd.read_csv()`, Filter |

**Schwierigkeit:** 4/5

---

## Klausurvorbereitung: "Die Abschlusspruefung"

**Briefing:** Die Fabrik ist gerettet. Die Investoren haben unterschrieben. Kemper: *"Bevor ich euch Festvertraege anbiete, gibt es eine Abschlusspruefung. Zeigt mir dass ihr alles verstanden habt - nicht nur den Code, sondern auch die Theorie dahinter."*

Alle 11 Klausuraufgaben mit vollstaendigem Mapping:

| # | Original | Neu (Fabrik-Framing) | Typ |
|---|---|---|---|
| 1 | Was definiert ein Datentyp? Unterschied float/double | Kemper: *"Erklaert mir, warum unsere Sensoren zwischen `float` und `double` unterscheiden muessen."* Datentypen im Kontext Maschinensteuerung erklaeren. | Theorie |
| 2 | Fehler im Code finden (berechneSumme) | Notfall-Patch Teil 2: Funktion `berechneGesamtgewicht()` eines Mitarbeiters enthaelt Compiler- und Laufzeitfehler. Finden und klassifizieren. | Debugging |
| 3 | Definition "Algorithmus" + 4 Eigenschaften | Kemper: *"Wenn ihr einen Produktionsprozess als Algorithmus beschreiben muesst - was muss der erfuellen?"* Algorithmus-Definition am Beispiel eines Fertigungsschritts. | Theorie |
| 4 | Wie viele Werte mit 7 Bit? | Kemper: *"Unser Fehlercode-Register hat 7 Bit. Wie viele verschiedene Fehlercodes koennen wir damit darstellen?"* | Theorie/Berechnung |
| 5 | Von-Neumann-Zyklus skizzieren | Kemper: *"Die neue Steuerung basiert auf Von-Neumann-Architektur. Skizziert den Zyklus."* Theoriefrage bleibt abstrakt - der Fabrikbezug ist der Anlass, nicht der Inhalt. | Theorie |
| 6 | Warum ist `(ende != true)` redundant? Kuerzere Form | Kemper zeigt Code der alten Maschinensteuerung: `while (notaus_gedrueckt != True):`. *"Das hat der Vorgaenger geschrieben. Vereinfacht das."* | Theorie/Code |
| 7 | Programmablaufplan: Gebuehrenberechnung (gestaffelt) | Flussdiagramm: Versandkosten-Berechnung fuer MotoTec-Lieferungen. Gestaffelte Gebuehren je nach Anzahl Lieferungen pro Monat. | Flussdiagramm |
| 8 | Zahlensysteme: Dezimal/Binaer/Hex umrechnen (2015, F5D4hex, 10101101bin) | Maschinenregister-Werte: *"Wandelt diese Werte um - die alte Steuerung gibt dezimal aus, die neue braucht hex."* Gleiche Zahlen, Fabrik-Kontext. | Berechnung |
| 9 | For-Schleife: Zahlen im Bereich teilbar durch 5 UND 9 | Chargen-Nummern: Finde alle Chargennummern in einem Bereich, die sowohl durch 5 als auch durch 9 teilbar sind (= Pruefchargen). | Programmierung |
| 10 | Zahlenraten (Zufallszahl 1-100, "zu hoch/zu niedrig") | Fehlercode erraten: Die Maschine hat einen Fehler, der Code liegt zwischen 1 und 100. Kemper: *"Findet den Code. Das System sagt euch ob ihr zu hoch oder zu niedrig liegt."* | Programmierung |
| 11 | Optimierung: Rechteck-Flaeche ~75.5m², minimaler Umfang, 0.01m-Schritte | Materialzuschnitt optimieren: Eine Metallplatte soll moeglichst nah an 75.5m² sein bei minimalem Materialverschnitt (Umfang). Zwei Funktionen (Flaeche, Umfang), Iteration in 0.01m-Schritten. | Programmierung |

**Schwierigkeit:** 4-4.5/5

---

## Nicht uebernommene Inhalte

| Original-Notebook | Grund |
|---|---|
| `Z99_PIN_eingabe.ipynb` (Kap. 5) | Fragment/Konzeptdemo zur Funktionssyntax. Wird durch die vollstaendigen Aufgaben 5.1a-e abgedeckt. |
| `Getting_started_with_AAS.ipynb` (Klausurvorbereitung) | Spezialthema Asset Administration Shell (BaSyx SDK, Industry 4.0). Geht ueber den Informatik-I-Lehrplan hinaus. Kann spaeter als optionales Bonus-Notebook "MotoTec goes Digital Twin" ergaenzt werden. |

---

## NPC: Ingrid Kemper

### Charakter-Profil
- 30 Jahre Erfahrung in der Autoindustrie
- Pragmatisch, direkt, trockener Humor
- Hat alles schon gesehen, laesst sich nicht leicht beeindrucken

### Stimmungsentwicklung ueber das Semester
- **Kapitel 1-2:** Angespannt, knapp. Krisenmodus. *"Keine Zeit fuer Erklaerungen."*
- **Kapitel 3:** Fordernd, aber erste Anerkennung. *"Wird langsam."*
- **Kapitel 4:** Genervt ueber Altlasten, pragmatisch. *"Wer hat das hier so verkommen lassen?"*
- **Kapitel 5:** Mentor-Modus. Professionalisierung. *"Funktioniert ist nicht genug."*
- **Kapitel 6:** Aufgeregt, dann stolz. *"Ich wusste, dass ich mich auf euch verlassen kann."*

### Wiederkehrende Elemente
- Lobt gute Arbeit knapp: *"Laeuft."*
- Bei Fehlern: *"Schaut euch die Fehlermeldung an. Die luegt nicht."*
- Running Gag: *"In meiner ersten Fabrik hatten wir nicht mal Terminals..."*
- Bezieht sich in spaeteren Kapiteln auf fruehere Erfolge: *"Erinnert ihr euch an den Blackout? Dagegen ist das hier ein Kinderspiel."*

---

## Bestehende Dateien die wiederverwendet werden

- `autos.csv` -> Produktionsdaten der MotoTec GmbH (1000 Fahrzeuge: Marke, Modell, Baujahr, Verbrauch, CO2)
- `sales.csv` -> Verkaufsdaten der MotoTec-Fahrzeuge (Menge, Umsatz, Stadt)
- `temperatures.csv` -> Maschinentemperatur-Sensordaten (Maschine, Datum, Temperatur, Feuchtigkeit, Standort)
- `Temperaturverlauf.txt` -> 24h-Temperaturverlauf einer Maschine (24 Stundenwerte)
- `Beschreibung.txt` -> Alter Qualitaetsbericht (Inhalt kann an MotoTec-Kontext angepasst werden)
