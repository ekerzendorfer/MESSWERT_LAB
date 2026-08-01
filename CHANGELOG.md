# Änderungsprotokoll

## v0.3.0 – 2026-08-01

Erster vollständiger Anwendungsfall für photometrische Kinetik.

### Neu

- automatische Auswertung der Photometer-Exporte für Kristallviolett, Brillantblau/Hypochlorit und Iod-/Vitamin-C-Uhr
- komfortable Auswahl mehrerer Messreihen samt Versuchsbedingungen
- Prüfung, Korrektur und begründeter Ausschluss einzelner Zeitpunkte bei unveränderten Rohdaten
- Messkurve A gegen t
- Endwertkorrektur mit A∞
- automatische Plateauprüfung: Mittel der letzten fünf Punkte nur bei ausreichend konstantem Endbereich, sonst Vorschlag A∞ = 0
- manuelle Wahl von A∞ und des auszuwertenden Zeitbereichs
- Linearisierungen A−A∞, ln(A−A∞) und 1/(A−A∞)
- Vergleich von 0., 1. und 2. Ordnung über R², RMSE und Residuen
- formale Geschwindigkeitskonstanten und Halbwertszeiten mit fachlich korrekter Einheitenkennzeichnung
- Schwellenwertauswertung der Iod-/Vitamin-C-Uhr mit linear interpolierter Schwellenzeit
- relative Vergleichsrate 1/tS für gleichartig durchgeführte Uhrreaktionen
- Vergleichstabelle aller Messreihen
- PNG-, Markdown-, CSV- und Sitzungs-JSON-Export für Kinetik
- eingebettetes Kristallviolett-Beispiel

### Didaktische Leitplanken

- das höchste R² wird ausdrücklich nicht als automatischer Beweis einer Reaktionsordnung ausgegeben
- A∞, Datenbereich und nicht transformierbare Punkte bleiben sichtbar
- Rohdaten werden nie durch Korrekturen oder Ausschlüsse überschrieben
- die fachliche Interpretation bleibt Teil des SchülerInnenprotokolls

## v0.2.1 – 2026-08-01

Komforterweiterung der manuellen Eichkurveneingabe.

### Neu

- Konzentrationen können bei manueller Dateneingabe wahlweise in mol/L oder mg/L erfasst werden
- bei mg/L-Eingabe ist die molare Masse verpflichtend
- Tabellenüberschrift, Prüfschritt und Zusammenfassung verwenden weiterhin die gewählte Eingabeeinheit
- intern werden alle Konzentrationen einheitlich in mol/L gespeichert und berechnet
- das Diagramm übernimmt bei manueller mg/L-Eingabe zunächst ebenfalls mg/L
- CSV-, Markdown- und Sitzungs-JSON-Exporte dokumentieren die Eingabeeinheit

## v0.2.0 – 2026-08-01

Erweiterung der Eichkurvenauswertung um komfortabel bearbeitbare Stoffdaten.

### Neu

- sichtbare Eingabe für den analysierten Stoff und seine molare Masse nach dem CSV-Import
- optionale Eingabe von Stoffname und molarer Masse bei manueller Datenerfassung
- automatische Vorbelegung der molaren Masse aus CSV-Metadaten oder interner Stofftabelle
- manuelle Korrektur oder Ergänzung einer fehlenden molaren Masse
- Anzeige der Herkunft der verwendeten molaren Masse
- Stoffdaten werden in CSV-, Markdown- und Sitzungs-JSON-Exporte übernommen

### Verhalten

- mol/L bleibt immer verfügbar
- mg/L wird nur bei gültiger positiver molarer Masse aktiviert
- Dezimalpunkt und Dezimalkomma werden bei der Eingabe akzeptiert
- eine ungültige oder negative molare Masse wird nicht übernommen

## v0.1.1 – 2026-08-01

Kleine ergonomische und fachliche Nachschärfung der Eichkurvenauswertung.

### Geändert

- kompakte Anzeige „Std.-Abweichung s“ verhindert ungünstige Zeilenumbrüche
- Diagramm-x-Achse kann bei bekannter molarer Masse zwischen mol/L und mg/L umgeschaltet werden
- Steigung, Regressionsgleichung, Residuentabelle und Diagramm werden an die gewählte Einheit angepasst
- unbekannte Probe wird zusätzlich in mg/L ausgegeben
- Endergebnisse werden auf drei signifikante Stellen gerundet
- Kaliumpermanganat wird mit M = 158,034 g/mol umgerechnet

## v0.1.0 – 2026-08-01

Erste lauffähige Version mit einem vollständigen, auf das Virtuelle Photometer zugeschnittenen Eichkurven-Workflow.

### Enthalten

- automatische Erkennung der Photometer-CSV-Struktur
- manuelle Dateneingabe und Beispieldaten
- unveränderte Rohdatenbasis
- begründetes Korrigieren oder Ausschließen von Messwerten
- Mittelwerte und Stichproben-Standardabweichungen
- lineare Regression, R², RMSE und Residuen
- Konzentrationsbestimmung unbekannter Proben
- Interpolations-, Randbereichs- und Extrapolationshinweise
- Diagramm- und Datenexporte
