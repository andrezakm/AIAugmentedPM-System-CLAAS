---
name: kurs
description: Interaktive Version der sechs Woche-5-Circle-Lektionen — Schritt N im Kurs entspricht Lektion N in Circle, live im Repo durchgespielt statt nur gelesen. Aufrufen mit `/kurs`, wenn der Woche-5-System-Kurs durchlaufen werden soll.
---

# Kurs: Woche 5 — Das System

Willkommen in Woche 5. Dieser Kurs ist die interaktive Version der sechs Lektionen, die du diese Woche in Circle liest — gleiche Reihenfolge, gleicher Inhalt, aber hier machst du es live im Repo statt nur zu lesen: **Schritt N im Kurs = Lektion N in Circle.**

Du navigierst mit "weiter" (nächster Schritt) oder "ab Schritt 4" (direkt springen). Du kannst jederzeit pausieren und später weitermachen — sag einfach, bei welchem Schritt du stehen geblieben bist.

**Grobe Zeitplanung:**
- Schritt 1–3 (Struktur, Überblick, Muster): zusammen ca. 25 Minuten
- Schritt 4 (Grund-Flow, mit vier Haltepunkten): anderthalb bis zwei Stunden, wenn du an den Haltepunkten wirklich liest — mit der Abkürzung über `/build-eval` deutlich kürzer. Der größte Einzelschritt.
- Schritt 5 (Türsteher-Flow): ca. 15–20 Minuten
- Schritt 6 (Persona als Linse): ca. 20–25 Minuten

Macht zusammen etwa zweieinhalb bis drei Stunden für den vollständigen Durchlauf. Du musst das nicht an einem Stück machen — am besten verteilst du die Schritte über die Woche, passend zu den Lektionen.

## Für wen — was hast du davon?

**Als PM** siehst du hier zum ersten Mal, wie die einzelnen Skills aus den letzten Wochen zu einem System zusammenwachsen: derselbe Kontext, dieselbe Ablage, dieselbe Übergabe-Logik, egal welcher Skill gerade läuft. Am Ende weißt du nicht nur, welcher Skill was tut, sondern auch, wo du selbst eingreifen würdest — welcher Cluster nicht in dein `context/strategy.md` passt, welche Anfrage zu Recht zurückgeht, welche Punktzahl sich ändert, sobald du eine Persona als Linse davorlegst.

**Als Designerin oder Designer** ist das genauso deins: Eine Persona, ein Interface-Zustand, die Begründung für eine Entscheidung — das sind alles Textdateien, die in dasselbe Fundament aus `context/`, `input/` und `output/` passen, ohne eigenes Tool und eigene Ablage. In Schritt 6 siehst du das konkret: Eine Persona, die du selbst formulieren oder mit formen würdest, verändert direkt, wie eine Opportunity bewertet wird — nicht als Stimmungsbild, sondern als Zahl mit Begründung.

## Lernziele

Nach diesem Kurs weißt du:
- Was aus einzelnen Skills ein System macht — und wo genau der goldene Dreiklang aus Woche 1 dauerhaft eingebaut ist
- Wie der Workspace aufgeteilt ist: die sieben Bereiche, ihre Skills, die zwei Ablagekonventionen für Output
- Welche Grundmuster es gibt, um Skills zu kombinieren — nicht nur die eine vorgegebene Kette
- Wie sich der komplette Grund-Flow anfühlt, vom Rohfeedback bis zur Übergabe, inklusive der vier Stellen, an denen du selbst liest und entscheidest
- Wie ein einzelner Skill als Türsteher vor dir steht, bevor eine Anfrage überhaupt bei dir landet
- Wie ein Ergebnis aus einem Bereich (eine Persona) einen Skill in einem ganz anderen Bereich schärfer macht, ohne dass dieser Skill davon in seiner eigenen Anleitung etwas weiß

---

## Schritt 1 ↔ Lektion 01: Was ist ein System?

Du hast in den letzten Wochen einzelne Skills gebaut und benutzt — einen, der Interviews analysiert, einen, der eine Spezifikation schreibt, einen, der Abnahmekriterien formuliert. Jeder für sich hat funktioniert. Aber jeder stand für sich: eigener kleiner Kontext, kein Wissen davon, was der Skill davor produziert hat. Diese Woche wird daraus ein System — nicht durch mehr Automatisierung, sondern durch denselben goldenen Dreiklang aus Woche 1, dieses Mal dauerhaft eingebaut statt bei jeder Aufgabe neu gedacht:

- **Ergebnis** → landet immer im selben Ordner: `output/`
- **Kontext** → zweigeteilt wie in Woche 1: `context/` ist der permanente, statische Teil (wer ihr seid, welche Strategie ihr verfolgt), `input/` ist der dynamische Teil (das Rohmaterial für genau diesen einen Lauf)
- **Unterschritte** → die Skills selbst. Statt eines riesigen Auftrags von "rohes Feedback" bis "fertiger Handoff" gibt es viele kleine, fokussierte Skills, die hintereinander laufen können

Drei Dinge sorgen dafür, dass das wirklich zusammenklickt:

**Struktur.** `context/`, `input/` und `output/` bilden das Fundament eines ganzen Repos — des Projektordners, der Kontext, Rohdaten, Ergebnisse und die Skills selbst an einem Ort versioniert enthält.

**Der goldene Dreiklang** selbst, wie oben.

**Vereinheitlichung.** Jeder Skill hat dieselbe Form: eine `SKILL.md`, die genau beschreibt was er tut, dazu ein kurzes README als Zusammenfassung. Dieselbe Kontext-Regel für alle. Dieselbe Output-Konvention für alle. Alles Markdown — ein einfaches Textformat mit Überschriften und Listen, ohne Word-Formatierung.

Weil alle Teile dieselbe Form haben und denselben Kontext lesen, passen sie ineinander. Der Output des einen Skills ist automatisch lesbarer Input für den nächsten.

**Kleine Aufgabe:** Öffne `context/company.md` und danach eine beliebige `SKILL.md`, zum Beispiel `.claude/skills/feedback-synthesizer/SKILL.md`. Wirf dann einen kurzen Blick in den Ordner `output/` — du siehst, dass dort bereits einzelne frühere Läufe liegen.

**Reflexion:** Welcher Skill aus den letzten Wochen hätte am meisten von gemeinsamem Kontext profitiert — wo hast du ihm bisher jedes Mal von Neuem erklärt, was er eigentlich schon hätte wissen können?

Sag "weiter" für Schritt 2.

---

## Schritt 2 ↔ Lektion 02: Das System im Überblick

Das System gliedert sich in sieben Bereiche, ungefähr entlang des Wegs, den eine Idee von rohem Material bis zur Übergabe an die Entwicklung nimmt:

```
Discovery     Was sagen Kunden, Nutzer, Daten?
              /feedback-synthesizer · /interview-analyzer · /user-personas

Strategy      Was baut ihr, und warum?
              /opportunity-scorer · /decision-brief · /devils-advocate ·
              /success-metrics · /insight-validator · /business-case-debater

Roadmap       In welcher Reihenfolge?
              /roadmap-intake · /product-roadmap

Spec & Eval   Was genau wird gebaut, wann ist es gut?
              /spec-writer · /eval-writer · /story-map · /build-eval

Prototyping   Funktioniert die Idee als Artefakt?
              /prototype-builder · /option-stormer · /eval-runner

Handoff       Was braucht Dev zum Start?
              /handoff-packager

Meta          Wo stehe ich, was fehlt?
              /system-auditor
```

Alle Skills in allen sieben Bereichen lesen zuerst denselben Grund: den Ordner `context/`. Sieben Dateien liegen dort — `company.md`, `strategy.md`, `product.md`, `team.md`, `metrics.md`, `roadmap.md`, `learnings.md`. Ohne diesen Kontext gibt es keinen Output, für keinen Skill.

Für die Ergebnisse gelten zwei Ablagekonventionen: Lauf-Artefakte — eine Spec, eine Scorecard, ein Prototyp — landen im datierten Ordner `output/YYYY-MM-DD/<bereich>/`, ein Lauf, ein Verzeichnis, nichts wird überschrieben. Lebender Zustand, der über viele Läufe hinweg wächst, liegt dagegen stabil an einem festen Ort: die Roadmap unter `output/roadmap/`, das System-Audit unter `output/meta/`.

Ein Punkt braucht kurz Gewöhnung: Die Skills liegen technisch flach nebeneinander im Ordner `.claude/skills/` — kein Unterordner für Discovery, keiner für Strategy. Das ist der Preis einer bewussten Entscheidung: Alles, was das System kann, ist als Skill gebaut, damit man es teilen, im Team austauschen und über das Menü aufrufen kann. Dafür müssen alle Skills an einem einzigen, festen Ort liegen. Deshalb gibt es ein Inhaltsverzeichnis gleich zweimal: als Text im Ordner `skills/` (ein kurzes README pro Bereich), und visuell als System-Karte unter `doc/System-Karte.html` — dort siehst du alle sieben Bereiche, ihre Skills und den typischen Fluss dazwischen auf einen Blick.

Und noch ein Satz dazu: Diese Ordnerstruktur ist eine sinnvolle Wahl, keine einzig richtige. Wer mit vielen parallelen Projekten arbeitet, könnte unter `output/` zum Beispiel noch einen Unterordner pro Projekt einziehen. Nimm sie als Ausgangspunkt, nicht als Vorgabe.

**Aufgaben:**
1. Öffne `doc/System-Karte.html` im Browser: in VS Code Rechtsklick auf die Datei → „Reveal in Finder" (Mac) bzw. „Reveal in File Explorer" (Windows), dann Doppelklick.
2. Führe `/system-auditor` aus. Er zeigt dir, was in diesem Repo schon ausgefüllt ist und was noch fehlt — per Ampel: ✅ ausgefüllt, ⚠️ nur Template, ❌ fehlt. Ergebnis landet in `output/meta/system-audit.md`.

**Reflexion:** Beim Blick auf die System-Karte — welcher der sieben Bereiche wäre in deinem eigenen Alltag am dünnsten besetzt, wenn du ihn heute nachbauen würdest?

Sag "weiter" für Schritt 3.

---

## Schritt 3 ↔ Lektion 03: Was damit möglich ist

Du kennst jetzt die sieben Bereiche und ihre Skills einzeln. Die eigentliche Frage an dieser Stelle ist selten technisch, sondern eine der Vorstellungskraft: Welche Flows unterstützt ein System aus Skills eigentlich, jenseits der einen vorgegebenen Kette? Sieben Grundmuster:

1. **Ein Skill solo, als Alltagswerkzeug** — zum Beispiel `/devils-advocate` direkt aufrufen, ohne vorher durch Discovery und Strategy zu laufen.
2. **Die Kette entlang, vom Rohmaterial bis zur Übergabe** — der vollständige Weg über alle Stationen, den du in Schritt 4 selbst gehst.
3. **Abkürzungen über einen Orchestrator** — `/build-eval` nimmt dir Spec, Eval und Prototyp in einem Rutsch ab und überspringt automatisch, was schon existiert.
4. **Quer verketten** — die Skills wissen nicht, in welcher Reihenfolge du sie aufrufst. Jeder Output kann in jeden Skill hineingehen, auch in einen, für den er ursprünglich gar nicht gedacht war.
5. **Ein Artefakt als Linse für einen anderen Skill** — der Wert eines Outputs liegt manchmal nicht darin, der nächste Kettenschritt zu sein, sondern einen anderen Skill schärfer zu machen. Genau das siehst du in Schritt 6.
6. **Gleiche Kette, anderer Kontext** — weil jeder Skill seinen Kontext aus `context/` zieht statt ihn fest einzubacken, läuft dieselbe Kette unverändert auch mit einem anderen Unternehmen oder Produkt.
7. **Lebender Zustand, der mit jedem Lauf wächst** — die Roadmap unter `output/roadmap/` und das System-Audit unter `output/meta/` werden mit jedem Lauf fortgeschrieben, nicht neu angelegt.

Ein Bild dazu liegt unter `doc/flows/muster-kombinationen.png` — wirf einen Blick hinein, bevor du weitermachst.

**Reflexion:** Welches dieser sieben Muster würde in deiner eigenen Arbeit diese Woche am meisten helfen — und auf welche konkrete Aufgabe würdest du es anwenden?

Sag "weiter" für Schritt 4.

---

## Schritt 4 ↔ Lektion 04: Flow 1: Der Grund-Flow — vom Rohfeedback zur Übergabe

Das ist der Flow, den du als Erstes komplett durchspielen solltest — das Rückgrat, an dem sich jeder andere Flow orientiert. Acht Skills, eine Kette, vier Stellen, an denen ausdrücklich du liest und entscheidest, nicht Copilot. Rechne für einen ersten vollständigen Durchlauf mit anderthalb bis zwei Stunden — die einzelnen Skill-Läufe dauern jeweils nur wenige Minuten, die Zeit steckt im Lesen und Entscheiden an den vier Haltepunkten.

Wirf vorher noch einmal einen Blick auf `doc/System-Karte.html` und auf `doc/flows/flow1-grund.png` — beide zeigen genau diesen Fluss.

**1. Rohmaterial verdichten.** Alles beginnt im Ordner `input/raw_feedback/` — Slack-Exporte, E-Mail-Threads, interne Notizen, ungefiltert.

```
/feedback-synthesizer input/raw_feedback
```

Ergebnis: `output/YYYY-MM-DD/discovery/feedback-clusters.md` — YYYY-MM-DD steht für das Datum deines Laufs.

**2. Cluster bewerten.**

```
/opportunity-scorer
```

Ergebnis: `output/YYYY-MM-DD/strategy/opportunity-scorecard.md`.

**Haltepunkt 1:** Schau wirklich hin. Sind die Punktzahlen tatsächlich unterschiedlich, oder wurde der Einfachheit halber überall dieselbe Zahl vergeben? Steht hinter jeder Zahl ein Satz aus `context/company.md` oder `context/strategy.md`, oder nur eine Behauptung?

**3. Entscheidung ableiten.**

```
/decision-brief
```

Ergebnis: `output/YYYY-MM-DD/strategy/decision-brief.md`.

**Haltepunkt 2 — der wichtigste:** Lies die Empfehlung. Prüfen, ob die genannten Zahlen wirklich aus dem Feedback stammen. Dann entscheiden, ob du weitergehst.

**4. Spec schreiben.** Sagt der Brief BUILD, kommt eine Weiche, die leicht übersehen wird: `/spec-writer` erwartet als Eingabe einen Brief — und dieser Brief ist an dieser Stelle keine neue Datei, sondern genau die, die du gerade gelesen hast:

```
/spec-writer output/YYYY-MM-DD/strategy/decision-brief.md
```

Ergebnis: `output/YYYY-MM-DD/spec-eval/spec.md`.

**5. Eval schreiben.**

```
/eval-writer
```

Ergebnis: `output/YYYY-MM-DD/spec-eval/eval.md`.

**Haltepunkt 3:** Lies Spec und Eval zusammen, bevor irgendetwas gebaut wird. Deckt jedes Eval-Kriterium wirklich etwas aus der Spec ab?

**6. Prototyp bauen.**

```
/prototype-builder
```

Ergebnis: `output/YYYY-MM-DD/prototyping/app.html` + `data.js`. Öffne `app.html` per Doppelklick im Finder bzw. Explorer — kein Terminal, kein Server, der Browser springt direkt an.

**Abkürzung:** Wer Spec, Eval und Prototyp — also die Schritte 4 bis 6 — in einem Rutsch will statt drei Skills einzeln aufzurufen, nutzt `/build-eval` mit dem Brief-Pfad als Argument — er überspringt automatisch, was schon existiert.

**7. Prototyp prüfen.**

```
/eval-runner
```

Ergebnis: `output/YYYY-MM-DD/prototyping/eval-results.md`.

**Haltepunkt 4:** Schau dir das Ergebnis wirklich an — vor allem jedes UNKLAR, denn das ist kein Ausweichen, sondern ein echter Hinweis, dass du selbst noch einmal reinschauen musst.

**8. Übergabe bündeln.**

```
/handoff-packager
```

Ergebnis: `output/YYYY-MM-DD/handoff/handoff.md` — der letzte Halt vor der Übergabe an die Entwicklung.

**Praktischer Hinweis:** Findet ein Skill den Output eines vorherigen Schritts nicht — zum Beispiel weil zwischen zwei Aufrufen ein neuer Tag angefangen hat und dadurch ein neuer `output/YYYY-MM-DD/`-Ordner entstünde — sag einfach "nimm den letzten Lauf". Copilot sucht dann im zuletzt verwendeten Datumsordner weiter, statt einen leeren neuen anzufangen.

**Reflexion:** An welchem der vier Haltepunkte bist du am längsten hängen geblieben — und was hat dich dort zum Nachdenken gebracht?

Sag "weiter" für Schritt 5.

---

## Schritt 5 ↔ Lektion 05: Flow 2: Ein Skill solo — der Türsteher vor dem PM

Anfragen kommen aus jeder Richtung — eine weitergeleitete Mail, eine Slack-Nachricht, ein Satz im Review, der auf einmal eine neue Idee ist. Die wenigsten liefern genug, um wirklich zu entscheiden, ob sich die Idee lohnt. `/roadmap-intake` übernimmt genau diese erste Station: Er prüft nicht, ob eine Idee gut ist — das kommt später. Er prüft nur, ob genug auf dem Tisch liegt, um überhaupt zu entscheiden. Fünf Punkte, jeder mit Ja oder Nein:

- Ist konkret beschrieben, was gebaut oder geändert werden soll?
- Ist eine Zielgruppe oder ein konkretes Problem benannt — nicht nur eine Lösung?
- Ist der erwartete Nutzen benannt, und woran würde man erkennen, dass er eingetreten ist?
- Gibt es eine Aufwandsschätzung, und sei sie noch so grob?
- Lässt sich ein Bezug zur Strategie herstellen — auch ein offener Zielkonflikt zählt, nur Schweigen dazu nicht?

Fehlt auch nur einer dieser Punkte oder bleibt er zu vage, geht die Anfrage mit konkreten Hinweisen zurück. Sind alle fünf beantwortet, gilt sie als aufgenommen.

**Aufgabe 1 — eine einzelne Anfrage:** Im Ordner `input/roadmap-requests/` liegen drei Beispiel-Anfragen. Nimm dir eine davon vor, zum Beispiel die knappste:

```
/roadmap-intake input/roadmap-requests/01-vertrieb-chatbot.md
```

Lies das Verdikt. Zurückgewiesen? Dann schau dir an, welche der fünf Dimensionen konkret fehlt.

**Aufgabe 2 — alle auf einmal:** Für die Montags-Runde reicht ein einziger Aufruf, der alle Dateien im Ordner nacheinander prüft:

```
/roadmap-intake Prüfe alle Anfragen in input/roadmap-requests/ nacheinander, jede mit eigenem Verdikt.
```

Vergleiche die drei Verdikte. Welche Anfrage kam mit welchen Nachschärfungs-Hinweisen zurück, welche wurde aufgenommen — und war das Ergebnis für dich nachvollziehbar?

**Optional — einen Schritt weiter:** `/product-roadmap` sequenziert aufgenommene Ideen in Now, Next und Later — eine Datei unter `output/roadmap/roadmap.md`, die mit jedem Lauf weiterwächst statt neu geschrieben zu werden. Der Skill sortiert dabei nur, er bewertet nicht selbst: Was aufgenommen, aber noch nicht mit `/opportunity-scorer` bewertet ist, landet zunächst unter "Ungeklärt", bis eine Bewertung vorliegt. Du kannst `/product-roadmap` jetzt probehalber laufen lassen und dir ansehen, wo deine gerade aufgenommenen Anfragen landen.

Ein Bild zu diesem Flow liegt unter `doc/flows/flow2-roadmap-intake.png`.

**Reflexion:** Diese fünf Prüfpunkte sind fest und offen einsehbar. Würdest du sie an Stakeholder in deinem Umfeld weitergeben, bevor sie dir überhaupt eine Anfrage schicken — und was würde sich dadurch bei den Anfragen ändern, die bei dir landen?

Sag "weiter" für Schritt 6.

---

## Schritt 6 ↔ Lektion 06: Flow 3: Persona als Linse — ein Discovery-Ergebnis schärft die Strategie

Dieser Flow zeigt etwas anderes als die vorherigen: Ein Ergebnis, das eigentlich für einen ganz anderen Bereich gebaut wurde, wird zur Linse, durch die ein zweiter Skill blickt — obwohl dieser zweite Skill in seiner eigenen Anleitung nichts davon weiß.

**1. Ausgangspunkt.** Wenn du noch im selben Tages-Ordner arbeitest wie in Schritt 4, kannst du die vorhandenen Feedback-Cluster weiterverwenden. Sonst neu erzeugen:

```
/feedback-synthesizer input/raw_feedback/
```

**2. Personas verdichten.**

```
/user-personas
```

Ergebnis: `output/YYYY-MM-DD/discovery/personas.md`. Entscheidend an diesem Skill ist nicht die fertige Persona, sondern die Disziplin dahinter: Jede Aussage ist entweder mit einer Quelle belegt oder ausdrücklich als Annahme markiert — keine dritte, unmarkierte Kategorie. Falls eigene Interviews fehlen, zeigt `output/discovery/personas-beispiel.md`, wie derselbe Skill auch mit Schreibtisch- und Web-Recherche arbeitet (Modus B, ehrlich niedrigere Konfidenz als bei eigenen Gesprächen).

**3. Ganz regulär bewerten, ohne Linse.**

```
/opportunity-scorer
```

Ergebnis: `output/YYYY-MM-DD/strategy/opportunity-scorecard.md`.

**4. Mit Linse noch einmal bewerten.** Der Opportunity Scorer weiß in seiner eigenen Anleitung nichts von Personas — er ist dafür gebaut, Cluster gegen die Firmenstrategie zu spiegeln, mehr nicht. Nichts hindert dich daran, ihm zusätzlichen Kontext mitzugeben, mit genau diesem Prompt:

```
/opportunity-scorer Lies diesmal zusätzlich
output/YYYY-MM-DD/discovery/personas.md. Gewichte jeden Cluster danach,
welche der Personas er bedient und wie stark — und lass das sichtbar in
Begründung und Fazit einfließen, nicht nur in die drei Standard-Dimensionen.
Speichere das Ergebnis als opportunity-scorecard-mit-linse.md, damit die
erste Scorecard erhalten bleibt.
```

**5. Vergleichen.** Öffne beide Scorecards nebeneinander — `opportunity-scorecard.md` und `opportunity-scorecard-mit-linse.md`. Bleibt die Reihenfolge der Cluster gleich? Wo wird die Begründung konkreter, wo verschiebt sich sogar die Punktzahl, und warum?

Ein Bild zu diesem Flow liegt unter `doc/flows/flow3-persona-linse.png`.

**Reflexion:** Für welchen deiner eigenen Skills oder Entscheidungen wäre eine Persona als Linse hilfreich — nicht um sie neu zu erfinden, sondern um eine bestehende Bewertung genauer zu machen?

Sag "weiter" für den Abschluss.

---

## Abschluss

Damit hast du die sechs Lektionen dieser Woche live durchgespielt: die Struktur des Systems, den Überblick über die sieben Bereiche, die Grundmuster zur Kombination von Skills, und drei konkrete Flows — den vollständigen Grund-Flow, einen Skill solo als Türsteher, und ein Ergebnis als Linse für einen anderen Skill.

Im Lauf der Woche kommen weitere Flows dazu — sie werden hier als weitere Schritte ergänzt, sobald die passende Circle-Lektion live ist, immer mit derselben Regel: Schritt N im Kurs entspricht Lektion N in Circle.

Falls du beim Durchspielen eine eigene Idee für einen Flow hattest — eine Kombination von Skills, die zu deiner konkreten Arbeit passt, oder eine Stelle, an der dein Kontext noch fehlt — notier sie dir jetzt. Sobald du bereit bist, kannst du sie direkt mit Copilot besprechen und ausprobieren, ganz ohne Kurs.
