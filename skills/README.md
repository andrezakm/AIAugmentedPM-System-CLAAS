# Skills — semantische Karte

Die ausführbaren Skills liegen technisch **flach** in `.claude/skills/` — dort liest der Agent (Copilot) sie. Diese Karte gliedert sie in die **7 konzeptuellen Bereiche**, damit die Struktur sichtbar bleibt, die in der flachen Ablage verloren geht. Aufruf jeweils mit `/name`.

| Bereich | Frage |
|---|---|
| [Discovery](discovery/) | Verstehen: Was sagen Kunden, Nutzer, Daten? |
| [Strategy](strategy/) | Entscheiden: Was bauen wir — und warum? |
| [Roadmap](roadmap/) | Planen: In welcher Reihenfolge? |
| [Spec & Eval](spec-eval/) | Übergeben: Was genau, wann ist es gut? |
| [Prototyping](prototyping/) | Validieren: Funktioniert die Idee als Artefakt? |
| [Handoff](handoff/) | Abschließen: Was braucht Dev? |
| [Meta](meta/) | Navigieren: Wo stehe ich, was fehlt? |

Details zu jedem Skill: `.claude/skills/[name]/SKILL.md` (Instruktionen) und `.claude/skills/[name]/README.md` (Kurzreferenz). Gesamtübersicht und Flows: die [README.md](../README.md) im Root.

**Zwei Ablage-Konventionen für Outputs:** Lauf-Artefakte (Spec, Eval, Story-Map, Personas, Prototyp …) landen im datierten Run-Ordner `output/YYYY-MM-DD/<bereich>/` — ein Lauf, ein Verzeichnis. *Lebender Zustand*, der über Läufe hinweg wächst (die Roadmap, das System-Audit), liegt stabil unter `output/roadmap/` bzw. `output/meta/`.
