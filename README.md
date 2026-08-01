# MESSWERT_LAB – DatenLab

**Version:** v0.1.1  
**Titel der App:** DatenLab – Messwerte auswerten

## Start

Die Datei `index.html` direkt im Browser öffnen oder den gesamten Ordner in das GitHub-Repository `MESSWERT_LAB` hochladen und GitHub Pages aktivieren.

Die App ist als eigenständige Single-HTML-Anwendung ausgeführt. Für die Nutzung sind keine Installation, kein Server und keine zusätzlichen Bibliotheken erforderlich.

## Inhalt des Ordners

- `index.html` – lauffähige Anwendung
- `docs/` – Projektkonzept
- `examples/` – reale CSV-Testexporte aus dem Virtuellen Photometer
- `development/` – Entwicklungs- und Testdateien; für den Betrieb der App nicht erforderlich

## Schwerpunkt von v0.1.1

- Import von Photometer-Eichkurven
- Prüfung und nachvollziehbarer Ausschluss einzelner Messwerte
- Zusammenfassung von Wiederholungsmessungen
- lineare Regression und Eichkurve
- Bestimmung einer unbekannten Konzentration
- Export von Diagramm, Markdown, CSV und Sitzungs-JSON

Andere Photometer-Exporttypen werden erkannt, aber in dieser Version noch nicht ausgewertet.


## Ergänzungen in v0.1.1

- kompaktere Beschriftung der Standardabweichung in den Messwertkarten
- umschaltbare Diagramm-x-Achse zwischen mol/L und mg/L bei hinterlegter molarer Masse
- Kaliumpermanganat: Umrechnung mit M = 158,034 g/mol
- Konzentration unbekannter Proben in mol/L und zusätzlich mg/L
- Endergebnisse einheitlich auf drei signifikante Stellen gerundet
