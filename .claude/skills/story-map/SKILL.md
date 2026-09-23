---
name: story-map
description: Wenn eine Spec vorliegt (oder ersatzweise ein Brief) und in eine nach Aktivitäten, Tasks und Release-Slices geordnete Story Map übersetzt werden soll — die Naht zwischen Spec und Bau.
allowed-tools: Read, Write, Glob
---

> **Hinweis:** Verwende ausschließlich die eingebauten `Read`-, `Write`- und `Glob`-Tools. Keine MCP-Tools.

# Referenz: Story Map schreiben

## Was eine Story Map ist

Eine Story Map ordnet Arbeit nach Jeff Patton in einem zweidimensionalen Raster an: horizontal die User Journey als Backbone — **Aktivitäten** (die großen Ziele) über **Tasks** (die konkreten Schritte dorthin) — vertikal die **Release-Slices**, vom dünnen Walking Skeleton bis zur vollen Tiefe. Sie ist die Naht zwischen Spec und Bau: Sie übersetzt das Was in eine Reihenfolge, in der es entsteht.

## Schritt 0: Run-Verzeichnis bestimmen

Berechne das heutige Datum im Format YYYY-MM-DD. Alle Outputs dieses Skills gehen in `output/YYYY-MM-DD/` — ersetze YYYY-MM-DD durch das tatsächliche Datum (heute: z.B. `output/2026-04-09/`). Erstelle dieses Verzeichnis implizit durch den ersten Write-Aufruf.

## Input

- `output/YYYY-MM-DD/spec-eval/spec.md` — die Spec des aktuellen Runs, falls vorhanden
- Fallback, falls keine Spec existiert: ein Brief, dessen Pfad beim Aufruf übergeben wird (z.B. „Führe story-map aus für input/mein-brief.md")

Prüfe mit Glob, was tatsächlich vorliegt, bevor du liest.

## Kontext

Lies vor der Arbeit:
- `context/company.md` + `context/strategy.md` — immer
- `context/product.md` — bestehender Stack und bestehende Features, damit die Backbone realistisch an das Produkt anschließt
- `context/team.md` — wer welche Rolle hat, für plausible Rollen in den Stories und für Setup-/Admin-Aktivitäten, die sonst leicht vergessen werden

Ohne Kontext kein Output.

## Vorgehen

1. **Backbone bauen.** Identifiziere aus Spec oder Brief die großen **Aktivitäten** — die Ziele, die Nutzer erreichen wollen — und darunter die konkreten **Tasks**, die einzelnen Schritte dorthin.
2. **Stories unter jedem Task sammeln.** Format: „Als [Rolle] möchte ich [Aktion], damit [Nutzen]."
3. **Jede Story einer Release-Slice zuordnen.** Release 1 ist der Walking Skeleton — durchgängig funktionsfähig, aber dünn. Spätere Releases fügen Tiefe, Qualität und UX hinzu, keine neuen Aktivitäten.
4. **Neglect no one.** Prüfe gegen `context/team.md`, ob Setup- oder Admin-Aktivitäten fehlen — das Rückgrat braucht eine Wirbelsäule, auch unsichtbare Arbeit gehört ins Skelett.

## Struktur einer Story Map

```
# Story Map: [Feature-Name]

## Aktivität: [Ziel, z.B. "Leads anreichern"]
[Ein Satz: worum geht es in dieser Aktivität]

### Task: [Konkreter Schritt, z.B. "Leadliste einlesen"]

#### Release 1 — Walking Skeleton
- Als [Rolle] möchte ich [Aktion], damit [Nutzen].
- Als [Rolle] möchte ich [Aktion], damit [Nutzen].

#### Release 2 — [Tiefe / Qualität / UX]
- Als [Rolle] möchte ich [Aktion], damit [Nutzen].

### Task: [Nächster Schritt]
...

## Aktivität: [Nächste Aktivität]
...
```

## Qualitätskriterien

- Backbone zuerst: Aktivitäten und Tasks stehen fest, bevor Stories geschrieben werden
- Jede Story folgt dem Format „Als … möchte ich … damit …" — kein Fragment, kein abgekürzter Satz
- Jede Story ist einer Release-Slice zugeordnet — keine Story ohne Slice
- Release 1 ist end-to-end funktionsfähig, nicht nur ein isolierter Teilschritt
- Setup- und Admin-Aktivitäten sind enthalten, nicht vergessen
- Rollen stammen aus `context/team.md` oder der Spec — keine erfundenen Rollen
- Kein Spekulieren über Dinge, die nicht in Spec, Brief oder Kontext stehen

## Output

`output/YYYY-MM-DD/spec-eval/story-map.md`
