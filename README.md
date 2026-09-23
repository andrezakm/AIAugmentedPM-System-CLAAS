# PM Workspace — AI-Augmented PM, Woche 5

Ein modulares System für Product Manager, die mit GitHub Copilot arbeiten. Von rohem Feedback bis zum Dev-Handoff — in einem Repo, mit einem gemeinsamen Kontext.

Dies ist das fünfte Modul des Kurses **AI-Augmented PM**: Die ersten Wochen bauen einzelne Skills. Diese Woche fügt sich alles zu **einem System** zusammen. Der Unterschied zwischen vielen einzelnen Skills und *einem System* ist **Kontext** — ein gemeinsames Fundament, das jeder Skill liest, bevor er arbeitet.

---

## Schnellstart

1. **[Repo als ZIP herunterladen](https://github.com/andrezakm/AIAugmentedPM-System-CLAAS/archive/refs/heads/main.zip)** und entpacken.
2. Den entpackten Ordner in **VS Code** öffnen.
3. **GitHub Copilot** im Agent-Modus öffnen — die Skills erscheinen im `/`-Menü.

Dann im Chat:

```
/kurs
```

`/kurs` ist der geführte Einstieg — er erklärt das System Schritt für Schritt. **Wichtig:** Copilot muss *diesen* Ordner geöffnet haben (hier liegt `.claude/skills/`), sonst sind die Kurse und Skills nicht verfügbar.

> Prototypen ansehen: Die Skills erzeugen eine `app.html` (plus `data.js`). Doppelklick im Browser — kein Setup, kein Server, keine Installation.

---

## Die Kurse

Zwei aufeinander aufbauende Kurse führen durch das System — jeder mit kleinen Aufgaben zum Mitdenken und Anpassen:

| Aufruf | Präsentation | Thema |
|---|---|---|
| `/kurs` | [doc/PM-System-Übersicht.html](doc/PM-System-Übersicht.html) | Das System verstehen — Struktur, Flows, Anpassung |
| `/zeig_mir_teamwork` | [doc/PM-Teamwork-Übersicht.html](doc/PM-Teamwork-Übersicht.html) | Teamwork — Zimmer / Wohnzimmer, Übergabe-Flow |

**Optionaler Zusatz:** `/PTW-workshop` ([doc/PTW-Workshop-Anleitung.html](doc/PTW-Workshop-Anleitung.html)) — ein Play-to-Win-Strategie-Workshop mit vollständiger Fallstudie (LEGO 2004).

---

## Dokumentation — wo finde ich was?

- **Visuelle System-Karte:** [doc/System-Karte.html](doc/System-Karte.html) — die sieben Bereiche, alle Skills, der Fluss und die PM↔Dev-Grenze auf einen Blick (im Browser öffnen)
- **Flow-Grafiken:** [`doc/flows/`](doc/flows/) — die Flows als Bild (PNG, direkt in VS Code ansehbar) und als HTML: die sieben Kombinationsmuster, der Grund-Flow, ein Skill solo, Persona als Linse
- **Kurse & Präsentationen:** die HTML-Dateien in [`doc/`](doc/) (im Browser öffnen)
- **Skill-Details:** pro Skill ein `README.md` unter `.claude/skills/[name]/`
- **Semantische Skill-Karte:** [`skills/`](skills/) — die sieben Bereiche mit je einer Kurzreferenz
- **Kontext-Regel:** [CLAUDE.md](CLAUDE.md) — was jeder Skill liest, bevor er arbeitet
- **PTW-Demo-Lauf** (Beispiel-Output): Falldokumente in [`input/ptw-workshop/`](input/ptw-workshop/), vollständiger Lauf in [`output/2026-06-14/strategy/ptw-lego/`](output/2026-06-14/strategy/ptw-lego/)

---

## Skill-Übersicht

Die Skills liegen technisch flach in `.claude/skills/` — konzeptuell sind sie in 7 Bereiche gegliedert:

```
Discovery
├── /feedback-synthesizer   Rohes Feedback → thematische Cluster
├── /interview-analyzer     Interviews → Einzel-Analysen + Synthese
├── /user-personas          Belege oder Web-Recherche → evidenzbasierte Personas
└── /slack-importer         Slack-Export → strukturiertes Feedback (Platzhalter)

Strategy
├── /opportunity-scorer     Cluster → Scorecard (Vision / Wiederholbarkeit / Baubarkeit)
├── /decision-brief         Scorecard → 1-Pager (BUILD / SKIP / MEHR DATEN)
├── /success-metrics        Spec/Bet → North-Star-, Input- & Guardrail-Metriken
├── /devils-advocate        Brief → Annahmen-Kritik + Verdikt
├── /insight-validator      Insight → Validierung gegen Kontext + Experiment-Design
├── /business-case-debater  Vollständige Analyse: Research → Debatte → Synthese
└── /PTW-workshop           Play-to-Win Strategie-Workshop: 5 Perspektiven → Choice Cascade

Roadmap
├── /roadmap-intake         Stakeholder-Anfrage → Türsteher: zurück mit Hinweisen oder aufgenommen
└── /product-roadmap        Aufgenommene Ideen → sequenzierte Roadmap (Now / Next / Later)

Spec & Eval
├── /spec-writer            Brief → Spec (Was, nicht Wie)
├── /eval-writer            Spec → 8–12 pass/fail Kriterien
├── /story-map              Spec → User-Story-Map (Backbone + Release-Slices)
└── /build-eval             Orchestrator: Brief → Spec + Eval + Prototyp

Prototyping
├── /prototype-builder      Spec → eine HTML-App (app.html + data.js, Doppelklick)
├── /option-stormer         Spec → 3 strukturell verschiedene HTML-Apps + Vergleich
└── /eval-runner            Eval + App → PASS/FAIL/UNKLAR pro Kriterium

Handoff
└── /handoff-packager       Alle Artefakte → Cover-Sheet für Dev

Meta
└── /system-auditor         Workspace-Audit: was fehlt, was als nächstes tun
```

---

## Typischer Flow

```
input/raw_feedback/         input/interviews/
        ↓                           ↓
/feedback-synthesizer       /interview-analyzer
        ↓
/user-personas              (das „Wer" evidenzbasiert festhalten)
        ↓
/opportunity-scorer
        ↓
/decision-brief
        ↓
/devils-advocate
        ↓
/success-metrics            (woran erkennen wir, dass es gewirkt hat?)
        ↓
/spec-writer [brief]
        ↓
/story-map                  (Backbone + Release-Slices → Brücke zum Bau)
        ↓
/option-stormer             (oder /build-eval für alles auf einmal)
        ↓
/eval-runner
        ↓
/handoff-packager

Daneben, als lebender Zustand:
/roadmap-intake  →  /product-roadmap   (Anfragen filtern → in die Roadmap einordnen)
```

Lauf-Artefakte landen in `output/YYYY-MM-DD/` — ein Run, ein Verzeichnis. Lebender Zustand (Roadmap, System-Audit) liegt stabil unter `output/roadmap/` bzw. `output/meta/`.

---

## Architektur

- **Skills:** `.claude/skills/[name]/SKILL.md` — aufgerufen mit `/name`
- **Kontext:** `context/` — wird von jedem Skill gelesen (Regel in `CLAUDE.md`)
- **Input:** `input/` — Rohdaten, Briefs, Datendateien
- **Output:** `output/YYYY-MM-DD/` pro Lauf; `output/roadmap/` und `output/meta/` als lebender Zustand
- **Scripts:** `scripts/` — persönliche Sandbox für neue Skills in Entwicklung

`CLAUDE.md` ist bewusst kurz. Details zu jedem Skill: `.claude/skills/[name]/README.md`.

---

## Empfohlener Kurs-Flow

```
Schritt 1 — Alleine starten
  /kurs                System verstehen, Notizen machen · context/ befüllen
                       /system-auditor · ersten Flow manuell durchlaufen

Schritt 2 — Mit dem Team
  /zeig_mir_teamwork   Teamwork-Prinzipien (Zimmer / Wohnzimmer)

Schritt 3 — Plan machen
  „Hier sind meine Notizen aus den Kursen. Hilf mir, einen konkreten Plan zu
   erstellen: was passe ich an, welchen Flow starte ich, was baue ich neu?"
```

---

## Verzeichnisstruktur

```
.
├── README.md            ← dieses Dokument
├── CLAUDE.md            Kontext-Regel — was jeder Skill liest
├── context/             das Fundament: company, strategy, product, team, …
├── input/               Rohdaten (inkl. ptw-workshop/ Fallbeispiel)
├── output/              Ergebnisse: output/YYYY-MM-DD/ pro Lauf, output/roadmap/ + output/meta/ lebend
├── doc/                 die HTML-Präsentationen (inkl. System-Karte), Flow-Grafiken in doc/flows/
├── skills/              semantische Karte der 7 Bereiche (je ein README)
├── scripts/             persönliche Sandbox für neue Skills
└── .claude/skills/      die ausführbaren Skills (je mit eigenem README)
```
