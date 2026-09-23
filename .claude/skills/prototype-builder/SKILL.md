---
name: prototype-builder
description: Baut einen Zero-Install-HTML-Prototyp (app.html + data.js) aus einer Spec — für eine einzelne Variante eines Features. Für drei Varianten: option-stormer.
allowed-tools: Read, Write
---

> **Hinweis:** Verwende ausschließlich die eingebauten `Read`- und `Write`-Tools. Keine MCP-Tools.

# Referenz: Prototyp bauen

## Was ein Prototyp ist

Eine self-contained `app.html` mit `<style>` und `<script>` inline, die alle UI-Komponenten der Spec implementiert — plus eine `data.js`, die die Rohdaten als `window.DATA` bereitstellt. Kein Server, kein Build-Schritt. Öffnet per Doppelklick im Browser (`file://`). Keine Placeholder, keine TODOs.

## Schritt 0: Run-Verzeichnis bestimmen

Berechne das heutige Datum im Format YYYY-MM-DD. Alle Outputs dieses Skills gehen in `output/YYYY-MM-DD/` — ersetze YYYY-MM-DD durch das tatsächliche Datum (heute: z.B. `output/2026-04-09/`). Erstelle dieses Verzeichnis implizit durch den ersten Write-Aufruf.

## Input

- `output/YYYY-MM-DD/spec-eval/spec.md` und die darin referenzierten Datendateien

## Der HTML-Vertrag

`output/YYYY-MM-DD/prototyping/data.js` übersetzt die Rohdaten aus der Spec (bzw. den referenzierten Datendateien) in ein JS-Objekt und setzt eine globale Variable:

```js
// data.js — Beispiel
window.DATA = {
  items: [
    { name: "...", value: "..." }
  ]
};
```

`output/YYYY-MM-DD/prototyping/app.html` ist EINE Datei. Sie lädt zuerst `data.js` per Skript-Tag, dann liest sie `window.DATA`:

```html
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <title>...</title>
  <style>
    /* alles inline */
  </style>
</head>
<body>
  <div id="app"></div>
  <script src="data.js"></script>
  <script>
    // liest window.DATA, rendert die UI
  </script>
</body>
</html>
```

Kein `fetch`, kein Netzwerk-Request — der Browser blockiert `fetch()` auf lokale Dateien unter `file://`, ein `<script src="...">`-Tag dagegen nicht. Deshalb der Umweg über `data.js` statt einer JSON-Datei.

## Qualitätskriterien

- `app.html` öffnet per Doppelklick im Browser ohne Konsolenfehler
- Alle UI-Komponenten aus der Spec sind implementiert
- Daten kommen ausschließlich aus `data.js` (`window.DATA`) — keine hardcodierten Inhalte in `app.html`
- Sonderfälle behandelt (z.B. leerer Filter → Hinweis statt leere Ansicht)
- Kein Server, kein Backend, keine externen Abhängigkeiten (kein CDN, kein npm, kein Build-Schritt)
- `data.js` enthält valides JavaScript, das ohne Fehler ausgeführt wird

## Output

- `output/YYYY-MM-DD/prototyping/app.html`
- `output/YYYY-MM-DD/prototyping/data.js`
