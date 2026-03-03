# Mission MotoTec - Design-Dokument

## Konzept

Refactoring aller Informatik-I-Aufgaben zu einer durchgehenden Storyline: **"Mission MotoTec"**.

Die Studierenden sind IT-Notfallteam der **MotoTec GmbH**, einer Autofabrik nach IT-Totalausfall. Verschiedene Mitarbeiter - von der IT-Leiterin ueber den Schichtleiter bis zum Geschaeftsfuehrer - stellen die Aufgaben und begleiten die Rettung. Jede Aufgabe = ein konkretes Problem in der Fabrik, das geloest werden muss.

### Narrative Struktur pro Notebook

**Aufgaben-Notebook:**
1. **Briefing** (Markdown, 3-5 Saetze): Lage in der Fabrik
2. **Stakeholder-Dialog** (kursiv/zitiert): Konkrete Aufgabe und Motivation
3. **Aufgabe**: Programmieraufgabe im Fabrik-Kontext
4. **Leere Code-Zelle**: Platz fuer die Loesung der Studierenden

**Loesungs-Notebook (`_Lsg`):**
1. **Briefing** (identisch zur Aufgabe)
2. **Stakeholder-Dialog** (identisch zur Aufgabe)
3. **Aufgabe** (identisch zur Aufgabe)
4. **Loesungscode**: Vollstaendig kommentierte Musterloesung
5. **Debriefing** (nur hier, nicht in der Aufgabe): Der Stakeholder kommentiert das Ergebnis

### Format

Alle Aufgaben, Beispiele und Loesungen werden als **Jupyter Notebooks (.ipynb)** erstellt - identisch zum bestehenden Format.

### Loesungs-Notebooks

Fuer jede Aufgabe wird ein separates Loesungs-Notebook im Fabrik-Kontext erstellt (analog zu den bestehenden `_Lsg`-Notebooks). Die Loesung enthaelt denselben narrativen Rahmen (Briefing, Stakeholder-Dialog) plus vollstaendig kommentierte Musterloesung.

### Notebook-Granularitaet

**1 Notebook pro Aufgabe.** Jede Aufgabennummer (z.B. 1.1, 2.3, 3.6) ergibt genau ein Aufgaben-Notebook und ein separates Loesungs-Notebook. Keine Buendelung mehrerer Aufgaben in einem Notebook (anders als im Original, wo z.B. `04_Verzweigungen.ipynb` mehrere Aufgaben enthielt).

### Dateinamen-Konvention

**Ordnerstruktur:** Ein Ordner pro Kapitel, benannt nach Schema `{NN}_{Story}:{Thema}/`:

- `01_Blackout:Einfuehrung_IDE/`
- `02_Fehlkalibrierung:Variablen_Datentypen/`
- `03_Fertigungsstrasse:Operatoren_Kontrollstrukturen/`
- `04_Lagerchaos:Strings_Listen/`
- `05_Code_Review:Funktionale_Programmierung/`
- `06_Investoren_Pitch:Dateien_Pandas_Visualisierung/`
- `Klausurvorbereitung/`

**Dateinamen:** `{NN}_{Thema}_Aufgabe.ipynb` bzw. `{NN}_{Thema}_Loesung.ipynb`.

- `NN` = zweistellige laufende Nummer innerhalb des Kapitels (01, 02, ... 12)
- `Thema` = Kurzbezeichnung der Aufgabe in Snake_Case
- `_Aufgabe` / `_Loesung` als Suffix (sortiert alphabetisch korrekt: A vor L)

**Beispiele:**

| Aufgabe | Dateiname |
|---|---|
| 1.1 Aufgabe | `01_Blackout:Einfuehrung_IDE/01_Bootsequenz_Aufgabe.ipynb` |
| 1.1 Loesung | `01_Blackout:Einfuehrung_IDE/01_Bootsequenz_Loesung.ipynb` |
| 2.5 Aufgabe | `02_Fehlkalibrierung:Variablen_Datentypen/05_Werkzeugkasten_Aufgabe.ipynb` |
| 3.6 Aufgabe | `03_Fertigungsstrasse:Operatoren_Kontrollstrukturen/06_Materialkalkulator_Aufgabe.ipynb` |
| 4.8 Aufgabe | `04_Lagerchaos:Strings_Listen/08_NumPy_Sensor_Matrix_Aufgabe.ipynb` |
| 5.3 Aufgabe | `05_Code_Review:Funktionale_Programmierung/03_Materialkalkulator_2_0_Aufgabe.ipynb` |
| 6.4 Aufgabe | `06_Investoren_Pitch:Dateien_Pandas_Visualisierung/04_Investor_Dashboard_Plotly_Aufgabe.ipynb` |
| K-1 Aufgabe | `Klausurvorbereitung/01_Datentypen_Aufgabe.ipynb` |

### Original-Aufgaben (Legacy)

Die bisherigen Aufgaben, auf denen dieses Refactoring basiert: `/Users/ostfalia/vs-code/Informatik-I----Python-Beispiele/`

### Sprachkonventionen

- **Sie-Form:** Alle Aufgabentexte, Hinweise und Anleitungen verwenden die hoefliche Anrede ("Schreiben Sie...", "Verwenden Sie...", nicht "Schreib..." oder "Verwende...")
- **Kein Schwierigkeitsgrad in Notebooks:** Die Schwierigkeitsangabe (1/5 etc.) dient nur der internen Planung im Design-Dokument und erscheint NICHT in den Notebooks

### Akzeptanzkriterien

- Aufgaben machen Spass (Krimi-/Rettungsstory, Problemloesung als Motivation)
- Vermitteltes Wissen bleibt identisch (1:1-Mapping jeder Originalaufgabe)
- Schwierigkeitsgrad vergleichbar (gleiche Progression 1/5 -> 4/5)
- Sinnvolle Kontext-Integration (jedes Thema hat natuerlichen Grund in Fabrikrettung)

### TDD-Workflow fuer Notebook-Erstellung

Jedes Notebook durchlaeuft 3 Phasen:

1. **Red (Kriterien definieren):** Vor der Erstellung die Verifikations-Checkliste (siehe unten) fuer das spezifische Notebook ausfuellen. Aufgabenspezifische Kriterien aus der Kapitel-Tabelle ergaenzen (Konzepte, Stakeholder-Zitat, Original-Referenz).
2. **Green (Implementieren):** Notebook erstellen. Alle Checklisten-Punkte muessen erfuellt sein, bevor das Notebook als "fertig" gilt.
3. **Verify (Pruefen):** Notebook gegen die Checkliste abarbeiten. Erst wenn alle Punkte bestanden sind, wird der Status im Progress-Tracker auf [x] gesetzt.

### Verifikations-Checkliste (Template)

Universelle Checkliste - gilt fuer **jedes** Notebook:

**Struktur-Checks (Aufgaben-Notebook):**

- [ ] Dateiname folgt Konvention (`{NN}_{Thema}_Aufgabe.ipynb`)
- [ ] Liegt im korrekten Kapitel-Ordner (`{NN}_{Story}:{Thema}/`)
- [ ] Briefing vorhanden (Markdown, 3-5 Saetze, Fabrik-Situation)
- [ ] Stakeholder-Dialog vorhanden (kursiv/zitiert, konkrete Aufgabe + Motivation)
- [ ] Aufgabe klar formuliert (Programmieraufgabe im Fabrik-Kontext)
- [ ] Leere Code-Zelle mit Scaffolding-Kommentaren
- [ ] KEIN Debriefing (Debriefing gehoert nur in die Loesung)

**Inhalts-Checks:**

- [ ] Alle gelisteten Konzepte aus der Design-Tabelle werden abgedeckt
- [ ] Schwierigkeitsgrad passt zum Kapitel (siehe Kapitel-Header)
- [ ] Stakeholder passt zur Situation (siehe Story-Arc und Stakeholder-Cast)
- [ ] Keine Konzepte verwendet die erst in spaeteren Kapiteln eingefuehrt werden
- [ ] Sie-Form durchgehend verwendet (keine Du-Form in Aufgabentexten/Hinweisen)
- [ ] Kein Schwierigkeitsgrad im Notebook sichtbar
- [ ] Code-Zellen sind ausfuehrbar (kein `ImportError`, kein `SyntaxError`)

**Loesung-Checks (nur fuer `_Lsg`-Notebooks):**

- [ ] Separates Loesungs-Notebook existiert (`{NN}_{Thema}_Loesung.ipynb`)
- [ ] Selber narrativer Rahmen wie Aufgabe (Briefing, Stakeholder-Dialog, Aufgabentext)
- [ ] Vollstaendig kommentierte Musterloesung
- [ ] Debriefing vorhanden (Stakeholder kommentiert Ergebnis)
- [ ] Loesung ist korrekt und laeuft fehlerfrei

---

## Story-Arc

| Kapitel | Titel | Fabrik-Phase | Stimmung | Haupt-Stakeholder |
|---|---|---|---|---|
| 1 | Blackout | Systeme hochfahren | Hektisch, Dunkelheit, Grundlagen | Sandra Holz (IT-Leiterin) |
| 2 | Fehlkalibrierung | Sensoren reparieren | Methodisch, Diagnose | Dr. Lena Voss (Qualitaetsmanagerin) |
| 3 | Fertigungsstrasse ausser Kontrolle | Produktionslogik fixen | Aufbauend, Kernarbeit | Tarek Oezdal (Schichtleiter), Marco Petri (Einkauf) |
| 4 | Lagerchaos | Lager organisieren | Ordnung, Komplexitaet | Juergen Brandt (Lagerleiter) |
| 5 | Code-Review | Eigene Befehle fuer die Expansion | Aufbruch, Zukunft | Sandra Holz (IT-Leiterin), Thomas Wegner (GF) |
| 6 | Investoren-Pitch | Daten auswerten, Fabrik retten | Finale, Triumph | Thomas Wegner (GF), Aylin Demir (CFO) |

---

## Kapitel 1: "Blackout" (IDE-Einfuehrung)

**Briefing:** Die Fabrikhalle ist dunkel. Kein System reagiert. Sandra Holz, die IT-Leiterin, steht mit Taschenlampe am Hauptterminal.

**Stakeholder:** Sandra Holz (IT-Leiterin). Angespannt und knapp. Keine Zeit fuer Smalltalk.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 1.1 | Hello World, Begruessung (Original enthaelt auch `def`/`return` - wird hier bewusst entfernt, da Funktionen erst Kapitel 5) | Terminal hochfahren: Bootsequenz, Techniker-Name eingeben, Statusmeldung ausgeben. Rein prozedural, keine Funktionen. Holz: *"Keine Zeit fuer Erklaerungen. Terminal an."* | `print()`, `input()`, Strings |
| 1.2 | Zwei Zahlen eingeben & addieren | Stromversorgung pruefen: Spannungswerte per `input()` eingeben, String-Problem entdecken. Holz: *"Die Spannungswerte muessen stimmen, sonst fliegt uns die Sicherung."* | `input()`, `int()`, String vs. Integer |
| 1.3 | Steuerzeichen | Statusanzeige reparieren: Ein ASCII-Art-Dashboard mit Escape-Zeichen formatieren, Ladebalken mit `\r` fuer Systemstart. Holz: *"Die Statusanzeige muss lesbar sein. Formatiert das sauber."* | `\n`, `\t`, `\r`, `\b`, `print(end="")` |
| 1.4 | Escape-Zeichen Aufgabe | System-Dashboard: Fabriksystem-Uebersicht (Strom/Wasser/Netzwerk je mit Status) als formatiertes ASCII-Layout mit `\t` und `\n` in einem einzigen `print()` ausgeben. Holz: *"Ich brauch eine Uebersicht aller Systeme. Auf einen Blick."* | `\t`, `\n`, Formatierung |

**Schwierigkeit:** 1/5

**Debriefing-Beispiel:** Holz: *"Terminal laeuft. Erster Schritt geschafft. Aber das war der einfache Teil."*

---

## Kapitel 2: "Fehlkalibrierung" (Variablen & Datentypen)

**Briefing:** Terminal laeuft, aber Sensoren liefern falsche Werte. Temperatur als Text, negative Drehzahlen. Irgendjemand hat die Konfiguration verhunzt. Dr. Lena Voss von der Qualitaetssicherung uebernimmt.

**Stakeholder:** Dr. Lena Voss (Qualitaetsmanagerin). Systematisch-analytisch. *"Eins nach dem anderen."*

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 2.1 | Auskommentieren, Dokumentation | Maschinendiagramm bereinigen: Ein `matplotlib`-Plot zeigt Maschinendaten, aber mit falschen/ueberfluessigen Elementen (z.B. Testdaten, falsche Achsenbeschriftung, Debug-Linie). Durch gezieltes Auskommentieren bestimmter Code-Zeilen veraendert sich die Grafik - Studierende sehen visuell den Effekt von Kommentaren. Plus: Code-Dokumentation mit Header-Kommentar. Voss: *"Das Diagramm ist unbrauchbar - Testdaten, falsche Achsen, Debug-Reste. Raumt das auf und dokumentiert was ihr gemacht habt."* | `#`, mehrzeilige Kommentare, Doku-Header, visuelles Feedback durch `matplotlib` |
| 2.2 | Datentyp aendert sich | Warum spinnt der Sensor? Variable `drehzahl` ist `int`, nach Division durch Korrekturfaktor ploetzlich `float`. Studierende untersuchen mit `type()` warum die Weiterverarbeitung fehlschlaegt. | `type()`, `int`/`float`, implizite Typaenderung |
| 2.3 | Variablen-Beispiele | Maschinenpass rekonstruieren: Maschinendatenbank ist weg. Variablen neu anlegen: `maschinen_id = 1042` (int), `max_temp = 85.5` (float), `bezeichnung = "Presswerk Alpha"` (str) | Variablen, `int`, `float`, `str` |
| 2.4 | Explizite Typumwandlung | Sensordaten reparieren: Temperatursensor liefert `"72.4"` als String. Damit kann nicht gerechnet werden. Problem finden, explizit konvertieren. | `float()`, `int()`, `str()`, `type()` |
| 2.5 | Bibliotheken: math, random, time (Demo) | Werkzeugkasten aktivieren (Demo-Notebook): `math.sqrt()` fuer Toleranzberechnung, `random.randint()` fuer Testsimulation, `time.sleep()` + `time.strftime()` fuer Logeintraege mit Zeitstempel. Reines Demonstrations-Notebook, keine Aufgabe. | `import`, `math`, `random`, `time` |
| 2.6 | Neu | QR-Code Maschinenetikett: Alle Etiketten sind nach dem Crash weg. Programm nimmt Maschinenname, ID und Leistung (kW) per `input()` entgegen, berechnet den Tagesverbrauch (Leistung * Betriebsstunden, aufgerundet mit `math.ceil()`) und generiert einen QR-Code mit allen Daten als Bild im Notebook. Studierende koennen ihn mit dem Handy scannen und sehen die einkodierten Maschinendaten. Voss: *"Jede Maschine braucht ein neues Etikett. Mit QR-Code - ein Scan und man hat alle Daten."* Benoetigt: `pip install qrcode[pil]`. | `import qrcode`, `math.ceil()`, `input()`, `float()`, f-Strings |
| 2.7 | Neu | QR-Code mit Pruefpause: Programm aus 2.6 erweitern - bevor der QR-Code generiert wird, zeigt das Programm erst alle berechneten Werte als Klartext an und wartet 3 Sekunden, damit der Techniker die Daten pruefen kann. Erst danach wird der QR-Code erzeugt. Voss: *"Erst pruefen, dann drucken. Ich hab keine Lust nochmal 500 falsche Etiketten wegzuschmeissen."* | `time.sleep()` |
| 2.8 | Neu | QR-Code mit Zeitstempel: Programm aus 2.7 erweitern - der QR-Code enthaelt zusaetzlich den Erstellungszeitpunkt. Beim Scannen sieht man wann das Etikett generiert wurde. Voss: *"Ich will auf jedem Etikett sehen WANN es erstellt wurde. Sonst weiss keiner ob die Daten noch aktuell sind."* | `time.strftime()`, `time.localtime()` |
| 2.9 | Zufallszahlen plotten | Stresstest: Maschine laeuft wieder, aber ist sie stabil? 10 simulierte Temperaturwerte (random 50-90) ueber die Zeit messen und plotten. Voss: *"Zeigt mir ob die Temperatur stabil bleibt oder ob wir ein Problem haben."* | `random`, `matplotlib`, `while`, `time.sleep()` |

**Hinweis zu 2.1:** Der `matplotlib`-Code ist in dieser Aufgabe komplett vorgegeben. Studierende veraendern die Grafik ausschliesslich durch Aus-/Einkommentieren von Code-Zeilen, schreiben keinen eigenen Plot-Code. Die formale Einfuehrung von Bibliotheken (inkl. `import`) erfolgt in 2.5; in 2.9 nutzen Studierende `matplotlib` dann erstmals selbst.

**Schwierigkeit:** 1.5/5

---

## Kapitel 3: "Fertigungsstrasse ausser Kontrolle" (Operatoren & Kontrollstrukturen)

**Briefing:** Maschinen laufen, aber Fertigungslogik ist zerschossen. Autos werden falsch sortiert, Qualitaetskontrolle winkt alles durch, Roboter arbeiten in Endlosschleifen. Oezdal: *"Das hier ist das Herzstueck der Fabrik. Wenn die Steuerungslogik nicht stimmt, produzieren wir Schrott."*

**Stakeholder:** Tarek Oezdal (Schichtleiter Produktion). Fordernd, erkennt aber auch gute Arbeit an. Dazu: Marco Petri (Einkauf), Sandra Holz (IT), Aylin Demir (Finanzen) fuer Spezialthemen.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 3.1 | Neu (aus Vorlesungs-Pattern) | Fabrikzugangssystem: Das Sicherheitssystem ist nach dem IT-Ausfall offline. Notfall-Zugangskontrolle programmieren. (a) Einfache Passwort-Abfrage mit `while`. (b) Max 5 Fehlversuche, danach Sperre. (c) Verbleibende Versuche anzeigen. (d) Nach der Schleife: "Zugang gewaehrt" oder "System gesperrt". Holz: *"Ohne Zugangskontrolle kommt hier jeder rein. Das aendern wir sofort."* | `while`, `!=`, Zaehler, `if/else` nach Schleife, f-Strings |
| 3.2 | Quersumme, teilbar-durch-5, kombinierte Bedingung | Seriennummer-Pruefung: 3-stellige Auto-Seriennummer eingeben. (a) Quersumme berechnen (Pruefziffer). (b) Teilbar durch 5? -> Sondermodell. (c) Teilbar durch 5 UND > 100? -> Exportmodell. Voss: *"Jede Seriennummer muss pruefbar sein. Ohne Pruefziffer geht hier nichts raus."* | `//`, `%`, `if/else`, `and`, `int(input())` |
| 3.3 | Operatorrangfolge vorhersagen | Fehldiagnose Sortiermaschine: Die Sortierlogik enthaelt komplexe Bedingungen. Studierende muessen vorhersagen was die Maschine tut, BEVOR sie den Code ausfuehren. Oezdal: *"Die Sortiermaschine schickt SUVs in die Kleinwagen-Spur. Schaut euch die Bedingungen an."* | Operatorrangfolge, `**`, `//`, `%`, `and`/`or` |
| 3.4 | if/elif Verhalten + Einrueckung | Roboterarm-Steuerung debuggen: Verschachtelte `if/elif`-Ketten steuern den Roboterarm. Warum greift er daneben? Code-Verhalten vorhersagen, Einrueckungsfehler finden. Oezdal: *"Der Roboterarm greift seit heute morgen daneben. Findet raus warum."* | `if/elif/else`, Einrueckung |
| 3.5 | Magic 8-Ball | Diagnose-Automat: Die alte CNC-Maschine hat ein fehlerhaftes Diagnosemodul - statt einer echten Analyse gibt sie je nach Zufallszahl eine von 8 vordefinierten Statusmeldungen aus (z.B. "Lager verschlissen - Austausch empfohlen", "Temperatur im Grenzbereich - Kuehlung pruefen", "Kalibrierung erforderlich", "System arbeitet nominal", "Sensor defekt - manuelle Pruefung noetig"). Studierende bauen die Zufallsauswahl per `if/elif`-Kette nach. Oezdal: *"Das Diagnosemodul spuckt Zufallsmeldungen aus statt echter Analyse. Baut das nach, damit wir verstehen wie die Logik funktioniert - und warum sie versagt."* | `random.randint()`, `if/elif` |
| 3.6 | Taschenrechner | Materialkalkulator: Zwei Materialmengen und eine Rechenoperation eingeben (+, -, *, /). Petri: *"Ich brauch ein Tool um Materialbedarfe schnell zu berechnen."* | `input()`, `if/elif`, Arithmetik |
| 3.7 | Schere-Stein-Papier-Echse-Spock | Werkzeug-Duell: Bei Schichtzuteilung gibt es regelmaessig Streit - wer kriegt die begehrte Fruehschicht? Oezdal hat ein faires Zufallssystem eingefuehrt: Zwei Techniker waehlen je ein Werkzeug (Schraubenschluessel, Schaltplan, Sicherung, Kabel, Multimeter - 5 Optionen, asymmetrische Regeln, identische Spielmechanik wie Schere-Stein-Papier-Echse-Spock). Der Computer wertet aus und entscheidet. Oezdal: *"Diskussionen ueber Schichtzuteilung kosten mich jeden Montag eine halbe Stunde. Ab jetzt entscheidet das System."* | `random`, verschachtelte Bedingungen, Spiellogik |
| 3.8 | break/continue vorhersagen | Fliessband-Steuerung analysieren: Code-Snippets mit `break`/`continue` in einer Fliessband-Schleife. Welche Autos werden uebersprungen? Wann stoppt das Band? Oezdal: *"Das Band ueberspringt Autos und stoppt ohne Grund. Schaut euch die Steuerung an."* | `break`, `continue` |
| 3.9 | Alle Teiler einer Zahl | Schichtplanung: Oezdal: *"Wir haben X Mitarbeiter. In wie viele gleichgrosse Teams kann ich die aufteilen?"* Alle ganzzahligen Teiler berechnen. | `for`, `range()`, `%` |
| 3.10 | Wie oft durch 2 teilbar | Halbierungsmaschine: Ein Stahlblock wird wiederholt halbiert. Wie oft kann man halbieren, bis er nicht mehr teilbar ist? Oezdal: *"Wie duenn koennen wir das Blech schneiden? Rechnet das aus."* | `while`, `//`, Zaehler |
| 3.11 | Zinsberechnung (Sparen ueber 50 Jahre, 7%) | Ruecklagen-Rechner: MotoTec legt monatlich Geld fuer neue Maschinen zurueck. Wie entwickelt sich das Kapital ueber 50 Jahre bei 7% jaehrlicher Rendite? Mit Eingabevalidierung fuer die monatliche Rate (50-300 EUR). Demir: *"Rechnet mir das durch, bevor ich zur Bank gehe."* WICHTIG: Mathematik identisch zum Original = Kapitalaufbau durch regelmaessiges Sparen, NICHT Kredit-Tilgung. | `while`, Zinseszins, Eingabevalidierung |
| 3.12 | Debugger (Primzahlen mit Fehlern) | Notfall-Patch: Ein ehemaliger Mitarbeiter hat eine Funktion zur Chargenprufung geschrieben - voller Bugs (C-Syntax wie `int n =`, fehlender Doppelpunkt, `=` statt `==`, falscher Zaehler). Holz: *"Der Typ hat Java programmiert, kein Python. Findet alle Fehler."* Story minimal halten, Fokus auf Fehlersuche. | Syntax-/Logikfehler, Debugging, `while`, `if`, `%` |

**Schwierigkeit:** 2.5-3/5

---

## Kapitel 4: "Lagerchaos" (Strings & Listen)

**Briefing:** Die Produktion laeuft halbwegs, aber das Lager ist eine Katastrophe. Etiketten falsch, Regale durcheinander, niemand weiss wo was steht. Brandt: *"Bevor wir ausliefern koennen, muss das Lager stimmen. Jedes Teil, jedes Regal, alles muss inventarisiert und auffindbar sein."*

**Stakeholder:** Juergen Brandt (Lagerleiter). Genervt ueber das Chaos, ueberfordert aber herzlich. *"Da drin sieht's aus wie Kraut und Rueben."*

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 4.1 | String-Ops: "Strauss, & Co., Levi" -> "Levi Strauss & Co." rekonstruieren | Etiketten reparieren: Zulieferer-Datenbank hat fehlerhafte Eintraege. Aus `"GmbH, MotoTec, Zulieferer"` den korrekten Namen `"MotoTec Zulieferer GmbH"` rekonstruieren (Slicing, Reordering) plus `replace("ae", "ä")` fuer Umlaute. Petri: *"Die Zulieferer-Datenbank ist Muell. Repariert die Eintraege."* | String-Indexing, Slicing, `len()`, `find()`, `replace()` |
| 4.2 | 1D-Listen Aufgabe 7_1: 4 Automarken-Variablen -> Liste | Teilelager digitalisieren: Vier einzelne Teile-Variablen (`teil1 = "Kolben"` etc.) in eine Liste ueberfuehren und ausgeben. Brandt: *"Einzelne Zettel am Regal sind vorbei. Ab jetzt digitale Inventarliste."* | `list`, `for x in list`, `print()` |
| 4.3 | 1D-Listen Aufgabe 7_2: Erstes Element loeschen, zweites per Eingabe ersetzen | Teilelager bearbeiten: Erstes Teil wurde verbaut -> loeschen. Zweites Teil ist falsch erfasst -> per `input()` korrigieren. Brandt: *"Kolben ist verbaut, kann raus. Und die Dichtung ist falsch erfasst - korrigiert das."* | `pop()`, `remove()`, Indexing, `input()` |
| 4.4 | 1D-Listen Aufgabe 7_3: Funktion zum Suchen und Ersetzen in Liste | Teilelager durchsuchen: Funktion schreiben die ein Teil im Lager sucht und gegen ein neues ersetzt. Brandt: *"Wenn der Zulieferer wechselt, muessen wir alle Teile dieses Typs umbuchen."* | `index()`, Funktion, `for`-Schleife, Listen-Methoden |
| 4.5 | 2D-Listen: Schachbrett interaktiv befuellen | Lagerhalle als 8x8-Raster: Die Lagerhalle hat 8 Reihen mit je 8 Regalplaetzen. Teile interaktiv einlagern (Typ + Reihe + Spalte eingeben). Nach jeder Einlagerung: Lagerplan anzeigen. Brandt: *"Ich brauch ein System wo ich sehe was wo liegt. Reihe, Platz, Teil."* | 2D-Listen, List-Comprehension, verschachtelte `for`, `while`, `input()`, `clear_output()` |
| 4.6 | Weissen Koenig finden | Teil suchen: Wo steht ein bestimmtes Teil im Lager? Mit verschachtelten Schleifen das gesamte Raster durchsuchen. Brandt: *"Finde mir den Turbolader. Sofort."* | Verschachtelte `for`-Schleifen, Vergleich |
| 4.7 | Weissen Koenig verschieben | Teil umlagern: Teil an alter Position entfernen (`"0"` setzen), an neuer Position einlagern. Brandt: *"Der Turbolader muss in Regal 3-7, naeher an der Montagelinie."* | 2D-Zugriff, Position loeschen/setzen |
| 4.8 | Neu (aus Vorlesungsstoff NumPy) | NumPy Sensor-Matrix: Die Sensordaten der Fabrik muessen effizient verarbeitet werden. (a) 8x8 Array mit `np.full()` initialisieren (Soll-Temperaturen aller Maschinen). (b) Eine Maschinenreihe ueberhitzt - Zeile per Broadcasting auf Alarm-Wert setzen. (c) Differenz Soll vs Ist berechnen (element-weise Arithmetik). (d) Copy-Aufgabe: Was passiert bei `b = a` vs `b = a.copy()`? Voss: *"Mit Listen dauert die Auswertung zu lange. Wir brauchen etwas Schnelleres."* | `import numpy as np`, `np.array()`, `np.full()`, `np.zeros()`, Zeilen/Spalten-Zugriff, Broadcasting, `.copy()`, element-weise Arithmetik |

**Schwierigkeit:** 3-3.5/5

---

## Kapitel 5: "Code-Review" (Funktionale Programmierung)

**Briefing:** Die Produktion laeuft, das Lager ist sortiert. Naechste Woche kommen die Investoren. Wenn die zusagen, wird MotoTec expandieren - drei Werke statt einem. Aber der bisherige Code ist Einweg-Code: fest verdrahtet, nicht uebertragbar. Holz: *"Euer Code muss in drei Werken laufen, nicht nur hier. Bisher habt ihr Befehle benutzt die andere geschrieben haben: `print()`, `input()`, `math.sqrt()`. Ab heute schreibt ihr eure eigenen. Befehle die so gut sind, dass sie ueberall funktionieren."*

**Stakeholder:** Sandra Holz (IT-Leiterin) fuer Code-Qualitaet, Thomas Wegner (GF) fuer die strategische Perspektive. *"Wir bauen jetzt nicht fuer heute, sondern fuer morgen."*

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 5.1 | Falscher Funktionsaufruf (falsche Argumente) | Roboterarm-Fehler: Der Aufruf der Roboterarm-Funktion schlaegt fehl. Warum? Falsche Anzahl Parameter. Holz: *"Lest die Fehlermeldung. Die sagt euch genau was falsch ist."* | `def`, Parameter, `TypeError`, `NameError` |
| 5.2 | Debugger - Programmfluss verfolgen | Ablaufverfolgung: Mit dem Debugger durch die Maschinensteuerung steppen und den Programmfluss verstehen. Sequentieller Ablauf vs. Funktionsaufruf. Holz: *"Ihr muesst verstehen was der Code tut, nicht nur dass er laeuft. Steppt da durch."* | Debugger, Programmablauf |
| 5.3 | Taschenrechner als Funktion refactoren | Materialkalkulator 2.0: Den Kalkulator aus Kapitel 3 (Aufgabe 3.6) in eine Funktion `berechne_material(a, b, op)` refactoren. Holz: *"Den gleichen Code an 5 Stellen? Das ist genau das Problem. Einmal schreiben, ueberall nutzen."* | `def`, `return`, Refactoring, Modularisierung |
| 5.4 | Dezimal zu Binaer | Fehlercodes entschluesseln: Die Maschinensteuerung gibt Fehlercodes als Dezimalzahlen aus, aber das technische Handbuch listet sie als Bitmasken (binaer). Funktion schreiben die konvertiert. Kontext: Industriesteuerungen nutzen tatsaechlich Bitmasken fuer Statusflags und Fehlercodes. Holz: *"Das Handbuch spricht binaer, die Steuerung spricht dezimal. Schreibt mir einen Uebersetzer."* | `while`, Liste, `insert()`, `//`, `%` |
| 5.5 | Datum/Zeit-Funktionen | Schichtprotokoll: Zwei Funktionen schreiben - `get_aktuelle_zeit()` gibt aktuelle Zeit zurueck, `zeit_ausgabe(zeit)` schreibt sie formatiert ins Schichtprotokoll. Holz: *"Jede Aktion muss protokolliert werden. Mit Zeitstempel."* | `datetime`, Funktionen mit `return` |
| 5.6 | Variablengueligkeit local/global | Mysterioeser Bug: Eine Funktion soll zwei Maschinenwerte tauschen (z.B. Soll- und Ist-Temperatur), aber nach dem Aufruf sind sie unveraendert. Warum? Studierende analysieren lokale vs. globale Variablen. Holz: *"Der Letzte der hier `global` benutzt hat, hat die ganze Linie lahmgelegt. Versteht warum."* | `global`, lokaler Scope, Parameterweitergabe |

**Hinweis:** `Z99_PIN_eingabe.ipynb` aus dem Original wird nicht uebernommen - es ist ein Fragment/Konzeptdemonstration zur Funktionssyntax, das durch die vollstaendigen Aufgaben 5.1-5.6 abgedeckt wird.

**Schwierigkeit:** 3.5/5

---

## Kapitel 6: "Investoren-Pitch" (Dateien, Pandas, Visualisierung)

**Briefing:** Die Fabrik laeuft wieder! Aber die Investoren wollen Beweise. Daten, Zahlen, Grafiken. Wegner: *"Morgen kommen die Geldgeber. Wenn die keine ueberzeugenden Daten sehen, war alles umsonst. Das ist eure letzte Mission."*

**Stakeholder:** Thomas Wegner (GF) und Aylin Demir (CFO). Aufgeregt-motiviert. Alles steht auf dem Spiel.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 6.1 | Dateien lesen: Vokale in Beschreibung.txt zaehlen + Bar Chart | Qualitaetsbericht analysieren: Die alte Qualitaetsabteilung hat einen Textbericht hinterlassen (`Beschreibung.txt`). Zeile fuer Zeile einlesen, Vokale pro Zeile und gesamt zaehlen, als Balkendiagramm darstellen. Voss: *"Irgendwo in diesem Bericht stecken die Infos die wir brauchen. Parst das."* | `open()`, `read()`, `readlines()`, `close()`, `str.count()`, `matplotlib` |
| 6.2 | Dateien schreiben: Leetspeak-Konverter | Notfall-Kodierung: Die Maschinenlogs muessen schnell unleserlich gemacht werden, bevor die Konkurrenz sie sieht. Einfache Zeichenersetzung (A->4, B->8, O->0 etc.) und in neue Datei schreiben. Holz: *"Keine echte Verschluesselung, aber besser als Klartext auf dem Schreibtisch."* Expliziter Hinweis: Dies ist KEINE echte Kryptographie, nur String-Manipulation. | `open("w"/"a")`, `write()`, `replace()`-Ketten, `datetime` |
| 6.3 | Pandas: autos.csv + sales.csv | Produktionsdaten auswerten: `autos.csv` enthaelt die Daten aller produzierten Fahrzeuge. Filtern: Verbrauch < 6l/100km, nach CO2 sortieren, Durchschnittsverbrauch pro Marke. Plus `sales.csv`: Umsatz > 100 filtern, nach Stadt gruppieren, Durchschnittsumsatz berechnen. Demir: *"Die Investoren wollen wissen: Was haben wir produziert? Was verkauft sich?"* | `pd.read_csv()`, `DataFrame`, Filter, `sort_values()`, `groupby()`, `mean()` |
| 6.4 | Plotly: 2D + 3D Visualisierung | Investor-Dashboard: Maschinentemperaturen aus `temperatures.csv` ueber Zeit als interaktive Plotly-Grafik, 3D-Scatter (Datum x Temperatur x Feuchtigkeit pro Standort). Wegner: *"Wenn die morgen reinkommen, will ich ein Dashboard das beeindruckt. Nicht Excel."* | `plotly.express.line()`, `scatter_3d()`, `pd.read_csv()`, Filter |
| 6.5 | Neu (aus Vorlesungsstoff Matplotlib) | Produktions-Dashboard: Alle wichtigen Kennzahlen auf einen Blick fuer die Investoren. (a) Balkendiagramm: Produktion pro Marke aus `autos.csv`. (b) Streudiagramm: Verbrauch vs CO2 mit Farbe pro Marke. (c) Histogramm: Verteilung der Baujahre. (d) Alles als Subplots in einem Figure, gespeichert als `dashboard.png`. Wegner: *"Die Investoren wollen alles auf einer Seite sehen. Ein Bild, alle Zahlen."* | `plt.bar()`, `plt.scatter()`, `plt.hist()`, `plt.subplot()`, `plt.tight_layout()`, `plt.savefig()`, `plt.legend()` |

**Schwierigkeit:** 4/5

---

## Klausurvorbereitung: "Die Abschlusspruefung"

**Briefing:** Die Fabrik ist gerettet. Die Investoren haben unterschrieben. Wegner: *"Bevor ich euch Festvertraege anbiete, gibt es eine Abschlusspruefung. Zeigt mir dass ihr alles verstanden habt - nicht nur den Code, sondern auch die Theorie dahinter."*

Alle 11 Klausuraufgaben mit vollstaendigem Mapping:

| # | Original | Neu (Fabrik-Framing) | Typ |
|---|---|---|---|
| 1 | Was definiert ein Datentyp? Unterschied float/double | Voss: *"Erklaert mir, warum unsere Sensoren zwischen `float` und `double` unterscheiden muessen."* Datentypen im Kontext Maschinensteuerung erklaeren. | Theorie |
| 2 | Fehler im Code finden (berechneSumme) | Notfall-Patch Teil 2: Funktion `berechneGesamtgewicht()` eines Mitarbeiters enthaelt Compiler- und Laufzeitfehler. Finden und klassifizieren. Holz: *"Schon wieder fehlerhafter Code. Findet die Bugs und sagt mir welche Kategorie."* | Debugging |
| 3 | Definition "Algorithmus" + 4 Eigenschaften | Holz: *"Wenn ihr einen Produktionsprozess als Algorithmus beschreiben muesst - was muss der erfuellen?"* Algorithmus-Definition am Beispiel eines Fertigungsschritts. | Theorie |
| 4 | Wie viele Werte mit 7 Bit? | Holz: *"Unser Fehlercode-Register hat 7 Bit. Wie viele verschiedene Fehlercodes koennen wir damit darstellen?"* | Theorie/Berechnung |
| 5 | Von-Neumann-Zyklus skizzieren | Holz: *"Die neue Steuerung basiert auf Von-Neumann-Architektur. Skizziert den Zyklus."* Theoriefrage bleibt abstrakt - der Fabrikbezug ist der Anlass, nicht der Inhalt. | Theorie |
| 6 | Warum ist `(ende != true)` redundant? Kuerzere Form | Holz zeigt Code der alten Maschinensteuerung: `while (notaus_gedrueckt != True):`. *"Das hat der Vorgaenger geschrieben. Vereinfacht das."* | Theorie/Code |
| 7 | Programmablaufplan: Gebuehrenberechnung (gestaffelt) | Flussdiagramm: Versandkosten-Berechnung fuer MotoTec-Lieferungen. Gestaffelte Gebuehren je nach Anzahl Lieferungen pro Monat. Petri: *"Zeichnet mir den Ablauf auf. Ich will sehen wie die Staffelung funktioniert."* | Flussdiagramm |
| 8 | Zahlensysteme: Dezimal/Binaer/Hex umrechnen (2015, F5D4hex, 10101101bin) | Maschinenregister-Werte: Holz: *"Wandelt diese Werte um - die alte Steuerung gibt dezimal aus, die neue braucht hex."* Gleiche Zahlen, Fabrik-Kontext. | Berechnung |
| 9 | For-Schleife: Zahlen im Bereich teilbar durch 5 UND 9 | Chargen-Nummern: Finde alle Chargennummern in einem Bereich, die sowohl durch 5 als auch durch 9 teilbar sind (= Pruefchargen). Voss: *"Die Pruefchargen muessen raus. Welche Nummern sind das?"* | Programmierung |
| 10 | Zahlenraten (Zufallszahl 1-100, "zu hoch/zu niedrig") | Fehlercode erraten: Die Maschine hat einen Fehler, der Code liegt zwischen 1 und 100. Oezdal: *"Findet den Code. Das System sagt euch ob ihr zu hoch oder zu niedrig liegt."* | Programmierung |
| 11 | Optimierung: Rechteck-Flaeche ~75.5m², minimaler Umfang, 0.01m-Schritte | Materialzuschnitt optimieren: Eine Metallplatte soll moeglichst nah an 75.5m² sein bei minimalem Materialverschnitt (Umfang). Zwei Funktionen (Flaeche, Umfang), Iteration in 0.01m-Schritten. Petri: *"Jeder Zentimeter Verschnitt kostet Geld. Optimiert das."* | Programmierung |

**Schwierigkeit:** 4-4.5/5

---

## Nicht uebernommene Inhalte

| Original-Notebook | Grund |
|---|---|
| `Z99_PIN_eingabe.ipynb` (Kap. 5) | Fragment/Konzeptdemo zur Funktionssyntax. Wird durch die vollstaendigen Aufgaben 5.1-5.6 abgedeckt. |
| `Getting_started_with_AAS.ipynb` (Klausurvorbereitung) | Spezialthema Asset Administration Shell (BaSyx SDK, Industry 4.0). Geht ueber den Informatik-I-Lehrplan hinaus. Kann spaeter als optionales Bonus-Notebook "MotoTec goes Digital Twin" ergaenzt werden. |

---

## Stakeholder-Cast

| Name | Rolle | Tonfall | Typische Kapitel |
|---|---|---|---|
| **Sandra Holz** | IT-Leiterin | Technisch versiert, fordert sauberen Code, knapp | Kap 1, 3 (IT-Security), 5, 6 |
| **Dr. Lena Voss** | Qualitaetsmanagerin | Praezise, analytisch, duldet keine Schlamperei | Kap 2, 3 (QM), 4 (Sensoren), 6 |
| **Tarek Oezdal** | Schichtleiter Produktion | Hands-on, ungeduldig, will dass Dinge laufen | Kap 3, Klausur |
| **Juergen Brandt** | Lagerleiter | Ueberfordert, genervt ueber Chaos, aber herzlich | Kap 4 |
| **Marco Petri** | Einkaufsleiter | Zahlenmensch, pragmatisch | Kap 3 (Material), Kap 4 (Zulieferer) |
| **Aylin Demir** | CFO / Finanzchefin | Nuechtern, ergebnisorientiert, Druck von oben | Kap 3 (Ruecklagen), Kap 6 |
| **Thomas Wegner** | Geschaeftsfuehrer | Visionaer, motivierend, steht unter Druck | Kap 5 (Strategie), Kap 6, Klausur |

### Stimmungsentwicklung ueber das Semester
- **Kapitel 1-2:** Krisenmodus. Holz und Voss kaempfen um die Grundlagen. *"Keine Zeit fuer Erklaerungen."*
- **Kapitel 3:** Oezdal fordert Tempo, erste Anerkennung. *"Wird langsam."*
- **Kapitel 4:** Brandt ist genervt ueber Altlasten. *"Wer hat das hier so verkommen lassen?"*
- **Kapitel 5:** Holz bereitet die Expansion vor. *"Ab heute schreibt ihr eure eigenen Befehle."*
- **Kapitel 6:** Wegner motiviert fuer den Pitch. *"Ich wusste, dass ich mich auf euch verlassen kann."*

---

## Progress-Tracker

Legende: `[ ]` = offen, `[x]` = erledigt

### Kapitel 1: Blackout (4 Aufgaben)

| # | Thema | Dateiname | Aufgabe | Loesung | Verifiziert |
|---|---|---|---|---|---|
| 1.1 | Bootsequenz | `01_Bootsequenz` | [ ] | [ ] | [ ] |
| 1.2 | Stromversorgung | `02_Stromversorgung` | [ ] | [ ] | [ ] |
| 1.3 | Statusanzeige | `03_Statusanzeige` | [ ] | [ ] | [ ] |
| 1.4 | System-Dashboard | `04_System_Dashboard` | [ ] | [ ] | [ ] |

### Kapitel 2: Fehlkalibrierung (9 Aufgaben)

| # | Thema | Dateiname | Aufgabe | Loesung | Verifiziert |
|---|---|---|---|---|---|
| 2.1 | Maschinendiagramm | `01_Maschinendiagramm` | [ ] | [ ] | [ ] |
| 2.2 | Sensortypen | `02_Sensortypen` | [ ] | [ ] | [ ] |
| 2.3 | Maschinenpass | `03_Maschinenpass` | [ ] | [ ] | [ ] |
| 2.4 | Sensordaten reparieren | `04_Sensordaten_reparieren` | [ ] | [ ] | [ ] |
| 2.5 | Werkzeugkasten (Demo) | `05_Werkzeugkasten` | [ ] | [ ] | [ ] |
| 2.6 | QR-Code Maschinenetikett | `06_QR_Code_Maschinenetikett` | [ ] | [ ] | [ ] |
| 2.7 | QR-Code Pruefpause | `07_QR_Code_Pruefpause` | [ ] | [ ] | [ ] |
| 2.8 | QR-Code Zeitstempel | `08_QR_Code_Zeitstempel` | [ ] | [ ] | [ ] |
| 2.9 | Stresstest | `09_Stresstest` | [ ] | [ ] | [ ] |

### Kapitel 3: Fertigungsstrasse (12 Aufgaben)

| # | Thema | Dateiname | Aufgabe | Loesung | Verifiziert |
|---|---|---|---|---|---|
| 3.1 | Fabrikzugangssystem | `01_Fabrikzugangssystem` | [ ] | [ ] | [ ] |
| 3.2 | Seriennummer-Pruefung | `02_Seriennummer_Pruefung` | [ ] | [ ] | [ ] |
| 3.3 | Fehldiagnose Sortiermaschine | `03_Fehldiagnose_Sortiermaschine` | [ ] | [ ] | [ ] |
| 3.4 | Roboterarm-Steuerung | `04_Roboterarm_Steuerung` | [ ] | [ ] | [ ] |
| 3.5 | Diagnose-Automat | `05_Diagnose_Automat` | [ ] | [ ] | [ ] |
| 3.6 | Materialkalkulator | `06_Materialkalkulator` | [ ] | [ ] | [ ] |
| 3.7 | Werkzeug-Duell | `07_Werkzeug_Duell` | [ ] | [ ] | [ ] |
| 3.8 | Fliessband-Steuerung | `08_Fliessband_Steuerung` | [ ] | [ ] | [ ] |
| 3.9 | Schichtplanung | `09_Schichtplanung` | [ ] | [ ] | [ ] |
| 3.10 | Halbierungsmaschine | `10_Halbierungsmaschine` | [ ] | [ ] | [ ] |
| 3.11 | Ruecklagen-Rechner | `11_Ruecklagen_Rechner` | [ ] | [ ] | [ ] |
| 3.12 | Notfall-Patch | `12_Notfall_Patch` | [ ] | [ ] | [ ] |

### Kapitel 4: Lagerchaos (8 Aufgaben)

| # | Thema | Dateiname | Aufgabe | Loesung | Verifiziert |
|---|---|---|---|---|---|
| 4.1 | Etiketten reparieren | `01_Etiketten_reparieren` | [ ] | [ ] | [ ] |
| 4.2 | Teilelager digitalisieren | `02_Teilelager_digitalisieren` | [ ] | [ ] | [ ] |
| 4.3 | Teilelager bearbeiten | `03_Teilelager_bearbeiten` | [ ] | [ ] | [ ] |
| 4.4 | Teilelager durchsuchen | `04_Teilelager_durchsuchen` | [ ] | [ ] | [ ] |
| 4.5 | Lagerhalle Raster | `05_Lagerhalle_Raster` | [ ] | [ ] | [ ] |
| 4.6 | Teil suchen | `06_Teil_suchen` | [ ] | [ ] | [ ] |
| 4.7 | Teil umlagern | `07_Teil_umlagern` | [ ] | [ ] | [ ] |
| 4.8 | NumPy Sensor-Matrix | `08_NumPy_Sensor_Matrix` | [ ] | [ ] | [ ] |

### Kapitel 5: Code-Review (6 Aufgaben)

| # | Thema | Dateiname | Aufgabe | Loesung | Verifiziert |
|---|---|---|---|---|---|
| 5.1 | Roboterarm-Fehler | `01_Roboterarm_Fehler` | [ ] | [ ] | [ ] |
| 5.2 | Ablaufverfolgung | `02_Ablaufverfolgung` | [ ] | [ ] | [ ] |
| 5.3 | Materialkalkulator 2.0 | `03_Materialkalkulator_2_0` | [ ] | [ ] | [ ] |
| 5.4 | Fehlercodes entschluesseln | `04_Fehlercodes_entschluesseln` | [ ] | [ ] | [ ] |
| 5.5 | Schichtprotokoll | `05_Schichtprotokoll` | [ ] | [ ] | [ ] |
| 5.6 | Mysterioeser Bug | `06_Mysterioeser_Bug` | [ ] | [ ] | [ ] |

### Kapitel 6: Investoren-Pitch (5 Aufgaben)

| # | Thema | Dateiname | Aufgabe | Loesung | Verifiziert |
|---|---|---|---|---|---|
| 6.1 | Qualitaetsbericht | `01_Qualitaetsbericht` | [ ] | [ ] | [ ] |
| 6.2 | Notfall-Kodierung | `02_Notfall_Kodierung` | [ ] | [ ] | [ ] |
| 6.3 | Produktionsdaten Pandas | `03_Produktionsdaten_Pandas` | [ ] | [ ] | [ ] |
| 6.4 | Investor-Dashboard Plotly | `04_Investor_Dashboard_Plotly` | [ ] | [ ] | [ ] |
| 6.5 | Produktions-Dashboard | `05_Produktions_Dashboard` | [ ] | [ ] | [ ] |

### Klausurvorbereitung (11 Aufgaben)

| # | Thema | Dateiname | Aufgabe | Loesung | Verifiziert |
|---|---|---|---|---|---|
| K-1 | Datentypen | `01_Datentypen` | [ ] | [ ] | [ ] |
| K-2 | Fehler finden | `02_Fehler_finden` | [ ] | [ ] | [ ] |
| K-3 | Algorithmus | `03_Algorithmus` | [ ] | [ ] | [ ] |
| K-4 | Bitkodierung | `04_Bitkodierung` | [ ] | [ ] | [ ] |
| K-5 | Von-Neumann | `05_Von_Neumann` | [ ] | [ ] | [ ] |
| K-6 | Redundante Bedingung | `06_Redundante_Bedingung` | [ ] | [ ] | [ ] |
| K-7 | Flussdiagramm | `07_Flussdiagramm` | [ ] | [ ] | [ ] |
| K-8 | Zahlensysteme | `08_Zahlensysteme` | [ ] | [ ] | [ ] |
| K-9 | Chargen-Nummern | `09_Chargen_Nummern` | [ ] | [ ] | [ ] |
| K-10 | Fehlercode erraten | `10_Fehlercode_erraten` | [ ] | [ ] | [ ] |
| K-11 | Materialzuschnitt | `11_Materialzuschnitt` | [ ] | [ ] | [ ] |

---

## Zusaetzliche Abhaengigkeiten

- `qrcode[pil]` (pip install) - fuer Aufgabe 2.6-2.8 (QR-Code-Generierung)

## Bestehende Dateien die wiederverwendet werden

- `autos.csv` -> Produktionsdaten der MotoTec GmbH (1000 Fahrzeuge: Marke, Modell, Baujahr, Verbrauch, CO2)
- `sales.csv` -> Verkaufsdaten der MotoTec-Fahrzeuge (Menge, Umsatz, Stadt)
- `temperatures.csv` -> Maschinentemperatur-Sensordaten (Maschine, Datum, Temperatur, Feuchtigkeit, Standort)
- `Temperaturverlauf.txt` -> 24h-Temperaturverlauf einer Maschine (24 Stundenwerte)
- `Beschreibung.txt` -> Alter Qualitaetsbericht (Inhalt kann an MotoTec-Kontext angepasst werden)
