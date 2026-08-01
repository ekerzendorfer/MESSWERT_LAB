# Änderungsprotokoll

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
