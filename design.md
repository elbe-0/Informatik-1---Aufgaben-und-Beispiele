# Mission MotoTec - Design-Dokument

## Konzept

Refactoring aller Informatik-I-Aufgaben zu einer durchgehenden Storyline: **"Mission MotoTec"**.

Die Studierenden sind IT-Notfallteam der **MotoTec GmbH**, einer Autofabrik nach IT-Totalausfall. Werksleiterin **Ingrid Kemper** (erfahren, pragmatisch, trocken-humorvoll) führt sie durch die Rettung. Jede Aufgabe = ein konkretes Problem in der Fabrik, das gelöst werden muss.

### Narrative Struktur pro Notebook

1. **Briefing** (Markdown, 3-5 Sätze): Lage in der Fabrik
2. **Dialog mit Frau Kemper** (kursiv/zitiert): Konkrete Aufgabe und Motivation
3. **Aufgabe**: Programmieraufgabe im Fabrik-Kontext
4. **Debriefing** (optional): Kemper kommentiert das Ergebnis

### Akzeptanzkriterien

- Aufgaben machen Spass (Krimi-/Rettungsstory, Problemloesung als Motivation)
- Vermitteltes Wissen bleibt identisch (1:1-Mapping jeder Originalaufgabe)
- Schwierigkeitsgrad vergleichbar (gleiche Progression 1/5 -> 4/5)
- Sinnvolle Kontext-Integration (jedes Thema hat natuerlichen Grund in Fabrikrettung)

---

## Story-Arc

| Kapitel | Titel | Fabrik-Phase | Stimmung |
|---|---|---|---|
| 1 | Blackout | Systeme hochfahren | Hektisch, Dunkelheit, Grundlagen |
| 2 | Fehlkalibrierung | Sensoren reparieren | Methodisch, Diagnose |
| 3 | Fertigungsstrasse ausser Kontrolle | Produktionslogik fixen | Aufbauend, Kernarbeit |
| 4 | Lagerchaos | Lager organisieren | Ordnung, Komplexitaet |
| 5 | Spaghetti-Code | Systeme modularisieren | Professionalisierung |
| 6 | Investoren-Pitch | Daten auswerten, Fabrik retten | Finale, Triumph |

---

## Kapitel 1: "Blackout" (IDE-Einfuehrung)

**Briefing:** Die Fabrikhalle ist dunkel. Kein System reagiert. Frau Kemper steht mit Taschenlampe am Hauptterminal.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 1.1 | Hello World, Begruessung | Terminal hochfahren: Bootsequenz, Techniker-Name eingeben, Statusmeldung | `print()`, `input()`, Strings, `def`/`return` |
| 1.2 | Zwei Zahlen eingeben & addieren | Stromversorgung pruefen: Spannungswerte per input() eingeben, String-Problem entdecken | `input()`, `int()`, String vs. Integer |
| 1.3 | Steuerzeichen | Statusanzeige reparieren: Formatierung mit Escape-Zeichen fixen, Ladebalken mit \r | `\n`, `\t`, `\r`, `\b`, `print(end="")` |
| 1.4 | Escape-Zeichen Aufgabe | System-Dashboard: Uebersicht aller Fabriksysteme formatiert ausgeben | `\t`, `\n`, Formatierung |

**Schwierigkeit:** 1/5

---

## Kapitel 2: "Fehlkalibrierung" (Variablen & Datentypen)

**Briefing:** Terminal laeuft, aber Sensoren liefern falsche Werte. Temperatur als Text, negative Drehzahlen.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 2.1 | Auskommentieren, Dokumentation | Debug-Log aufraeumen: Stoerende Ausgaben per Kommentar unterdruecken | `#`, Kommentare, Doku-Header |
| 2.2 | Datentyp aendert sich | Warum spinnt der Sensor? drehzahl nach Division ploetzlich float | `type()`, `int`/`float`, implizite Typaenderung |
| 2.3 | Variablen-Beispiele | Maschinenpass rekonstruieren: ID, max_temp, Bezeichnung anlegen | Variablen, `int`, `float`, `str` |
| 2.4 | Explizite Typumwandlung | Sensordaten reparieren: "72.4" als String -> float konvertieren | `float()`, `int()`, `str()`, `type()` |
| 2.5 | Bibliotheken: math, random, time | Werkzeugkasten aktivieren: sqrt fuer Toleranz, random fuer Tests, time fuer Logs | `import`, `math`, `random`, `time` |
| 2.6 | Zufallszahlen plotten | Stresstest: 10 Temperaturwerte ueber Zeit messen und plotten | `random`, `matplotlib`, `while`, `time.sleep()` |

**Schwierigkeit:** 1.5/5

---

## Kapitel 3: "Fertigungsstrasse ausser Kontrolle" (Operatoren & Kontrollstrukturen)

**Briefing:** Maschinen laufen, aber Fertigungslogik ist zerschossen. Falsche Sortierung, Endlosschleifen, Qualitaetskontrolle defekt.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 3.1 | Quersumme, teilbar-durch-5, kombinierte Bedingung | Seriennummer-Pruefung: Quersumme als Pruefziffer, Sondermodell-Erkennung | `//`, `%`, `if/else`, `and`, `int(input())` |
| 3.2 | Loesungen 3.1 | Loesungen Seriennummer-Pruefung | identisch |
| 3.3 | Operatorrangfolge vorhersagen | Fehldiagnose Sortiermaschine: Komplexe Bedingungen analysieren | Operatorrangfolge, `**`, `//`, `%`, `and`/`or` |
| 3.4a | if/elif Verhalten + Einrueckung | Roboterarm-Steuerung debuggen: Warum greift er daneben? | `if/elif/else`, Einrueckung |
| 3.4b | Magic 8-Ball | Qualitaetsorakel: Simulierte Qualitaetspruefung (A-Ware, B-Ware, Ausschuss) | `random.randint()`, `if/elif` |
| 3.4c | Taschenrechner | Materialkalkulator: Materialbedarfe berechnen | `input()`, `if/elif`, Arithmetik |
| 3.4d | Schere-Stein-Papier-Echse-Spock | Schichtplan-Duell: Wer uebernimmt die Nachtschicht? (Fabrik-Variante) | `random`, verschachtelte Bedingungen |
| 3.5a | break/continue vorhersagen | Fliessband-Steuerung analysieren: Welche Autos werden uebersprungen? | `break`, `continue` |
| 3.5b | Alle Teiler einer Zahl | Schichtplanung: X Mitarbeiter in gleichgrosse Teams aufteilen | `for`, `range()`, `%` |
| 3.5c | Wie oft durch 2 teilbar | Halbierungsmaschine: Stahlblock wiederholt halbieren | `while`, `//`, Zaehler |
| 3.5d | Zinsberechnung 50 Jahre | Investitionsrechnung: Kredit-Tilgung fuer neue Maschinen | `while`, Zinseszins, Eingabevalidierung |
| 3.X | Debugger (Primzahlen mit Fehlern) | Notfall-Patch: Chargen-Funktion voller Bugs (C-Syntax, Logikfehler) | Syntax-/Logikfehler, Debugging |

**Schwierigkeit:** 2.5-3/5

---

## Kapitel 4: "Lagerchaos" (Strings & Listen)

**Briefing:** Produktion laeuft, aber Lager ist Katastrophe. Etiketten falsch, Regale durcheinander.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 4.1 | String-Ops: "Strauss & Co." rekonstruieren | Etiketten reparieren: Fehlerhaften Lieferantennamen rekonstruieren + replace | String-Indexing, Slicing, `len()`, `find()`, `replace()` |
| 4.2 | 1D-Listen: Automarken | Teilelager verwalten: 4 Teile -> Liste, CRUD-Operationen | `list`, `append()`, `pop()`, `remove()`, `insert()`, `index()` |
| 4.3a | 2D-Listen: Schachbrett befuellen | Lagerhalle als 8x8-Raster: Teile interaktiv einlagern | 2D-Listen, verschachtelte `for`, `while`, `input()` |
| 4.3b | Weissen Koenig finden | Teil suchen: "Finde den Turbolader im Lager" | Verschachtelte `for`-Schleifen |
| 4.3c | Weissen Koenig verschieben | Teil umlagern: Entfernen + an neuer Position einlagern | 2D-Zugriff, Position loeschen/setzen |

**Schwierigkeit:** 3-3.5/5

---

## Kapitel 5: "Spaghetti-Code" (Funktionale Programmierung)

**Briefing:** Systeme laufen, aber Code ist Chaos. Keine Struktur, nichts wiederverwendbar.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 5.1a | Falscher Funktionsaufruf | Roboterarm-Fehler: Falshe Anzahl Parameter | `def`, Parameter, `TypeError` |
| 5.1b | Debugger Programmfluss | Ablaufverfolgung: Maschinensteuerung step-by-step | Debugger |
| 5.1c | Taschenrechner als Funktion | Materialkalkulator 2.0: Kalkulator aus Kap.3 refactoren | `def`, `return`, Refactoring |
| 5.1d | Dezimal zu Binaer | Fehlercodes entschluesseln: Dezimal-Fehlercode -> Binaer | `while`, Liste, `insert()`, `//`, `%` |
| 5.1e | Datum/Zeit-Funktionen | Schichtprotokoll: Aktuelle Zeit holen + formatiert schreiben | `datetime`, Funktionen |
| 5.2 | Variablengueligkeit local/global | Mysterioeser Bug: Warum tauscht die Funktion die Werte nicht? | `global`, lokaler Scope |

**Schwierigkeit:** 3.5/5

---

## Kapitel 6: "Investoren-Pitch" (Dateien, Pandas, Visualisierung)

**Briefing:** Fabrik laeuft wieder. Investoren wollen Beweise: Daten, Zahlen, Grafiken.

| # | Original | Neu | Konzepte |
|---|---|---|---|
| 6.1 | Dateien lesen, Vokale zaehlen + Bar Chart | Qualitaetsbericht analysieren: Text einlesen, Vokale zaehlen, Balkendiagramm | `open()`, `read()`, `readlines()`, `matplotlib` |
| 6.2 | Dateien schreiben, Leetspeak | Verschluesseltes Backup: Maschinenlogs verschluesselt sichern | `open("w"/"a")`, `write()`, `replace()` |
| 6.3 | Pandas: autos.csv + sales.csv | Produktionsdaten auswerten: Autos filtern/sortieren/gruppieren + Umsatzanalyse | `pd.read_csv()`, Filter, `sort_values()`, `groupby()` |
| 6.4 | Plotly: 2D + 3D Visualisierung | Investor-Dashboard: Interaktive Grafiken fuer die Praesentation | `plotly.express`, `scatter_3d()` |

**Schwierigkeit:** 4/5

---

## Klausurvorbereitung: "Die Abschlusspruefung"

**Briefing:** Fabrik ist gerettet. Kemper: "Bevor ich euch Festvertraege anbiete - Abschlusspruefung."

Die 11 Klausuraufgaben behalten ihren Inhalt, bekommen Fabrik-Framing:
- Zahlenratespiel -> Fehlercode erraten
- Optimierungsaufgabe -> Materialzuschnitt optimieren
- Flussdiagramm -> Gebuehrenberechnung fuer Lieferanten
- Binaer/Hex-Umrechnung -> Maschinenregister-Werte

---

## NPC: Ingrid Kemper

- 30 Jahre Erfahrung in der Autoindustrie
- Pragmatisch, direkt, trockener Humor
- Lobt gute Arbeit knapp: "Laeuft."
- Bei Fehlern: "Schaut euch die Fehlermeldung an. Die luegt nicht."
- Wiederkehrende Sprueche als Running Gags (z.B. "In meiner ersten Fabrik hatten wir nicht mal Terminals...")

---

## Bestehende Dateien die wiederverwendet werden

- `autos.csv` -> Passt perfekt als Produktionsdaten der MotoTec GmbH
- `sales.csv` -> Verkaufsdaten der MotoTec-Fahrzeuge
- `temperatures.csv` -> Maschinentemperatur-Sensordaten
- `Temperaturverlauf.txt` -> 24h-Temperaturverlauf einer Maschine
- `Beschreibung.txt` -> Alter Qualitaetsbericht (Inhalt kann angepasst werden)
