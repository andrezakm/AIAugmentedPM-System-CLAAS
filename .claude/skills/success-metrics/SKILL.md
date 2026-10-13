---
name: success-metrics
description: Definiert, woran ein Feature oder ein strategischer Bet als erfolgreich gilt — North-Star-, Input- und Guardrail-Metriken mit Baseline und Zielwert, oder eine einfache Erfolgskriterien-Liste; aufrufen, sobald eine Spec oder ein Decision Brief steht und die Outcome-Frage noch offen ist.
---

# Skill: Success Metrics

Du legst fest, woran wir erkennen, dass ein Produkt oder Feature tatsächlich gewirkt hat — die Outcome-Ebene, die sonst fehlt. Lies zuerst `context/company.md` und `context/strategy.md`, dazu `context/metrics.md` für Baseline-Werte und `context/product.md` für den bestehenden Produktkontext.

## Schritt 0: Run-Verzeichnis und Grundlage bestimmen

Berechne zuerst das heutige Datum im Format YYYY-MM-DD. Alle Outputs dieses Skills gehen in `output/YYYY-MM-DD/` — ersetze YYYY-MM-DD durch das tatsächliche Datum (heute: z. B. `output/2026-04-09/`). Erstelle dieses Verzeichnis implizit durch den ersten Write-Aufruf.

Bestimme dann, wofür Erfolgsmetriken definiert werden:

1. Wurde beim Aufruf ein Thema oder ein Dateipfad direkt genannt (z. B. „/success-metrics Onboarding-Flow")? Dann das als Grundlage nehmen.
2. Sonst: versuche `output/YYYY-MM-DD/spec-eval/spec.md` zu lesen. Existiert die Datei, ist das die Grundlage — Feature-/Spec-Ebene.
3. Sonst: versuche `output/YYYY-MM-DD/strategy/decision-brief.md` zu lesen. Existiert die Datei, ist das die Grundlage — strategischer Bet.
4. Existiert keines von beidem und wurde kein Thema übergeben: frage den Anwender kurz, wofür Erfolgsmetriken definiert werden sollen.

## Input

- `output/YYYY-MM-DD/spec-eval/spec.md` — Feature/Spec (bevorzugte Grundlage, falls vorhanden)
- `output/YYYY-MM-DD/strategy/decision-brief.md` — strategischer Bet (Alternative)
- Thema oder Dateipfad, direkt beim Aufruf übergeben
- `context/company.md` — Wer wir sind und wie wir arbeiten
- `context/strategy.md` — Unsere strategische Richtung und Constraints
- `context/metrics.md` — Baseline-Werte
- `context/product.md` — Bestehender Produktkontext

## Vorgehen

1. Lies die bestimmte Grundlage vollständig, dazu alle vier Context-Files.
2. Wähle den Modus (siehe unten): North-Star-Framework als Standard, Erfolgskriterien-Liste als schlanke Alternative.
3. Baue den Output gemäß dem gewählten Modus (siehe Output-Format).
4. Jede Metrik bzw. jedes Kriterium braucht eine Definition, eine Begründung warum sie das Ergebnis zeigt, und wo möglich einen Bezug zu `context/metrics.md`.
5. Schließe den Absatz „Outcome vs. Verhalten" ein — ohne ihn bleibt der Unterschied zur eval-writer/eval-runner-Prüfung unklar.
6. Benenne das Anti-Pattern kurz und konkret auf das Thema bezogen.

### Modus wählen

Standard ist das **North-Star-Framework**. Wechsle zur schlankeren **Erfolgskriterien-Liste**, wenn:
- der Anwender das beim Aufruf explizit sagt (z. B. „keine North Star, nur Erfolgskriterien", „einfache Liste reicht"), oder
- das Thema zu klein oder zu früh für eine eigene North-Star-Metrik ist (z. B. ein einzelnes UI-Detail ohne eigenständigen Nutzerpfad, oder ein sehr früher Bet ohne belastbare Baseline).

Im Zweifel: North-Star-Framework — es ist differenzierter und zwingt zur Trennung von Treiber- und Grenz-Metriken. Bei der Erfolgskriterien-Liste den Moduswechsel kurz begründen.

## Qualitätskriterien

- Jede Metrik bzw. jedes Kriterium ist konkret messbar — keine „wird besser" ohne Zahl
- Baseline ist entweder aus `context/metrics.md` belegt oder explizit als „unbekannt — zuerst messen" markiert
- Die North-Star-Kennzahl ist eine einzelne, konkrete Zahl — kein Bündel aus mehreren Metriken
- Guardrails sind Grenzen, keine zweiten Ziele
- Der Outcome-vs-Verhalten-Absatz fehlt nie
- Die Vanity-Metriken-Warnung ist konkret auf das Thema bezogen, nicht generisch
- Keine Spekulation über Zielwerte, die nicht aus Kontext oder Grundlage ableitbar sind

## Output-Format

### Modus „North-Star-Framework"

Schreibe `output/YYYY-MM-DD/strategy/success-metrics.md` mit folgendem Format:

```
# Success Metrics: [Feature-/Bet-Name]

**Modus:** North-Star-Framework
**Datum:** [Heutiges Datum]

## Outcome vs. Verhalten
[1–2 Sätze: Diese Datei misst Outcome — hat sich ein Nutzer- oder Geschäftsergebnis bewegt? Das ist etwas anderes als die Verhaltens-/Ausgabe-Prüfung von eval-writer/eval-runner, die nur prüft, ob der Prototyp die Spec Kriterium für Kriterium erfüllt.]

## North-Star-Metrik
**Ein Satz:** [Was die North Star inhaltlich zeigt]
**Kennzahl:** [Eine konkrete, messbare Größe]

## Input-Metriken (leading)
Treiben die North Star und sind früher sichtbar als sie.

| Metrik | Definition | Warum sie die North Star treibt |
|---|---|---|
| ... | ... | ... |

## Guardrail-Metriken
Was sich NICHT verschlechtern darf, während wir auf die North Star optimieren.

| Metrik | Definition | Grenze |
|---|---|---|
| ... | ... | ... |

## Baseline, Zielwert, Zeithorizont

| Metrik | Baseline | Zielwert | Zeithorizont |
|---|---|---|---|
| North Star | [aus context/metrics.md, sonst „unbekannt — zuerst messen"] | ... | ... |
| [Input-Metrik] | ... | ... | ... |

## Leading vs. Lagging
[1 Absatz: welche der genannten Metriken leading sind (früh sichtbar, weniger direkter Beweis) und welche lagging (spät sichtbar, aber direkter Beweis für den Outcome).]

## Anti-Pattern: Vanity-Metriken
[1–2 Sätze, konkret auf das Thema bezogen: welche naheliegende Metrik gut aussehen würde, aber nichts über den echten Outcome aussagt, und wie man vermeidet, auf eine einzelne Zahl hinzutricksen statt die Ursache zu verbessern.]
```

### Modus „Erfolgskriterien"

Schreibe `output/YYYY-MM-DD/strategy/success-metrics.md` mit folgendem Format:

```
# Success Metrics: [Feature-/Bet-Name]

**Modus:** Erfolgskriterien
**Datum:** [Heutiges Datum]
**Warum dieser Modus:** [1 Satz]

## Outcome vs. Verhalten
[gleicher Absatz wie oben]

## Erfolgskriterien
[3–5 messbare Erfolgsbedingungen. Jede mit Baseline und Zielwert, wo möglich.]

1. [Kriterium] — Baseline: [Wert oder „unbekannt — zuerst messen"], Zielwert: [Wert], Zeithorizont: [Zeitraum]
2. ...

## Anti-Pattern: Vanity-Metriken
[gleicher Absatz wie oben]
```

## Output

Schreibe die fertige Datei nach `output/YYYY-MM-DD/strategy/success-metrics.md`.
