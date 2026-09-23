---
name: build-eval
description: Orchestriert Spec, Eval und einen lauffähigen Zero-Install-HTML-Prototyp in einem einzigen Lauf aus einem Brief — überspringt Schritte deren Dateien schon existieren. Aufrufen als Shortcut für den gesamten Spec-Eval-Zyklus statt Spec-Writer, Eval-Writer und Prototype-Builder einzeln aufzurufen.
allowed-tools: Read, Write, Glob
---

# Orchestrator: Spec, Eval & Prototyp bauen

Führe die folgenden drei Schritte sequenziell aus. Schreibe alle drei Dateien wirklich — kein Code nur als Text.

## Schritt 0: Run-Verzeichnis bestimmen

Berechne das heutige Datum im Format YYYY-MM-DD. Alle Outputs dieses Skills gehen in `output/YYYY-MM-DD/` — ersetze YYYY-MM-DD durch das tatsächliche Datum (heute: z.B. `output/2026-04-09/`). Erstelle dieses Verzeichnis implizit durch den ersten Write-Aufruf.

## Vorbereitung

Der Pfad zum Brief wird beim Aufruf übergeben.
Prüfe mit Glob welche Datendateien im Brief referenziert werden. Lies den Brief und identifiziere die Datendateien. Wenn keine Datendateien gefunden: stoppe und melde den Fehler.

## Schritt 1: Spec → `output/YYYY-MM-DD/spec-eval/spec.md`

Prüfe mit Glob ob `output/YYYY-MM-DD/spec-eval/spec.md` bereits existiert.
- **Existiert:** Lies die Datei und melde "spec.md gefunden — wird verwendet." Kein Neuschreiben.
- **Existiert nicht:** Lies Brief und alle Datendateien. Schreibe `output/YYYY-MM-DD/spec-eval/spec.md` mit: **Zweck**, **Nutzer**, **Daten-Input**, **UI-Komponenten** (nummeriert), **Constraints**. Was, nicht Wie. Keine Implementierungsdetails.

Verifiziere mit Glob, bevor du weitermachst.

## Schritt 2: Eval → `output/YYYY-MM-DD/spec-eval/eval.md`

Prüfe mit Glob ob `output/YYYY-MM-DD/spec-eval/eval.md` bereits existiert.
- **Existiert:** Lies die Datei und melde "eval.md gefunden — wird verwendet." Kein Neuschreiben.
- **Existiert nicht:** Lies `output/YYYY-MM-DD/spec-eval/spec.md`. Schreibe `output/YYYY-MM-DD/spec-eval/eval.md` als Tabelle mit 8–12 Kriterien:

| ID | Kriterium | Wie testen | Pass-Bedingung | Ergebnis |
|----|-----------|------------|----------------|----------|

Jedes Kriterium eindeutig pass/fail entscheidbar. Ergebnis-Spalte wird mit FAIL vorbelegt.

Verifiziere mit Glob, bevor du weitermachst.

## Schritt 3: Prototyp → `output/YYYY-MM-DD/prototyping/app.html` + `data.js`

Lies `output/YYYY-MM-DD/spec-eval/spec.md`. Baue einen Zero-Install-HTML-Prototyp:
- `output/YYYY-MM-DD/prototyping/data.js` übersetzt die Rohdaten aus der Spec (bzw. den referenzierten Datendateien) in ein JS-Objekt und setzt `window.DATA` — kein Hardcoding der Daten in `app.html`
- `output/YYYY-MM-DD/prototyping/app.html` ist eine self-contained Datei mit `<style>` und `<script>` inline, lädt `data.js` per `<script src="data.js">` und implementiert alle UI-Komponenten der Spec
- Sonderfälle behandelt
- Kein Server, kein Build-Schritt, keine externen Abhängigkeiten (kein CDN, kein npm). Öffnet per Doppelklick im Browser (`file://`)
- Kein `fetch()` — der Browser blockiert das unter `file://`. Daten kommen ausschließlich über `data.js`

Verifiziere mit Glob.

## Abschluss

Alle Dateien vorhanden? Dann:
- Pfade ausgeben: `output/YYYY-MM-DD/spec-eval/spec.md`, `output/YYYY-MM-DD/spec-eval/eval.md`, `output/YYYY-MM-DD/prototyping/app.html`, `output/YYYY-MM-DD/prototyping/data.js`
- „app.html per Doppelklick im Browser öffnen"
- "Jetzt bist du dran — öffne die eval.md und gehe jeden Punkt manuell durch, bevor du den eval-runner startest."
