# MESSWERT_LAB / DatenLab
## Projektkonzept und Übergabe für einen neuen Chat

## 1. Projektidee

`MESSWERT_LAB` soll eine eigenständige browserbasierte Anwendung zur Eingabe, Auswertung und Visualisierung experimenteller Messdaten werden.

**Vorgeschlagener Repository-Name:** `MESSWERT_LAB`  
**Sichtbarer App-Titel:** **DatenLab – Messwerte auswerten**

Die Anwendung soll vollständig im Browser laufen und als Single-HTML-App über GitHub Pages bereitgestellt werden. Sie soll unabhängig von Excel, Google Sheets oder anderer Tabellenkalkulationssoftware funktionieren.

Ziel ist eine niedrigschwellige, didaktisch geführte Messwertauswertung für SchülerInnen, Lehrkräfte und schulische Laborprojekte.

---

## 2. Ausgangslage und Motivation

Mehrere bestehende und geplante virtuelle Chemie-Apps erzeugen Messwerte, zum Beispiel:

- Virtuelles Photometer
- Virtuelle Destillation
- kinetische Messungen
- spätere Enzymkinetik
- Titrations- und Gleichgewichtsversuche
- weitere Schülerlabor-Apps

Die eigentliche Auswertung erfolgt derzeit typischerweise in externen Programmen wie:

- Excel
- Google Sheets
- LibreOffice Calc
- Statistiksoftware

`MESSWERT_LAB` soll diese Lücke schließen und eine einheitliche, browserbasierte Auswertungsumgebung bereitstellen.

Die App soll sowohl Daten aus virtuellen Laboren als auch reale Messwerte aus dem Unterricht verarbeiten können.

---

## 3. Didaktische Grundidee

Die App darf keine reine „Ergebnis-Maschine“ sein.

Sie soll:

1. Messdaten strukturiert erfassen,
2. Rechenwege transparent darstellen,
3. Diagramme erzeugen,
4. statistische Kennwerte erklären,
5. problematische Werte sichtbar machen,
6. die Interpretation weiterhin bei den SchülerInnen belassen.

Die SchülerInnen sollen erkennen:

- wie Mittelwerte entstehen,
- warum Messwerte streuen,
- was Standardabweichung bedeutet,
- wie eine Regressionsgerade berechnet wird,
- wie unbekannte Werte aus einer Kalibrierung bestimmt werden,
- wann Messpunkte auffällig sind,
- warum einzelne Werte nicht beliebig gelöscht werden dürfen.

Die App soll die Auswertung unterstützen, aber nicht das externe Versuchsprotokoll oder die fachliche Argumentation ersetzen.

---

## 4. Technische Grundanforderungen

Die Anwendung soll:

- als Single-HTML-App funktionieren,
- vollständig im Browser laufen,
- keine Installation benötigen,
- auf GitHub Pages veröffentlicht werden können,
- ohne Benutzerkonto nutzbar sein,
- keine Serververbindung erfordern,
- auf Desktop und Tablet funktionieren,
- Daten lokal verarbeiten,
- CSV-Dateien importieren und exportieren,
- manuelle Dateneingabe ermöglichen,
- Ergebnisse als Diagramm oder kompakte Zusammenfassung exportieren können.

Optional kann später eine lokale Sitzungswiederherstellung über `localStorage` ergänzt werden.

---

# 5. Hauptmodule

## 5.1 Modul A – Dateneingabe

### Manuelle Eingabe

Die SchülerInnen sollen Daten direkt in eine Tabelle eingeben können.

Typische Spalten:

- Messreihe
- unabhängige Variable \(x\)
- abhängige Variable \(y\)
- Wiederholung 1
- Wiederholung 2
- Wiederholung 3
- Einheit
- Bemerkung

Mögliche Beispiele:

- Konzentration und Absorbanz
- Zeit und Absorbanz
- Temperatur und Reaktionsgeschwindigkeit
- Volumen und Temperatur
- Fraktion und Messwert
- pH-Wert und Absorbanz

### Tabellenfunktionen

- Zeile hinzufügen
- Zeile löschen
- Zeilen sortieren
- Werte korrigieren
- Spaltenbezeichnungen ändern
- Einheiten festlegen
- fehlende Werte zulassen
- Dezimalpunkt und Dezimalkomma akzeptieren
- ungültige Eingaben klar markieren

---

## 5.2 Modul B – CSV-Import

Die App soll CSV-Dateien aus anderen Chemie-Apps importieren können.

Wichtige Anforderungen:

- Semikolon oder Komma als Trennzeichen erkennen
- Dezimalkomma und Dezimalpunkt akzeptieren
- Spaltenüberschriften anzeigen
- Zuordnung der Spalten zu \(x\), \(y\), Wiederholungen oder Kategorien
- Vorschau vor dem Import
- überflüssige Metadaten ignorieren oder separat anzeigen
- Importfehler verständlich melden

### Unterstützte Quellen

Langfristig sollen CSV-Dateien aus folgenden Projekten unterstützt werden:

- Virtuelles Photometer
- Virtuelle Destillation
- Kinetikmodule
- Enzymkinetik-App
- reale Messgeräte
- beliebige schulische Tabellen

---

## 5.3 Modul C – Deskriptive Statistik

Für Messreihen und Wiederholungsmessungen sollen berechnet werden:

- Anzahl der Messwerte \(n\)
- arithmetischer Mittelwert
- Minimum
- Maximum
- Spannweite
- Standardabweichung
- Varianz
- relative Standardabweichung
- Standardfehler des Mittelwerts, optional
- Median, optional

### Didaktische Darstellung

Die App soll nicht nur Ergebnisse anzeigen, sondern auf Wunsch auch Rechenschritte:

- Summe der Messwerte
- Abweichungen vom Mittelwert
- quadrierte Abweichungen
- Division durch \(n-1\) bei der Stichprobenvarianz
- Quadratwurzel zur Standardabweichung

Dafür sind zwei Ansichten sinnvoll:

- **Kompaktansicht**
- **Rechenweg anzeigen**

---

## 5.4 Modul D – Diagramme

Grundlegende Diagrammtypen:

- Punktdiagramm
- Liniendiagramm
- Streudiagramm
- Messpunkte mit Fehlerbalken
- Regressionsdiagramm
- Zeitreihe

Einstellbar:

- Achsenbezeichnungen
- Einheiten
- Diagrammtitel
- lineare oder logarithmische Achse, später
- Verbindungslinien ein- oder ausblenden
- Fehlerbalken
- Messpunktbeschriftungen
- Regressionsgerade
- Residuenansicht

Die Diagramme sollen exportierbar sein, zum Beispiel als PNG oder SVG.

---

## 5.5 Modul E – Lineare Regression und Eichkurve

Dieses Modul ist besonders wichtig für das Virtuelle Photometer.

Berechnet werden sollen:

- Regressionsgleichung
- Steigung
- Achsenabschnitt
- Bestimmtheitsmaß \(R^2\)
- Residuen
- mittlerer quadratischer Fehler oder RMSE
- optional Unsicherheit der Steigung und des Achsenabschnitts

### Unbekannte Probe

Aus einem Messwert \(y\) soll ein unbekannter \(x\)-Wert bestimmt werden können.

Beispiel:

- gemessene Absorbanz
- Konzentration aus der Eichgeraden
- Anzeige der Interpolation im Diagramm

Die App soll klar unterscheiden zwischen:

- Interpolation innerhalb des Eichbereichs
- Extrapolation außerhalb des Eichbereichs

Bei Extrapolation erscheint eine Warnung.

---

## 5.6 Modul F – Ausreißer und auffällige Messwerte

Die App soll auffällige Werte markieren, aber nicht automatisch löschen.

Mögliche Hinweise:

- große Abweichung vom Mittelwert
- starkes Residuum
- ungewöhnlich große Streuung
- Messwert außerhalb des Kalibrierbereichs
- fehlende oder inkonsistente Wiederholung

Wichtig:

> Ein Wert darf nicht automatisch als „falsch“ bezeichnet werden.

Die App soll Formulierungen verwenden wie:

- „auffälliger Messwert“
- „sollte überprüft werden“
- „mögliche Abweichung“
- „Wiederholungsmessung empfohlen“

Optional können später einfache Verfahren ergänzt werden:

- z-Score
- IQR-Regel
- Grubbs-Test, nur im erweiterten Modus

---

## 5.7 Modul G – Kinetische Auswertung

Als spätere Erweiterung soll die App Zeitreihen auswerten können.

Mögliche Darstellungen:

- \(A\) gegen \(t\)
- \(\ln(A)\) gegen \(t\)
- \(1/A\) gegen \(t\)
- Konzentration gegen Zeit
- Reaktionsgeschwindigkeit gegen Konzentration

Mögliche Ergebnisse:

- Reaktionsordnung
- Geschwindigkeitskonstante
- Halbwertszeit
- Vergleich verschiedener Versuchsbedingungen

Dieses Modul ist besonders für folgende Projekte geeignet:

- Entfärbung von Kristallviolett
- Farbstoffbleiche mit Hypochlorit
- weitere photometrische Kinetik
- spätere Enzymkinetik

---

# 6. Betriebsarten

## 6.1 Freie Auswertung

Die NutzerInnen geben Daten ein oder importieren sie und wählen selbst die Auswertung.

Geeignet für:

- reale Laborversuche
- offene Aufgaben
- Olympiade
- Projektunterricht

## 6.2 Geführte Auswertung

Die App gibt einen strukturierten Ablauf vor:

1. Daten eingeben
2. Einheiten kontrollieren
3. Wiederholungsmessungen zusammenfassen
4. Diagramm auswählen
5. Regression durchführen
6. Ergebnis interpretieren

Geeignet für EinsteigerInnen.

## 6.3 Aufgabenmodus

Vordefinierte Aufgaben führen durch konkrete Auswertungen.

Die Aufgaben können über JSON bereitgestellt werden.

Beispiel:

```json
{
  "id": "PHOT-EICH-01",
  "title": "Eichkurve für Kaliumpermanganat",
  "level": "geführt",
  "analysisType": "linear_regression",
  "requiredColumns": ["concentration", "absorbance"],
  "showCalculationHints": true,
  "teacherNotes": {}
}
```

## 6.4 LehrerInnenmodus

Zusätzliche Funktionen:

- Musterlösung
- Sollwerte
- erwartete Regression
- Toleranzbereiche
- Vergleich mit Referenzdaten
- Hinweise zu typischen Fehlern
- optionale automatische Kontrolle

---

# 7. Aufgabenprofil

## 7.1 Grundlegende Aufgaben

- Mittelwert aus Wiederholungsmessungen bestimmen
- Standardabweichung berechnen
- Messwerte in einem Diagramm darstellen
- Achsen korrekt beschriften
- geeigneten Diagrammtyp auswählen
- Streuung beschreiben

## 7.2 Eichkurvenaufgaben

- Standards eintragen
- Mittelwerte aus Wiederholungen bilden
- Eichgerade berechnen
- \(R^2\) interpretieren
- unbekannte Konzentration bestimmen
- Interpolation und Extrapolation unterscheiden
- auffällige Standards erkennen

## 7.3 Fehleranalyse

- Eichkurven mit und ohne systematischen Fehler vergleichen
- mögliche Ausreißer erkennen
- Wiederholungsmessungen beurteilen
- zufällige und systematische Fehler unterscheiden
- entscheiden, welche Messung wiederholt werden sollte

## 7.4 Kinetikaufgaben

- Zeitreihe darstellen
- geeignete Linearisierung wählen
- Geschwindigkeitskonstante bestimmen
- Halbwertszeit berechnen
- mehrere Reaktionsbedingungen vergleichen
- Reaktionsordnung ableiten

## 7.5 Offene Aufgaben

- geeignete Auswertungsmethode auswählen
- Datenqualität beurteilen
- begründete Ausschlusskriterien formulieren
- Messstrategie verbessern
- Ergebnisse mit Unsicherheiten diskutieren

---

# 8. Externer Protokollworkflow

Auch `MESSWERT_LAB` soll kein vollständiges Protokoll schreiben.

Die App kann liefern:

- Rohdatentabelle
- berechnete Kennwerte
- Diagramm
- Regressionsgleichung
- Exportdatei
- kompakte Zusammenfassung der verwendeten Methode

Die SchülerInnen müssen weiterhin selbst formulieren:

- Fragestellung
- Versuchsaufbau
- Beobachtungen
- Interpretation
- Fehlerdiskussion
- Schlussfolgerung

---

# 9. Import- und Exportformate

## Import

- CSV
- manuelle Eingabe
- später optional JSON

## Export

### CSV

- Rohdaten
- bereinigte Daten
- Mittelwerte
- statistische Kennwerte

### Markdown

- kompakte Auswertungsübersicht
- Werte und Rechenweg
- geeignet zum Einfügen in den Onlinekurs oder ein Protokoll

### Grafik

- PNG
- optional SVG

### JSON

Für den Austausch zwischen virtuellen Labor-Apps und `MESSWERT_LAB`.

---

# 10. Mögliche gemeinsame Datenschnittstelle

Langfristig wäre ein einheitliches JSON-Format sinnvoll.

Beispiel:

```json
{
  "sourceApp": "VIRTUELLES_PHOTOMETER",
  "experimentId": "PHOT-KM-01",
  "title": "Eichkurve Kaliumpermanganat",
  "x": {
    "name": "Konzentration",
    "unit": "mol/L"
  },
  "y": {
    "name": "Absorbanz",
    "unit": ""
  },
  "data": [
    {
      "x": 0.00005,
      "values": [0.119, 0.123, 0.121]
    }
  ],
  "metadata": {
    "wavelength": 525,
    "pathLength": 1.0
  }
}
```

Damit könnten Messdaten direkt zwischen den Projekten übertragen werden.

---

# 11. Benutzeroberfläche

Empfohlene Hauptnavigation:

1. **Daten**
2. **Statistik**
3. **Diagramm**
4. **Regression**
5. **Kinetik**
6. **Aufgaben**

Um Überladung zu vermeiden, könnten Statistik, Regression und Kinetik abhängig vom gewählten Auswertungstyp eingeblendet werden.

### Empfohlener Workflow

1. Daten eingeben oder importieren
2. Spalten zuordnen
3. Auswertungsart wählen
4. Kennwerte berechnen
5. Diagramm erstellen
6. Ergebnis exportieren

---

# 12. Schutz vor didaktischer Überladung

Die App soll:

- nicht alle Kennwerte gleichzeitig anzeigen,
- erweiterte Statistik einklappbar machen,
- Fachbegriffe kontextsensitiv erklären,
- Anfänger- und Expertenansicht trennen,
- keine automatische Datenbereinigung durchführen,
- keine Messwerte ohne Bestätigung löschen,
- bei komplexen Verfahren kurze Hilfen anbieten.

---

# 13. Vorgeschlagene Versionsplanung

## v0.1.0 – Grundgerüst und Dateneingabe

- Single-HTML-App
- manuelle Tabelle
- CSV-Import
- Spaltenzuordnung
- einfache Validierung
- CSV-Export

## v0.2.0 – Deskriptive Statistik

- Mittelwert
- Standardabweichung
- Varianz
- relative Standardabweichung
- Wiederholungsmessungen
- Rechenwegansicht

## v0.3.0 – Diagramme

- Punkt- und Liniendiagramm
- Streudiagramm
- Achsen und Einheiten
- Fehlerbalken
- Grafikexport

## v0.4.0 – Regression und Eichkurve

- lineare Regression
- \(R^2\)
- Residuen
- unbekannter Wert
- Warnung bei Extrapolation

## v0.5.0 – Aufgabenmodus

- geführte Aufgaben
- offene Aufgaben
- LehrerInnenhinweise
- Export einer Auswertungsübersicht

## v0.6.0 – Fehleranalyse

- auffällige Messwerte
- Residuenanalyse
- Vergleich zufälliger und systematischer Fehler
- optionale Ausreißerdiagnostik

## v0.7.0 – Kinetische Auswertung

- \(A(t)\)
- \(\ln(A)\)
- \(1/A\)
- Regressionsvergleich
- Geschwindigkeitskonstante
- Halbwertszeit

## v0.8.0 – App-übergreifender Datenaustausch

- standardisiertes JSON
- direkte Übernahme aus Chemie-Apps
- Metadaten
- Versuchscodes

## v0.9.0 – Unterrichts- und Dokumentationsversion

- stabile Oberfläche
- Begleitmaterial
- Beispielaufgaben
- Importbeispiele
- Tests durch Lehrkräfte

## v1.0.0 – Stabile Veröffentlichung

- dokumentiertes Datenformat
- vollständige Hilfe
- getestete Exportformate
- stabile Aufgabenbibliothek
- Quellen- und Lizenzangaben

---

# 14. Empfohlener Startumfang

Für den ersten Entwicklungszyklus sollte der Umfang bewusst klein bleiben.

### Unverzichtbar für v0.1.0

- manuelle Dateneingabe
- CSV-Import
- Spaltenzuordnung
- Tabelle bearbeiten
- Daten validieren
- Datensatz zurücksetzen
- Rohdaten exportieren

### Noch nicht in v0.1.0

- Regression
- Diagramme
- Fehlerbalken
- Aufgabenmodus
- Kinetik
- automatische Ausreißerprüfung

Die kleinschrittige Entwicklung soll wie bei den bisherigen Apps beibehalten werden.

---

# 15. Beispielhafte Anwendung mit dem Virtuellen Photometer

## Workflow

1. Im Virtuellen Photometer Standards messen.
2. CSV-Rohdaten exportieren.
3. Zu `MESSWERT_LAB` wechseln.
4. CSV importieren.
5. Konzentration als \(x\) und Absorbanz als \(y\) zuordnen.
6. Wiederholungsmessungen zusammenfassen.
7. Eichgerade berechnen.
8. unbekannte Probe bestimmen.
9. Diagramm und Kennwerte exportieren.
10. Ergebnisse im externen Protokoll interpretieren.

Damit bleiben Messung und Auswertung getrennt, aber beide vollständig browserbasiert.

---

# 16. Projektprofil für den neuen Chat

Im neuen Chat soll das Projekt nach folgenden Grundsätzen entwickelt werden:

- Repository: `MESSWERT_LAB`
- sichtbarer Titel: **DatenLab – Messwerte auswerten**
- Single HTML auf GitHub Pages
- browserbasiert und installationsfrei
- kleinste stabile Entwicklungsschritte
- zuerst Dateneingabe und CSV-Import
- danach Statistik, Diagramme und Regression
- keine automatische Komplettauswertung
- Rechenwege und Datenqualität transparent machen
- externe Protokollführung beibehalten
- kompatibel mit Daten aus mehreren Chemie-Apps
- später Aufgaben- und Kinetikmodule ergänzen

---

# 17. Kurzfassung

`MESSWERT_LAB` soll eine universelle browserbasierte Messwert-Auswertungsapp werden.

Kernfunktionen:

- Daten eingeben
- CSV importieren
- Mittelwerte und Streuung berechnen
- Diagramme erstellen
- Eichgeraden bestimmen
- unbekannte Werte berechnen
- auffällige Messwerte erkennen
- kinetische Daten auswerten
- Ergebnisse exportieren

Die App soll externe Tabellenkalkulationen weitgehend ersetzen, ohne die fachliche Interpretation oder das Protokoll zu automatisieren.
