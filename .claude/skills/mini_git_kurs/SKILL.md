---
name: mini_git_kurs
description: Interaktiver 12-Schritte-Kurs zu Git für PM-Teams — Branches, Pull Requests, Merge, Konflikte, GitHub Copilot als Git-Assistent. Aufrufen mit `/mini_git_kurs`, nach `/zeig_mir_teamwork`.
---

# Mini-Git-Kurs: Versionierung und Teamwork

Git ist das Fundament für geteilte Infrastruktur — für Code, Skills, Context-Files, Artefakte. Ein gemeinsamer Projektordner, den Git beobachtet, heißt Repository, kurz Repo. Dieser Kurs erklärt die Grundprinzipien und die Kommandos (die Befehle), die du für den PM-Workspace-Workflow brauchst.

Der Kurs hat 12 Schritte. Du navigierst mit "weiter" (nächster Schritt) oder "Schritt X" (direkt springen).

**Kein Vorwissen nötig.** Wer Git schon kennt, kann ab Schritt 6 einsteigen (der PM-spezifische Workflow).

**Gut zu wissen:** Du hast zwei Helfer, die dir die Mechanik abnehmen. Der erste ist GitHub Copilot im Agent-Modus: Copilot kann Git-Befehle im Terminal ausführen (das Terminal ist das Eingabefenster für Befehle, in VS Code unten eingebaut). Es zeigt dir den Befehl und führt ihn erst aus, wenn du bestätigst. Du kannst also einfach sagen "erstelle einen neuen Branch und committe meine Änderungen" — Copilot schlägt die passenden Befehle vor. Der zweite Helfer ist VS Code selbst: Es hat eine eingebaute Ansicht namens "Quellcodeverwaltung" (englisch Source Control), in der du siehst, welche Dateien sich geändert haben, Änderungen committest und Branches wechselst. Schritt 10 zeigt, wie beides zusammenspielt.

**Und noch etwas:** Du kannst Copilot während des Kurses jederzeit umgangssprachlich fragen. "Was ist nochmal der Unterschied zwischen add und commit?" oder "Ich verstehe Branches nicht — erklär mir das anders." Copilot antwortet, und du sagst "weiter" wenn du bereit bist.

---

## Lernziele

Nach diesem Kurs weißt du:
- Was Git ist und warum es für PM-Teams relevant ist
- Den Unterschied zwischen lokal (auf deinem Rechner) und remote (auf GitHub, im Internet)
- Die Kommandos für den täglichen Workflow
- Wie der Weg einer Änderung aussieht: Branch (deine eigene Arbeitskopie) → Pull Request (die Bitte ans Team, draufzuschauen) → Review → Merge (das Zusammenführen in den gemeinsamen Hauptstand)
- Wie du GitHub Copilot und die Quellcodeverwaltung in VS Code als Git-Assistenten einsetzt

---

## Schritt 1: Was ist Git — und warum braucht ein PM das?

Git ist ein Versionierungssystem. Es merkt sich jede Änderung an Dateien — wer was wann geändert hat, und warum.

**Was das für dich bedeutet:**

- Du kannst jederzeit zurück. Jeder Stand ist gespeichert.
- Du siehst wer was geändert hat. Kein "wer hat das nochmal angepasst?"
- Du kannst parallel arbeiten. Du und ein Kollege ändern gleichzeitig verschiedene Dinge — ohne euch zu überschreiben.
- Du kannst Änderungen reviewen (prüfend durchsehen) bevor sie für alle gelten.

**Warum das für den pm-workspace zentral ist:**

Im pm-workspace sind Skills, Context-Files und `CLAUDE.md` (die Datei mit den Grundregeln, die Copilot beim Arbeiten liest) geteilte Infrastruktur. Wenn du `context/strategy.md` änderst, sollen alle die neue Version haben. Wenn du einen Skill verbesserst, sollen alle davon profitieren. Git ist der Mechanismus der das ermöglicht — kontrolliert, nachvollziehbar, rückgängig-machbar.

**Git ≠ GitHub.** Git ist das Werkzeug, ein Programm auf deinem Rechner. GitHub (oder GitLab, Bitbucket) ist die Plattform im Internet, die eine gemeinsame Kopie des Repos speichert — man nennt diese Kopie das Remote. Du brauchst beides.

**Für euch bei CLAAS: euer GitHub-Konto.** Ihr habt über Copilot bereits ein GitHub-Konto — mit genau diesem Konto meldest du dich in VS Code bei Copilot an. Dasselbe Konto brauchst du auch auf github.com, um das gemeinsame Repo zu sehen und später Pull Requests zu öffnen. Ein zweites Konto ist nicht nötig.

**Reflexion:** Wo verlierst du heute Zeit weil es keine klare "eine Wahrheit" gibt — bei Docs, Entscheidungen, Konfigurationen?

Sag "weiter" für Schritt 2.

---

## Schritt 2: Die drei Grundbegriffe

**Repository (Repo)**
Der Ordner der von Git beobachtet wird. Alle Dateien darin, ihre gesamte Geschichte. Im pm-workspace ist das der Workspace-Ordner mit `context/`, `input/`, `output/` und `.claude/skills/`.

Es gibt zwei Versionen davon:
- **Lokal** — auf deinem Rechner. Hier arbeitest du.
- **Remote** — auf GitHub. Das ist die geteilte Wahrheit. Alle sehen dasselbe.

**Commit**
Ein gespeicherter Zustand. Wie ein Foto des Repos zu einem bestimmten Zeitpunkt. Jeder Commit hat eine Nachricht ("Strategy: Fokus auf Enterprise") und einen Zeitstempel. Die Summe aller Commits ist die Geschichte des Repos.

**Branch**
Eine Abzweigung. Du arbeitest auf einem Branch, ohne den Hauptstand (`main`) zu berühren. Erst wenn du fertig bist und jemand drüber geschaut hat, kommt es rein — dieses Zusammenführen heißt Merge.

```
main  ──●──●──●──────────────────●──▶
              \                 /
               ●──●──●  (Branch)
```

Das ist der Kern der Zusammenarbeit: jeder arbeitet auf seinem Branch, `main` bleibt stabil.

**Reflexion:** Was wäre der Vorteil wenn `context/strategy.md` eine sichtbare Geschichte hätte — wer hat was wann geändert, und mit welcher Begründung?

Sag "weiter" für Schritt 3.

---

## Schritt 3: Lokal und Remote — die zwei Welten

```
LOKAL (dein Rechner)          REMOTE (GitHub)
─────────────────────         ───────────────
Working Directory             origin/main
      ↓  git add
Staging Area
      ↓  git commit
Local Repo (History)
      ↓  git push              ← Änderungen hochladen
      ↑  git pull              ← Änderungen holen
```

**Was das bedeutet:**

Wenn du eine Datei änderst, weiß Git davon noch nicht. Du musst ihr sagen: "diese Änderung will ich merken" (`git add` — die Datei kommt in die Staging Area, eine Art Vorbereitungsbereich für den nächsten Commit) und dann "jetzt speichern" (`git commit`). Erst mit `git push` (Push = hochschieben) landet es auf GitHub — für alle sichtbar.

Umgekehrt: wenn ein Kollege etwas geändert und gepusht hat, musst du mit `git pull` (Pull = herunterziehen) holen was neu ist. Git macht das nicht automatisch.

**Die wichtigste Konsequenz:** Bevor du anfängst zu arbeiten — `git pull`. Damit du auf dem aktuellen Stand bist.

**Für euch bei CLAAS: ZIP-Ordner und Repo.** Ihr habt den pm-workspace bisher als ZIP heruntergeladen und entpackt. Ein entpackter ZIP-Ordner enthält die Dateien, aber keine Git-Geschichte — er ist noch kein Git-Repo. Wenn du dort `git status` ausführst, antwortet Git mit einer Meldung wie "not a git repository". Das ist keine Störung, es heißt nur: Git beobachtet diesen Ordner (noch) nicht. Es gibt zwei Wege, das zu ändern:

- **Zum Ausprobieren** machst du den Ordner selbst zu einem Repo. Öffne in VS Code die Quellcodeverwaltung (das Symbol in der linken Seitenleiste) und klicke auf "Repository initialisieren". Oder bitte Copilot im Agent-Modus darum: "Mach aus diesem Ordner ein Git-Repo." So kannst du add, commit, Branches und die Anzeige der Änderungen in Ruhe üben. Ein solches Übungs-Repo existiert nur auf deinem Rechner und hat kein Remote — `git push` und `git pull` funktionieren dort deshalb nicht.
- **Für echtes Teamwork** braucht ihr ein gemeinsames Repo auf GitHub, das jeder per Clone auf den eigenen Rechner holt. Ein Clone ist eine vollständige Kopie samt Geschichte und bleibt mit GitHub verbunden — das unterscheidet ihn vom ZIP-Download.

**Git muss installiert sein.** Damit Git-Befehle laufen, muss das Programm Git auf dem Rechner installiert sein. Fehlt es, weist VS Code in der Quellcodeverwaltung darauf hin. Auf Firmenrechnern erledigt die Installation gegebenenfalls die IT.

Sag "weiter" für Schritt 4.

---

## Schritt 4: Die Basis-Kommandos

**Wo stehe ich?**
```bash
git status
```
Zeigt: was wurde geändert, was ist gestaged (für den nächsten Commit vorgemerkt), auf welchem Branch du bist. Erstes Kommando wenn du dich orientieren willst. Dieselbe Übersicht zeigt dir VS Code in der Quellcodeverwaltung.

```bash
git log --oneline
```
Zeigt die letzten Commits — kompakt, eine Zeile pro Commit. Gute Übersicht über was zuletzt passiert ist.

**Repo holen (einmalig):**
```bash
git clone <url>
```
Kopiert ein Remote-Repo auf deinen Rechner (Clone). Einmal pro Repo, am Anfang. Die Adresse (`<url>`) findest du auf der Repo-Seite bei GitHub hinter dem grünen "Code"-Button. Du kannst Copilot auch bitten, den Clone für dich im Terminal auszuführen — gib ihm dafür die Adresse.

**Aktuellen Stand holen:**
```bash
git pull
```
Holt alle neuen Commits vom Remote. Vor jedem Arbeitsbeginn ausführen.

**Zum Üben:** Wenn du die Kommandos in deinem entpackten ZIP-Ordner ausprobieren willst, mach ihn zuerst zum Repo (siehe Schritt 3). `git status`, `git log`, `git add` und `git commit` funktionieren dann lokal. `git clone` und `git pull` brauchen ein echtes Remote.

**Reflexion:** Wann hast du zuletzt eine Datei überschrieben die jemand anderes gerade bearbeitet hat? Was wäre mit `git pull` + Branches passiert?

Sag "weiter" für Schritt 5.

---

## Schritt 5: Änderungen committen

Du hast `context/strategy.md` angepasst. Jetzt willst du das speichern.

**Teil 1 — Stagen:**
```bash
git add context/strategy.md
```
Sagt Git: "diese Datei soll im nächsten Commit sein." Nur was gestaged ist, kommt in den Commit.

Mehrere Dateien auf einmal:
```bash
git add context/strategy.md context/company.md
```

**Teil 2 — Committen:**
```bash
git commit -m "Strategy: Fokus auf Enterprise-Segment ab Q3"
```
Speichert den Zustand mit einer Nachricht. Die Nachricht erklärt **warum** — nicht was (das sieht man im Diff, also in der Gegenüberstellung von alter und neuer Fassung).

Gute Commit-Nachrichten:
- `context: Strategie-Update nach Q1-Review` ✓
- `skill: decision-brief um Risk-Sektion ergänzt` ✓
- `update` ✗ (zu vage)

**Teil 3 — Pushen:**
```bash
git push
```
Lädt deine Commits auf GitHub hoch. Jetzt sehen es alle.

*Beim ersten Push eines neuen Branches:*
```bash
git push -u origin mein-branch-name
```
(`origin` ist der Name, den Git dem Remote gibt — also GitHub.) In einem Übungs-Repo ohne GitHub-Verbindung (siehe Schritt 3) meldet `git push` einen Fehler. Das ist erwartbar, denn es gibt dort kein Remote, zu dem hochgeladen werden könnte.

**Dasselbe in VS Code:** In der Quellcodeverwaltung siehst du alle geänderten Dateien. Mit dem Plus neben einer Datei merkst du sie für den Commit vor (Stagen), in das Textfeld oben schreibst du die Commit-Nachricht, und ein Klick auf "Commit" speichert den Stand. Welcher Weg dir lieber ist — Befehle, Klicks oder eine Ansage an Copilot — bleibt dir überlassen; das Ergebnis ist dasselbe.

Sag "weiter" für Schritt 6.

---

## Schritt 6: Branches — der PM-Workflow

Direkt auf `main` arbeiten ist eine schlechte Idee im Team. Branches sind die Lösung.

**Neuen Branch erstellen:**
```bash
git checkout -b update/strategy-enterprise
```
Erstellt den Branch und wechselt direkt drauf. Konvention: `typ/kurze-beschreibung`.

Gängige Typen im pm-workspace:
- `update/` — Context-Files anpassen
- `skill/` — neuen Skill hinzufügen oder verbessern
- `fix/` — Fehler korrigieren

**Branch wechseln:**
```bash
git checkout main
git checkout update/strategy-enterprise
```
In VS Code steht der Name des aktuellen Branches unten links in der Statusleiste, und auch die Quellcodeverwaltung lässt dich den Branch wechseln.

**Welche Branches gibt es?**
```bash
git branch
```
Zeigt alle lokalen Branches. Der aktuelle ist mit `*` markiert.

**Der vollständige Ablauf:**
```bash
git pull                                    # aktuellen Stand holen
git checkout -b skill/opportunity-scorer-v2 # Branch erstellen
# ... Änderungen machen ...
git add .claude/skills/opportunity-scorer/SKILL.md
git commit -m "skill: opportunity-scorer um Impact-Dimension erweitert"
git push -u origin skill/opportunity-scorer-v2
# → Pull Request auf GitHub öffnen
# → Kollege reviewt, mergt
git checkout main && git pull               # zurück zu main, Stand aktualisieren
```

Sag "weiter" für Schritt 7.

---

## Schritt 7: Pull Requests — Review und Merge

Ein Pull Request (PR) ist keine Git-Funktion — es ist eine GitHub-Funktion. Aber es ist der zentrale Übergangs-Mechanismus.

**Was ein PR ist:**
Du sagst dem Team: "Ich habe etwas geändert. Bitte schaut drüber bevor es in `main` geht."

**Was in einem PR passiert:**
1. Du öffnest ihn auf GitHub (Button: "New pull request")
2. Du beschreibst was du geändert hast — und warum. Den Text kannst du dir im Chat von Copilot entwerfen lassen, wenn du ihm sagst, was du geändert hast.
3. Ein Kollege liest den Diff (welche Zeilen haben sich geändert?)
4. Kollege sagt OK → Merge (die Änderung wird in `main` zusammengeführt). Oder: Kollege macht Kommentare → du passt an → nochmal schauen
5. Nach dem Merge: alle holen sich den neuen Stand mit `git pull`

**Was in einem PM-Workspace-PR typischerweise drin ist:**
- Context-Update: "Strategy nach Q1-Review angepasst — neuer Fokus Enterprise"
- Skill-Verbesserung: "decision-brief: Risk-Sektion ergänzt basierend auf Feedback von Ben"
- Neuer Skill: "skill/stakeholder-mapper: neuer Skill aus Pawel Huryns Repo adaptiert"

**Die Faustregel:** Ein PR = eine Sache. Nicht fünf Änderungen auf einmal. Macht Review einfacher.

**Reflexion:** Was wäre die erste Änderung die du als PR einbringen würdest — an Skills, Context oder CLAUDE.md?

Sag "weiter" für Schritt 8.

---

## Schritt 8: Konflikte — wenn zwei dasselbe geändert haben

Manchmal hat ein Kollege dieselbe Datei geändert die du gerade bearbeitest. Git nennt das einen **Merge-Konflikt**: Es kann die beiden Fassungen nicht von allein zusammenführen und bittet dich zu entscheiden.

```
<<<<<<< HEAD
Unser Fokus liegt auf SMB-Kunden mit 10-100 Mitarbeitern.
=======
Strategischer Fokus: Enterprise ab 500 Mitarbeitern.
>>>>>>> update/strategy-enterprise
```

Was das bedeutet:
- `<<<<<<< HEAD` — deine aktuelle Version
- `=======` — Trennlinie
- `>>>>>>> branch-name` — die andere Version

**Was tun:**
1. Datei öffnen, den Konflikt lesen
2. Entscheiden welche Version richtig ist (oder beide kombinieren)
3. Die Marker-Zeilen (`<<<<`, `====`, `>>>>`) löschen
4. `git add datei.md`
5. `git commit`

Wenn dir die beiden Fassungen unübersichtlich vorkommen, kannst du Copilot bitten, sie dir in einfachen Worten gegenüberzustellen. Welche Version stimmt, entscheidest du — du kennst den Inhalt.

**Tipp:** Konflikte vermeiden ist besser als sie lösen. Kurzlebige Branches, häufige Pulls, klare Zuständigkeiten (wer darf `context/strategy.md` ändern?) reduzieren Konflikte stark.

Sag "weiter" für Schritt 9.

---

## Schritt 9: .gitignore — was Git ignorieren soll

Nicht alles soll ins Repo. Im pm-workspace gibt es eine `.gitignore`-Datei, eine einfache Textdatei, die festlegt was Git ignoriert:

```
# Output-Artefakte — nie committen
output/**
!output/**/.gitkeep

# Python-Umgebung (falls du lokal Python nutzt)
.venv/
__pycache__/

# macOS
.DS_Store
```

Schau gern in die `.gitignore` in deinem Workspace-Ordner: Sie folgt derselben Idee und enthält zusätzlich ein paar Ausnahmen für den LEGO-Beispiel-Run, der als Lehrmaterial im Repo liegen soll.

**Warum `output/` nicht ins Repo gehört:**
Output ist persönlich. Jeder macht seine eigenen Runs. Dein `output/2026-04-11/` ist dein Zimmer — nicht das Wohnzimmer. Außerdem werden Output-Files schnell groß (Prototypen, PDFs, Logs).

**Was `.gitkeep` ist:**
Git trackt (beobachtet) keine leeren Ordner. `.gitkeep` ist eine leere Datei die nur da ist damit der Ordner existiert. Das `!output/**/.gitkeep` in der `.gitignore` sagt: ignoriere alles in output/ — außer `.gitkeep`-Files. So bleibt die Ordnerstruktur erhalten.

**Eigene Einträge hinzufügen:**
```
# Eigene Notizen — nicht teilen
notes/
*.local.md
```

Sag "weiter" für Schritt 10.

---

## Schritt 10: Copilot macht Git für dich

Wenn du in VS Code mit GitHub Copilot im Agent-Modus arbeitest, kann Copilot Git-Befehle im Terminal für dich ausführen. Es zeigt dir den Befehl vor der Ausführung und wartet auf deine Bestätigung — lies ihn kurz, bevor du bestätigst, dann behältst du den Überblick.

**Was du einfach sagen kannst:**

> "Erstelle einen neuen Branch `update/strategy-q2` und committe `context/strategy.md` mit der Nachricht 'Strategy: Q2-Fokus Enterprise'."

Copilot schlägt vor:
```bash
git checkout -b update/strategy-q2
git add context/strategy.md
git commit -m "Strategy: Q2-Fokus Enterprise"
git push -u origin update/strategy-q2
```

> "Zeig mir was sich seit dem letzten Commit geändert hat."

```bash
git diff HEAD
```

> "Ich habe Änderungen an drei Skill-Files gemacht. Committe alles auf einem neuen Branch."

Copilot schaut mit `git status`, staged die richtigen Files, erstellt Branch und Commit.

**Der zweite Weg: die Quellcodeverwaltung in VS Code.**
Wenn du lieber klickst als formulierst: Die Quellcodeverwaltung zeigt dir jederzeit, welche Dateien sich geändert haben, lässt dich Änderungen committen und Branches wechseln. Das ist besonders praktisch, um vor einem Commit noch einmal zu sehen, was alles drin wäre. Beide Wege führen zum selben Ergebnis, und du kannst sie mischen — etwa Copilot den Branch anlegen lassen und die Änderungen selbst in der Quellcodeverwaltung durchsehen.

**Was du weiterhin selbst machst:**
- Pull Requests öffnen (das ist auf GitHub, nicht im Terminal)
- Merge-Konflikte inhaltlich entscheiden (du weißt was richtig ist, Copilot nicht)
- Den finalen Merge (bewusste Entscheidung)
- Die Befehle bestätigen, die Copilot vorschlägt

**Die Faustregel:** Mechanik kann Copilot. Inhalt und Entscheidung bleibst du.

**Reflexion:** Welche Git-Aktionen würdest du am liebsten einfach ansagen — ohne die Kommandos tippen zu müssen?

Sag "weiter" für Schritt 11.

---

## Schritt 11: Häufige Situationen — was tue ich wenn...

Jede dieser Situationen kannst du auch in einem Satz an Copilot geben — die Befehle darunter zeigen dir, was dann im Terminal passiert.

**"Ich will den aktuellen Stand holen bevor ich anfange."**
```bash
git pull
```

**"Ich habe Änderungen gemacht und will sie teilen."**
```bash
git checkout -b update/meine-aenderung
git add <dateien>
git commit -m "Kurze Erklärung warum"
git push -u origin update/meine-aenderung
# → PR auf GitHub öffnen
```

**"Ein Kollege hat etwas gemergt. Ich will den neuen Stand."**
```bash
git checkout main
git pull
```

**"Ich will sehen was sich geändert hat."**
```bash
git status          # welche Dateien sind neu/geändert?
git diff            # was genau hat sich geändert?
git log --oneline   # welche Commits gab es?
```

**"Ich habe versehentlich auf main gearbeitet statt auf einem Branch."**
```bash
git stash                           # Änderungen kurz weglegen
git checkout -b fix/mein-branch     # Branch erstellen
git stash pop                       # Änderungen zurückbringen
```

**"Ich will einen alten Stand einer Datei wiederherstellen."**
```bash
git log --oneline context/strategy.md    # welche Commits gab es?
git checkout <commit-hash> -- context/strategy.md
```
(Der `<commit-hash>` ist die Kennung eines Commits — die kurze Zeichenfolge, die in `git log --oneline` vor der Nachricht steht.)

Sag "weiter" für Schritt 12.

---

## Schritt 12: Zusammenfassung — das Cheat Sheet

```
TÄGLICH
───────────────────────────────────────────────
git pull                    Aktuellen Stand holen
git status                  Wo stehe ich?
git log --oneline           Was ist zuletzt passiert?

ÄNDERUNGEN MACHEN
───────────────────────────────────────────────
git checkout -b typ/name    Neuen Branch erstellen
git add <datei>             Datei stagen
git commit -m "Warum"       Commit erstellen
git push -u origin <branch> Hochladen + PR öffnen

NACH DEM MERGE
───────────────────────────────────────────────
git checkout main           Zurück zu main
git pull                    Neuen Stand holen

IM NOTFALL
───────────────────────────────────────────────
git stash                   Änderungen kurz weglegen
git stash pop               Zurückbringen
git diff                    Was hat sich geändert?
```

**Der PM-Workflow in einem Satz:**
`pull → branch → ändern → add → commit → push → PR → review → merge → pull`

**Mit Copilot:**
Mechanik ansagen, Befehle bestätigen, Entscheidungen selbst treffen.

---

**Finale Reflexion:**

Du hast diesen Kurs durchgearbeitet. Dabei hast du Schritte gelesen, vielleicht Dinge ausprobiert, vielleicht sogar Skills oder Context-Files angepasst.

Stell dir vor, du hast während des Kurses etwas im pm-workspace verbessert — eine Reflexionsfrage schärfer formuliert, einen Skill angepasst, einen Tipp hinzugefügt. Du denkst: das wäre gut für alle Kursteilnehmer, Markus sollte das übernehmen.

**Was müsstest du tun?**
Und: **Was müsste Markus tun, um deine Änderung wirklich zu übernehmen?**

Denk kurz nach — du weißt jetzt alles was du brauchst um diese Frage zu beantworten.

---

**Kurs abgeschlossen.**

Git ist kein Entwickler-Tool — es ist Infrastruktur für jeden der kontrolliert zusammenarbeiten will. Im pm-workspace ist es der Mechanismus der Zimmer und Wohnzimmer verbindet.

**Zur Beruhigung:** Du musst die Kommandos nicht auswendig kennen. Das Cheat Sheet in Schritt 12 ist immer da. Copilot führt sie auf Ansage aus, sobald du bestätigst, und die Quellcodeverwaltung in VS Code zeigt dir jederzeit, wo du stehst. Was zählt ist das Prinzip — Branch, PR, Review, Merge. Den Rest erledigt die Praxis.

---

## Zusatzmaterial

- `doc/Git-Grundlagen.html` — Präsentation: Grundprinzipien und Kommandos im Überblick
- `/zeig_mir_teamwork` — Wie das alles im Team zusammenspielt
- GitHub Docs: docs.github.com/en/get-started
