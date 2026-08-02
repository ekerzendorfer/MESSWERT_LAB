# MESSWERT_LAB – DatenLab v0.5.0

Browserbasierte Anwendung zur geführten Auswertung schulischer Messdaten.

## Start

`index.html` lokal im Browser öffnen oder den Ordner als GitHub-Pages-Repository veröffentlichen. Es sind keine Installation, kein Benutzerkonto und keine Serververbindung erforderlich.

## Enthaltene Auswertungen

- Eichkurven und unbekannte Proben
- photometrische Kinetik
- Bromthymolblau-Spektren und pKa-Auswertung
- Titrationen nach der Schnittstelle `MESSWERT_LAB_CSV 1.0`

## Neu in v0.5.0: Titration

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
