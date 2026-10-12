# MESSWERT_LAB – DatenLab v0.6.2

Browserbasierte Anwendung zur geführten Auswertung schulischer Messdaten.

## Start

`index.html` lokal im Browser öffnen oder den Ordner als GitHub-Pages-Repository veröffentlichen. Es sind keine Installation, kein Benutzerkonto und keine Serververbindung erforderlich.

## Enthaltene Auswertungen

- Eichkurven und unbekannte Proben
- photometrische Kinetik
- Bromthymolblau-Spektren und pKa-Auswertung
- Titrationen nach der Schnittstelle `MESSWERT_LAB_CSV 1.0`

## Fehlerkorrektur in v0.5.2

- CSV-Import des Titrationstools wiederhergestellt
- vollständiger Aufbau aller Titrationsansichten unmittelbar nach dem Import

## Neu in v0.5.1: Überlagerte Titrationsdiagramme

- Optionskästchen „Titrationskurve überlagern“ bei erster und zweiter Ableitung
- pH-Kurve auf der linken y-Achse
- Ableitungswerte mit eigener Einheit auf der rechten y-Achse
- eindeutige Legende und achsenbezogene Farbzuordnung
- Überlagerungszustand im Sitzungs-JSON

## Titration seit v0.5.0

- strikte Prüfung der Schnittstelle und Pflichtmetadaten
- unveränderte Übernahme der Volumen-/pH-Rohdaten
- erste und zweite Ableitung an Volumenmittelpunkten
- Äquivalenzpunktbestimmung nach `TITR_AEP_V1`
- ein oder zwei Äquivalenzpunkte abhängig von Titrationsart und Protonenstufen
- Konzentration in mol/L und Massenkonzentration in g/L
- Vergleich mit Simulationsreferenzen, ohne diese zur ÄP-Suche zu verwenden
- Indikator-Umschlagsbereich im Vergleich zum interpolierten ÄP-pH
- Halbäquivalenzpunkt/pKs nur für einprotonige schwache Säuren oder Basen gemäß Schnittstelle 1.0
- PNG-, Markdown-, CSV- und JSON-Export

## Projektstruktur

- `index.html` – vollständige Single-HTML-App
- `docs/` – Projektkonzept und Titrationsschnittstelle
- `testdaten/` – reale Exporte aus Photometer und Titrationslabor
- `tests/` – Referenzprüfung für die Titrationsauswertung

Alle Berechnungen erfolgen lokal im Browser.


## v0.6.0 – Hub-Integration für die Cu-Photometrie

Das DatenLab kann nun direkt aus dem CHEMIE_ANALYTIK_HUB mit einem `UVVIS_CALIBRATION`-RESULT gestartet werden.

Hub-Modus:
- Standards und unbekannte Absorbanz werden direkt übernommen
- Datenprüfung und lineare Regression bleiben sichtbar
- die Regression ist ein offenes mathematisches Werkzeug, keine unsichtbare Blackbox
- die bisher automatisch ausgegebene Konzentration der unbekannten Probe wird im Hub-Modus verborgen
- die quantitative Auswertung erfolgt stattdessen schrittweise durch die SchülerInnen:
  1. Eignung der Eichgeraden beurteilen
  2. Konzentration der Messlösung aus A = m·c + b bestimmen
  3. Verdünnung auf die ursprüngliche Stocklösung zurückrechnen
  4. Stoffmenge Cu²⁺ in 100,0 mL bestimmen
  5. Masse CuSO₄·5H₂O gemäß VCÖ-01-Fallmodell berechnen
- jeder Schritt wird unmittelbar geprüft, ohne den Lösungswert vorzugeben
- erst nach vollständiger korrekter Rechenkette wird die Rückgabe an den Hub freigeschaltet

Rückgabe:
- `analysis_type: PHOTOMETRIC_QUANT_EVALUATION`
- verwendete Eichdaten und unbekannte Messwerte
- Regressionskennwerte
- studentische Rechenkette
- finale Cu-Stoffmenge und Massenbilanz als CuSO₄·5H₂O

Der normale Standalone-Betrieb für Photometrie, Kinetik, BTB und Titrationsdaten bleibt unverändert.


## v0.6.1 – Rundung in der Hub-Photometrie

Beim VCÖ-01-Hubauftrag wird nach der Berechnung von c(Mess) aus der Regressionsgeraden nun ausdrücklich auf sinnvolle Rundung entsprechend der Messgenauigkeit hingewiesen. Für die vorliegenden VCÖ-01-Daten ist ein Arbeitswert von ungefähr 0,01 mol/L angemessen; zusätzliche Regressionsstellen sollen nicht als Scheingenauigkeit in die weitere Bilanz übernommen werden.

Wichtig für die Transparenz der Rechenkette: Nach akzeptierter Eingabe von c(Mess) werden Verdünnungsrechnung, Stoffmenge und Massenbilanz nun aus den jeweils von den SchülerInnen eingegebenen und akzeptierten Zwischenwerten weitergeführt – nicht aus einem intern ungerundeten Regressionswert.


## v0.6.2 – Prüfung von c(Mess) gegen die Regressionsbeziehung

Beim Hub-Photometrieauftrag wird die Eingabe von c(Mess) jetzt nicht mehr gegen einen intern ungerundeten Zielwert geprüft. Stattdessen wird kontrolliert, ob der eingegebene – sinnvoll gerundete – Konzentrationswert die sichtbare Regressionsbeziehung A = m·c + b mit der gemessenen mittleren Absorbanz innerhalb einer zur Mess- und Regressionsgenauigkeit passenden Toleranz erfüllt.

Damit werden Rundungswerte wie 0,01 bzw. entsprechend aus der sichtbaren Eichgeraden berechnete Werte akzeptiert, sofern sie mit der Messung konsistent sind.

Zusätzlich wurde der konkrete VCÖ-01-Zielwert aus dem Hilfetext entfernt, damit im Expertenkontext keine Lösung vorweggenommen wird.
