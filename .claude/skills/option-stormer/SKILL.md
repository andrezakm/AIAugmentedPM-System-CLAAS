---
name: option-stormer
description: Baut aus einer Spec drei strukturell verschiedene Zero-Install-HTML-Prototypen parallel und vergleicht sie — der Willison-Move, wenn eine Kern-UI-Entscheidung noch offen ist.
---

> **Hinweis:** Verwende ausschließlich die eingebauten Tools. Keine MCP-Tools.

# Skill: Option Stormer

Du nimmst eine Spec und baust 3 verschiedene Prototypen — nicht einen und dann iterieren, sondern drei parallel, dann vergleichen. Das ist der Willison-Move: prototype drei Wege, weil es fast nichts kostet. Nicht eine Lösung bauen und hoffen, sondern drei bauen, anschauen, und entscheiden welche lebt.

## Schritt 0: Run-Verzeichnis bestimmen

Berechne das heutige Datum im Format YYYY-MM-DD. Alle Outputs dieses Skills gehen in `output/YYYY-MM-DD/` — ersetze YYYY-MM-DD durch das tatsächliche Datum (heute: z.B. `output/2026-04-09/`). Erstelle dieses Verzeichnis implizit durch den ersten Write-Aufruf.

## Input

- `output/YYYY-MM-DD/spec-eval/spec.md`
- Datendateien die in der Spec referenziert werden (via Glob finden)

## Vorgehen

1. **Spec lesen** — Lies `output/YYYY-MM-DD/spec-eval/spec.md` vollständig. Identifiziere alle UI-Komponenten und Constraints.
2. **Kern-UI-Entscheidung identifizieren** — Was ist die zentrale Design-Entscheidung? Layout, Interaktionsmodell, oder Informationshierarchie?
3. **3 Varianten bauen** — Schreibe drei vollständige Zero-Install-HTML-Prototypen (je `app.html` + `data.js`), die sich in dieser Kern-Entscheidung unterscheiden:
   - **Variante A** — Die naheliegendste Lösung
   - **Variante B** — Eine Alternative die ein anderes Interaktionsmuster nutzt
   - **Variante C** — Die unerwartete Variante: Was wäre wenn man das Problem ganz anders angeht?
4. **Vergleich schreiben** — Schreibe eine Vergleichstabelle: Was unterscheidet die drei? Welche Trade-offs?

## Der HTML-Vertrag

Jede Variante besteht aus zwei Dateien in ihrem eigenen Unterordner: `data.js` setzt `window.DATA = {...}` mit den Rohdaten aus der Spec, `app.html` lädt `data.js` per `<script src="data.js">` und rendert daraus die UI — inline `<style>` und `<script>`, kein `fetch`, kein Server, kein Build-Schritt. Öffnet per Doppelklick im Browser (`file://`). Details siehe `prototype-builder`.

## Qualitätskriterien

- Alle 3 Apps öffnen per Doppelklick im Browser ohne Konsolenfehler
- Alle 3 erfüllen die Spec (gleiche Funktionalität, andere UX)
- Die Unterschiede sind strukturell, nicht kosmetisch
- Daten kommen ausschließlich aus der jeweiligen `data.js` — keine hardcodierten Inhalte in `app.html`
- Kein Server, kein Backend, keine externen Abhängigkeiten (kein CDN, kein npm, kein Build-Schritt)
- Sonderfälle behandelt (z.B. leerer Filter → Hinweis statt leere Ansicht)

## Output

- `output/YYYY-MM-DD/prototyping/option-a/app.html` + `data.js`
- `output/YYYY-MM-DD/prototyping/option-b/app.html` + `data.js`
- `output/YYYY-MM-DD/prototyping/option-c/app.html` + `data.js`
- `output/YYYY-MM-DD/prototyping/option-comparison.md`

## Format: option-comparison.md

```
# Option Vergleich

## Kern-UI-Entscheidung
[Was ist die zentrale Entscheidung die die drei Varianten unterscheidet?]

## Übersicht

| Kriterium | Option A | Option B | Option C |
|-----------|----------|----------|----------|
| Interaktionsmodell | ... | ... | ... |
| Informationshierarchie | ... | ... | ... |
| Lernkurve für Nutzer | niedrig/mittel/hoch | ... | ... |
| Eignet sich für | ... | ... | ... |

## Trade-offs
**Option A:** [Stärken und Schwächen]
**Option B:** [Stärken und Schwächen]
**Option C:** [Stärken und Schwächen]

## Empfehlung
[Welche Variante für welchen Kontext? Keine pauschale Empfehlung — Bedingungen benennen.]
```
