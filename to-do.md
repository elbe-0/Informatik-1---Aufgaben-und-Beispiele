-laboraufgaben einfügen
-add to 2.1: wie können sie sicherstellen, dass ihr Ergebnis den gewünschten Datentyp hat? Schauen Sie bei den mathematischen Operatoren im Skript nach einem geeigneten Hilfsmitel., ergänzende frage: warum verhält es sich mit Mulitplikation anders? Diskutieren Sie mit ihrem Nachbarn. Lösung: (Kurzgefasst) Mathematische Vorhersagbarkeit

In der Mathematik ist das Produkt zweier ganzer Zahlen (Integers) immer wieder eine ganze Zahl. Es gibt keinen Fall, in dem die Rechnung Ganzzahl * Ganzzahl plötzlich Nachkommastellen erzeugt.

    5 * 2 = 10 (Ganzzahl)

    3 * 3 = 9 (Ganzzahl)

Da das Ergebnis garantiert eine ganze Zahl ist, gibt es für Python keinen Grund, den Datentyp ungefragt zu ändern. Das Programm bleibt bei int, da dieser Typ effizienter ist. Bei der Division hingegen führt die Rechnung sehr oft zu einem Rest (5 / 2 = 2.5), weshalb Python sich dort für den "sichersten gemeinsamen Nenner" (float) entschieden hat.
2. Schutz vor Präzisionsverlust (Der wichtigste technische Grund)

Dies ist ein entscheidender Vorteil von Python gegenüber vielen anderen Sprachen:

    Integers in Python haben eine unbegrenzte Genauigkeit (Arbitrary Precision). Sie können hunderte Stellen lang sein, ohne dass eine einzige Ziffer verloren geht.

    Floats hingegen haben eine begrenzte Genauigkeit (64-Bit-Standard). Ab einer gewissen Größe werden Zahlen gerundet.

Würde Python das Ergebnis einer Multiplikation von Integers automatisch in einen float umwandeln, würdest du bei sehr großen Zahlen sofort Informationen verlieren.
Beispiel:

    10**20 * 10**20 ergibt als int ein absolut exaktes Ergebnis.

    Als float wäre das Ergebnis nur noch eine wissenschaftliche Annäherung (1e+40), und die hinteren Ziffern wären ungenau oder verloren.
-2.3 und 2.4 optional 
-2.5: sie müssen zT auch installiert werden (Formulierungsfehler im Briefing und auch anderen Texten der Aufgabe): ## Briefing

Die Sensoren liefern wieder korrekte Werte. Aber für die Reparatur der Fertigungsstraße braucht das Team mehr Werkzeuge: Wurzelberechnungen für Toleranzgrenzen, Zufallswerte für Testsimulationen, Zeitstempel für Protokolle. Python bringt diese Werkzeuge als **Bibliotheken** mit - fertige Sammlungen von Befehlen, die nur aktiviert werden müssen. 
-ergänze dort auch ein kurzes beispiel mit pip install (und hinweis auf anaconda als alternative)
ordner 02 müsste neben variablen datentypen auch bibliotheken heißen
2-6, hier ist was komisch oder?
import qrcode

# QR-Code mit beliebigem Text erzeugen
bild = qrcode.make("Hallo MotoTec!")
bild

-Hilfestellung in 2.6 ist trivial, entfernen bitte
-when i scan the qr code of 2.6 with my phone, it automatically google that. is this the intent behavior? can there just an information be disyplayed minimal?

2.6:
> *"Perfekt. Name, ID, Leistung, Tagesverbrauch - alles drin. Ein Scan und jeder Techniker weiß Bescheid. So sieht moderne Kennzeichnung aus. Jetzt müssen wir nur noch sicherstellen, dass die Daten auch stimmen, bevor wir drucken."*
this should be: bevor wir den QR Code generieren. 
And can a created qr code be updated also? or always new genereated? because when i think on printing one with fix information which always vary, this needs to be updated. so also in 2.7 this should be align to not only drucken so generating and updating in the wordings.

2.7 solution took long to execute, nothing happened:
import qrcode
import math
import time

# === Aufgabe (a): Daten eingeben und berechnen ===
name = input("Maschinenname: ")
maschinen_id = int(input("Maschinen-ID: "))
leistung = float(input("Leistung in kW: "))

betriebsstunden = 16
tagesverbrauch = math.ceil(leistung * betriebsstunden)

# === Aufgabe (b): Daten zur Prüfung anzeigen ===
print()
print("=== Datenprüfung ===")
print(f"Name: {name}")
print(f"ID: {maschinen_id}")
print(f"Leistung: {leistung} kW")
print(f"Tagesverbrauch: {tagesverbrauch} kWh")
print()
print("QR-Code wird in 3 Sekunden generiert...")

# === Aufgabe (c): Prüfpause und QR-Code ===
# time.sleep(3) hält das Programm 3 Sekunden an.
# In dieser Zeit kann der Techniker die Daten prüfen.
time.sleep(3)

print("QR-Code wird generiert...")

etikett_text = f"""MotoTec Maschinenetikett
Name: {name}
ID: {maschinen_id}
Leistung: {leistung} kW
Tagesverbrauch: {tagesverbrauch} kWh"""

bild = qrcode.make(etikett_text)
bild

-use print(bild) everythwere its used
for a better understanding for the studierenden

2.9: include an information in the header: für fortgeschrittene (behandelt zukünftige Themen)

in 2.7:
**(c)** Warten Sie mit `time.sleep(3)` drei Sekunden. Geben Sie danach eine Bestätigung aus und erzeugen Sie den QR-Code.
the studierenden should check which befehl on they own. do not give this info in the exercise. check if there are problem like that on other places too.

_______________________
kommenare in den aufgaben blöcken (die bezug nehmen auf a, b, ...) sollen alle entfernt werden. (in lösung dürfen sie bleiben)


code review