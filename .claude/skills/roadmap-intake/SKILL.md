---
name: roadmap-intake
description: Prüft eine rohe Stakeholder-Anfrage auf Vollständigkeit, bevor sie in die Roadmap aufgenommen wird — nutze diesen Skill für jede neue Idee, jeden Feature-Wunsch oder jede Anfrage, die noch nicht strukturiert vorliegt.
---

# Skill: Roadmap Intake

Du bist die erste Station für jede neue Anfrage, bevor sie den PM erreicht. Deine Aufgabe ist nicht, die Idee zu bewerten oder zu priorisieren — das passiert später, an anderer Stelle. Du prüfst nur, ob genug auf dem Tisch liegt, um überhaupt eine informierte Entscheidung treffen zu können.

## Input

- Eine kurze Beschreibung der Anfrage, die direkt beim Aufruf übergeben wird, ODER
- eine beim Aufruf benannte Datei unter `input/roadmap-requests/`, ODER
- ist nichts benannt: alle Dateien, die mit Glob unter `input/roadmap-requests/` gefunden werden — liegen mehrere vor, wird jede einzeln geprüft.
- `context/company.md`, `context/strategy.md`, `context/metrics.md` — immer lesen, bevor du bewertest.

Liegt weder ein übergebener Text noch eine benannte Datei vor, und ist `input/roadmap-requests/` leer, kannst du nicht arbeiten — frage nach der Anfrage, statt eine zu erfinden.

## Vorgehen

1. Lies `context/company.md`, `context/strategy.md` und `context/metrics.md` vollständig.
2. Bestimme die zu prüfenden Anfragen: Ist beim Aufruf ein Text oder eine bestimmte Datei benannt, prüfst du genau diese eine. Ist nichts benannt, ermittle per Glob, welche Dateien unter `input/roadmap-requests/` liegen — bei mehreren gehst du sie nacheinander durch und wendest die Schritte 3–6 auf jede einzeln an, mit je eigenem Verdikt (und bei **Aufgenommen** mit je eigener Intake-Datei). Ist der Ordner leer und nichts benannt, frage nach der Anfrage.
3. Prüfe die jeweilige Anfrage gegen fünf universelle Dimensionen (Completeness Gate — kein Scoring, keine Gewichtung, nur: beantwortet oder nicht beantwortet):
   - **Was** — Ist konkret beschrieben, was gebaut oder geändert werden soll?
   - **Für wen / welches Problem** — Ist eine Zielgruppe oder ein konkretes Problem benannt, nicht nur eine Lösung?
   - **Nutzen und Erfolgssignal** — Ist der erwartete Nutzen benannt, und woran würde man erkennen, dass er eingetreten ist?
   - **Grobe Größe/Aufwand** — Gibt es eine Einschätzung, und sei sie noch so grob (Tage/Wochen/Monate oder klein/mittel/groß)?
   - **Fit zur Strategie** — Lässt sich ein Bezug zu `context/strategy.md` herstellen? Auch ein expliziter Zielkonflikt zählt als beantwortet — Schweigen dazu nicht.
4. Ziehe die Schwelle: **Aufgenommen** nur, wenn alle fünf Dimensionen mindestens minimal beantwortet sind und kein offener Widerspruch zu den Constraints in `context/strategy.md` besteht. Fehlt eine Dimension oder ist sie zu vage, um etwas Konkretes daraus abzuleiten, greift **Zurück an Stakeholder**. Die Schwelle ist bewusst einfach und nachvollziehbar — kein verstecktes Scoring, keine Gewichtung einzelner Dimensionen gegeneinander.
5. Bei **Zurück an Stakeholder**: Schreibe keine Datei. Liste jede fehlende oder zu vage Dimension einzeln auf und gib zu jeder einen konkreten Hinweis, wie sie nachgeschärft werden kann — eine Frage, die beantwortet werden müsste, kein pauschales „bitte mehr Details". Die Anfrage soll dadurch beim nächsten Anlauf weiterkommen, nicht nur abgewiesen werden.
6. Bei **Aufgenommen**: Bilde einen Slug aus dem Titel der Idee (klein geschrieben, Leerzeichen durch Bindestriche ersetzt, keine Sonderzeichen) und schreibe den normalisierten Eintrag nach `output/roadmap/intake/<slug>.md`.

## Qualitätskriterien

- Verdikt ist immer eindeutig: **Aufgenommen** oder **Zurück an Stakeholder** — nichts dazwischen.
- Die fünf Prüf-Dimensionen sind in der Rückmeldung immer sichtbar, auch bei Aufnahme — die Schwelle ist transparent, kein stiller Filter.
- Bei **Zurück an Stakeholder** hat jeder fehlende Punkt einen konkreten, umsetzbaren Hinweis — nicht nur die Feststellung, dass etwas fehlt.
- Die Strategie-Fit-Notiz verweist auf eine konkrete Aussage aus `context/strategy.md`, nicht auf eine allgemeine Vermutung.
- Kein numerischer Score, keine Rangfolge zwischen Anfragen — Intake trifft eine Ja/Nein-Entscheidung zur Vollständigkeit, keine Priorisierung.
- Der Handoff-Hinweis am Ende fehlt nie — bei **Aufgenommen** der Hinweis auf den Termin mit dem PM, bei **Zurück an Stakeholder** der Hinweis auf die erneute Einreichung.

## Output-Format — bei Zurück an Stakeholder (keine Datei, nur Rückmeldung)

```
# Roadmap Intake: [Titel oder Kurzbezeichnung der Anfrage]

**Verdikt:** Zurück an Stakeholder

## Was schon da ist
[Kurze Zusammenfassung dessen, was die Anfrage bereits hergibt]

## Was fehlt, und wie es nachgeschärft wird
- **[Fehlende Dimension]:** [Konkrete Frage/Hinweis, wie sie beantwortet werden könnte]
- **[Fehlende Dimension]:** [...]

**Nächster Schritt:** Die ergänzte Anfrage erneut über /roadmap-intake einreichen.
```

## Output-Format — bei Aufgenommen → `output/roadmap/intake/<slug>.md`

```
# [Titel der Idee]

**Status:** Aufgenommen
**Datum:** [Heutiges Datum]

## Problem
[Welches Problem löst die Idee, für wen]

## Für wen
[Zielgruppe/Stakeholder-Gruppe]

## Nutzen und erstes Erfolgssignal
[Erwarteter Nutzen; woran man ihn zuerst erkennen würde]

## Strategie-Fit-Notiz
[Bezug zu context/strategy.md — Fit oder expliziter Zielkonflikt]

## Grober Aufwand
[Einschätzung, so grob wie verfügbar]

## Offene Fragen
- [Frage 1]
- [Frage 2, falls vorhanden]

**Nächster Schritt:** Ein Termin oder eine Kalendereinladung mit dem PM, um die Idee gemeinsam einzuordnen. Diesen Termin simuliert dieser Skill nicht.
```

## Output

Nur bei Verdikt **Aufgenommen** entsteht eine Datei: `output/roadmap/intake/<slug>.md`. Bei **Zurück an Stakeholder** bleibt die Rückmeldung Teil der Antwort — es wird nichts geschrieben.

Liegen mehrere Anfragen vor, gilt das für jede einzeln: Jede geprüfte Anfrage endet entweder mit ihrer eigenen Intake-Datei und dem Hinweis auf den PM-Termin, oder mit ihrer eigenen Rückmeldung und dem Hinweis auf die erneute Einreichung.
