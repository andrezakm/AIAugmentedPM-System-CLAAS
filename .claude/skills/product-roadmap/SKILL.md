---
name: product-roadmap
description: Sequenziert Ideen mit vorhandenem Priorisierungssignal (Opportunity-Scorecard oder Decision Brief) in eine lebende Roadmap (Now/Next/Later, optional Timeline) — nutze diesen Skill, um Reihenfolge und Status sichtbar zu machen, nicht um Ideen neu zu bewerten. Eine aufgenommene Idee allein, ohne eigenes Priorisierungssignal, reicht dafür nicht — sie landet unter „Ungeklärt".
---

# Skill: Product Roadmap

Du bringst bereits priorisierte Ideen in eine Reihenfolge. Priorisiert heißt hier konkret: Es liegt eine Opportunity-Scorecard oder ein Decision Brief zu der Idee vor. Die Bewertung selbst — ist die Idee gut, passt sie strategisch — ist an dieser Stelle schon passiert; das ist die Aufgabe anderer Skills weiter vorne im Prozess. Eine aufgenommene Idee ohne ein solches Signal ist noch nicht priorisiert, egal wie vollständig ihr Intake-Eintrag ist — sie wartet sichtbar, statt geraten einsortiert zu werden. Deine Aufgabe ist reines Sequenzieren: was kommt zuerst, was wartet, was ist schon versprochen, wofür reicht die Kapazität nicht.

## Input

- `output/roadmap/intake/*.md` — aufgenommene, aber noch nicht priorisierte Kandidaten (Glob).
- Opportunity-Scorecards und Decision Briefs, falls vorhanden. Diese können je nach vorherigem Lauf datiert oder undatiert abgelegt sein — verwende ein Glob-Muster, das beide Formen findet, z. B. `output/**/strategy/opportunity-scorecard.md` und `output/**/strategy/decision-brief.md`. Bei mehreren Treffern gilt der zuletzt geänderte bzw. der mit dem jüngsten Datum im Pfad.
- `context/strategy.md` — strategische Richtung und Constraints.
- `context/roadmap.md` — was bereits committed ist.
- `context/team.md` — verfügbare Kapazität.
- `context/metrics.md` — für Erfolgssignale, falls ein Kandidat darauf verweisen kann.
- `output/roadmap/roadmap.md`, falls bereits vorhanden — die aktuelle Roadmap, die fortgeschrieben statt ersetzt wird.

## Vorgehen

1. Lies `context/strategy.md`, `context/roadmap.md`, `context/team.md` und `context/metrics.md` vollständig.
2. Sammle mit Glob alle verfügbaren Quellen: aufgenommene Intake-Kandidaten, Opportunity-Scorecards, Decision Briefs. Existiert keine einzige dieser Quellen, gibt es nichts zu sequenzieren — melde das, statt eine leere Roadmap zu erfinden.
3. Ordne Scorecards und Decision Briefs den passenden Intake-Einträgen zu, wo beide existieren. Es gibt keine ID, die beide verknüpft — matche über Thema/Titel. Ist nicht eindeutig, ob zwei Einträge dieselbe Idee beschreiben, führe sie als getrennte Items und vermerke den möglichen Overlap, statt sie zusammenzulegen.
4. Prüfe, ob `output/roadmap/roadmap.md` bereits existiert. Falls ja, lies sie vollständig — sie ist der Ausgangspunkt, kein leeres Blatt.
5. Ordne jedes Item einem Status zu:
   - **Committed** — steht bereits so in `context/roadmap.md`.
   - **Kandidat** — hat eine Opportunity-Scorecard oder einen Decision Brief, ist aber noch nicht committed.
6. Sequenziere die Kandidaten in Now / Next / Later. Nutze dabei ausschließlich vorhandene Bewertungen — eine BUILD-Empfehlung aus einem Decision Brief zieht nach vorn, ein hoher Score aus der Scorecard hilft bei der Reihenfolge innerhalb einer Spalte. Berechne selbst keinen neuen Score und ändere keine bestehende Empfehlung.
7. Respektiere die Kapazität aus `context/team.md`: Now darf nicht mehr enthalten, als die dort beschriebene Kapazität realistisch leisten kann. Was aus Kapazitätsgründen nicht in Now passt, wandert nach Next, auch wenn es inhaltlich stark bewertet wurde.
8. Für Items ohne eigenes Priorisierungssignal (ein Intake-Eintrag ohne Scorecard/Brief, oder eine widersprüchliche Datenlage): nicht raten. Diese Items kommen in den Abschnitt „Ungeklärt", nicht in Now/Next/Later — mit dem Hinweis, zuerst eine Opportunity-Scorecard (`/opportunity-scorer`) oder einen Decision Brief zu erstellen.
9. Wurde beim Aufruf explizit eine Timeline-Ansicht verlangt: erzeuge zusätzlich eine einfache chronologische Tabelle (Zeitraum/Reihenfolge statt Now/Next/Later). Ohne diese ausdrückliche Anfrage bleibt Now/Next/Later die einzige Ansicht.
10. Schreibe oder aktualisiere `output/roadmap/roadmap.md`. War bereits eine Version vorhanden, fülle den Abschnitt „Was sich geändert hat" mit einer echten Differenz (neu, verschoben, erledigt, entfernt). Beim allerersten Lauf steht dort „Erster Stand".

## Qualitätskriterien

- Kein Item wird neu bewertet oder gescored — Einordnung basiert ausschließlich auf vorhandenen Scorecards, Briefs und Intake-Einträgen.
- Now respektiert die Kapazität aus `context/team.md` explizit und nachvollziehbar.
- Jedes eingeordnete Item enthält: Outcome/Ziel, die Wette, grobe Größe, Abhängigkeiten, Erfolgssignal, Status (Committed/Kandidat).
- Erfolgssignal verweist auf `context/metrics.md` oder die Quelldatei, falls dort vorhanden — sonst steht explizit „kein Erfolgssignal hinterlegt", statt eines erfundenen.
- Committed und Kandidat sind für jedes Item eindeutig unterscheidbar.
- Items ohne ableitbare Priorität landen sichtbar unter „Ungeklärt" statt irgendwo einsortiert zu werden, mit dem Hinweis auf eine Opportunity-Scorecard oder einen Decision Brief als nächsten Schritt.
- Wo eine Zuordnung zwischen Intake-Eintrag und Scorecard/Brief nicht eindeutig ist, stehen beide Items getrennt mit einem Overlap-Hinweis, statt stillschweigend zusammengelegt zu werden.
- „Was sich geändert hat" ist bei jedem Lauf ausgefüllt — nie leer, nie eine reine Kopie des vorherigen Stands.

## Output-Format — `output/roadmap/roadmap.md`

```
# Product Roadmap

**Zuletzt aktualisiert:** [Datum]

## Was sich geändert hat
[Neu / verschoben / erledigt / entfernt seit dem letzten Stand. Beim ersten Lauf: "Erster Stand."]

## Now
### [Item-Titel]
**Status:** Committed / Kandidat
**Outcome/Ziel:** [...]
**Die Wette:** [Was gebaut wird]
**Grobe Größe:** [...]
**Abhängigkeiten:** [...]
**Erfolgssignal:** [Verweis auf context/metrics.md oder Quelle]

## Next
### [Item-Titel]
[gleiche Felder wie oben]

## Later
### [Item-Titel]
[gleiche Felder wie oben]

## Ungeklärt / ohne ableitbare Priorität
- [Item] — [warum keine Einordnung möglich war, z. B. „kein Priorisierungssignal vorhanden — zuerst /opportunity-scorer oder einen Decision Brief erstellen"]
```

Optional, nur auf explizite Anfrage — Timeline-Ansicht als Alternative/Ergänzung:

```
## Timeline

| Zeitraum/Reihenfolge | Item | Status | Abhängigkeiten |
|---|---|---|---|
| [...] | [...] | Committed/Kandidat | [...] |
```

## Output

Schreibe oder aktualisiere `output/roadmap/roadmap.md`. Die Datei ist lebend — sie wird bei jedem Lauf fortgeschrieben, nicht neu angelegt.
