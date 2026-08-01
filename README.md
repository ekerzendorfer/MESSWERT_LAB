# MESSWERT_LAB – DatenLab

**Version:** v0.3.0  
**Titel der App:** DatenLab – Messwerte auswerten

## Start

Die Datei `index.html` direkt im Browser öffnen oder den gesamten Ordner in das GitHub-Repository `MESSWERT_LAB` hochladen und GitHub Pages aktivieren.

Die App ist als eigenständige Single-HTML-Anwendung ausgeführt. Für die Nutzung sind keine Installation, kein Server und keine zusätzlichen Bibliotheken erforderlich.

## Inhalt des Ordners

- `index.html` – lauffähige Anwendung
- `docs/` – Projektkonzept
- `examples/` – reale CSV-Testexporte aus dem Virtuellen Photometer
- `development/` – Entwicklungs- und Testdateien; für den Betrieb nicht erforderlich

## Unterstützte Anwendungsfälle

### Eichkurve

- automatischer Import von Photometer-Eichkurven
- manuelle Eingabe in mol/L oder mg/L
- nachvollziehbares Korrigieren oder Ausschließen von Messwerten
- Mittelwerte und Stichproben-Standardabweichungen
- lineare Regression, R², RMSE und Residuen
- Bestimmung unbekannter Konzentrationen
- Ergebnisanzeige in mol/L und bei bekannter molarer Masse zusätzlich in mg/L

### Photometrische Kinetik

- Import der Photometer-Exporte für Kristallviolett, Brillantblau/Hypochlorit und Iod-/Vitamin-C-Uhr
- Auswahl und getrennte Prüfung mehrerer Messreihen
- unveränderte Rohdaten sowie begründete Korrekturen und Ausschlüsse
- Messkurve A gegen t
- Plateauprüfung und transparente Festlegung von A∞
- anpassbarer Auswertungszeitraum
- Vergleich der Linearisierungen für 0., 1. und 2. Ordnung
- R², RMSE, Residuen, formale Geschwindigkeitskonstante und Halbwertszeit
- Schwellenzeit und relative Vergleichsrate 1/t bei der Iod-/Vitamin-C-Uhr
- Vergleich aller Messreihen und Versuchsbedingungen

## Hinweise zur Kinetikauswertung

Die App bezeichnet die Linearisierung mit dem höchsten geeigneten R² nur als mathematischen Hinweis. Daraus wird nicht automatisch eine Reaktionsordnung abgeleitet. Bei den Transformationen wird vorausgesetzt, dass die Absorbanz proportional zur Konzentration des beobachteten Stoffes ist.

A∞ wird nur dann automatisch aus den letzten fünf Messpunkten bestimmt, wenn deren Spannweite auf ein ausreichend konstantes Plateau hindeutet. Andernfalls schlägt DatenLab A∞ = 0 vor; der Wert kann kontrolliert und manuell geändert werden.

## Noch nicht enthalten

- manuelle Eingabe kinetischer Zeitreihen
- Bromthymolblau-Spektrenauswertung
- Titrationsauswertung mit erster und zweiter Ableitung
- allgemeiner Aufgaben- und LehrerInnenmodus
