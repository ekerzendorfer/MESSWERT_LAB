# MESSWERT_LAB – DatenLab

**Version:** v0.2.0  
**Titel der App:** DatenLab – Messwerte auswerten

## Start

Die Datei `index.html` direkt im Browser öffnen oder den gesamten Ordner in das GitHub-Repository `MESSWERT_LAB` hochladen und GitHub Pages aktivieren.

Die App ist als eigenständige Single-HTML-Anwendung ausgeführt. Für die Nutzung sind keine Installation, kein Server und keine zusätzlichen Bibliotheken erforderlich.

## Inhalt des Ordners

- `index.html` – lauffähige Anwendung
- `docs/` – Projektkonzept
- `examples/` – reale CSV-Testexporte aus dem Virtuellen Photometer
- `development/` – Entwicklungs- und Testdateien; für den Betrieb der App nicht erforderlich

## Schwerpunkt von v0.2.0

- Import von Photometer-Eichkurven
- Prüfung und nachvollziehbarer Ausschluss einzelner Messwerte
- Zusammenfassung von Wiederholungsmessungen
- lineare Regression und Eichkurve
- Bestimmung einer unbekannten Konzentration
- Export von Diagramm, Markdown, CSV und Sitzungs-JSON
- editierbare Stoffangabe und molare Masse
- Umrechnung und Ergebnisanzeige in mol/L und mg/L

Andere Photometer-Exporttypen werden erkannt, aber in dieser Version noch nicht ausgewertet.

## Neu in v0.2.0

- Die molare Masse kann nach jedem Import kontrolliert, ergänzt oder überschrieben werden.
- Bei manueller Dateneingabe stehen Felder für Stoffname und molare Masse bereit.
- Die Herkunft der verwendeten molaren Masse wird angezeigt: Metadaten, interne Stofftabelle oder manuelle Eingabe.
- Ohne molare Masse bleibt die vollständige Auswertung in mol/L möglich; die mg/L-Ausgabe wird verständlich deaktiviert.
- Stoffname, molare Masse und deren Herkunft werden in die Exporte übernommen.
