---
name: user-personas
description: Verdichtet vorhandene Discovery-Belege oder Schreibtisch-/Web-Recherche zu 1–3 evidenzbasierten Personas, bei denen jede Aussage entweder ein Beleg oder eine markierte Annahme ist. Aufrufen, wenn Feedback-Cluster oder Interviews in handlungsfähige Personas übersetzt werden sollen, oder wenn noch keine eigenen Interviews vorliegen und eine erste, ehrlich niedrig-konfidente Persona-Hypothese aus öffentlichen Quellen gebraucht wird.
---

# Skill: User Personas

Du verdichtest verfügbare Belege zu 1–3 Personas. Personas sind fast immer Geschmackssache — jeder im Raum hat eine Meinung dazu, und in der klassischen Form (Stockfoto, Alter, Hobbys) hält kaum eine einer ernsthaften Design-Kritik stand. Der Wert dieses Skills liegt nicht darin, "die eine richtige Persona" zu finden, sondern in der Disziplin, mit der er gebaut wird: jede Aussage ist entweder mit einer Quelle belegt oder ausdrücklich als Annahme markiert. Diese Disziplin ist es, was eine Persona vor Kritik standhaft macht — nicht die Behauptung, sie sei "wahr".

## Schritt 0: Run-Verzeichnis bestimmen

Berechne das heutige Datum im Format YYYY-MM-DD. Alle Outputs dieses Skills gehen in `output/YYYY-MM-DD/` — ersetze YYYY-MM-DD durch das tatsächliche Datum (heute: z. B. `output/2026-04-09/`). Erstelle dieses Verzeichnis implizit durch den ersten Write-Aufruf. Das mitgelieferte Beispiel `output/discovery/personas-beispiel.md` liegt bewusst außerhalb der Run-Ordner — es ist eine feste Demo, kein Lauf-Ergebnis.

## Kontext lesen

Lies vor der Ausführung:
1. `context/company.md` — immer
2. `context/strategy.md` — immer
3. `context/product.md` — immer für diesen Skill (ohne Produktverständnis werden Jobs-to-be-Done beliebig)
4. `context/metrics.md` — nur, wenn Ziele oder Erfolgsmessgrößen der Zielgruppe für die Personas eine Rolle spielen (z. B. wenn ein Gain oder ein Auslöser direkt auf eine Kennzahl verweist). `context/team.md` und `context/roadmap.md` werden für diesen Skill nicht gebraucht.

Ohne `context/company.md` und `context/strategy.md` kein Output — abbrechen und den Anwender informieren.

## Input: zwei Modi

Beide Modi können sich ergänzen. Wenn unklar ist, welcher Modus gilt, frag kurz nach, bevor du recherchierst.

### Modus A — Primärbelege (höhere Konfidenz)

Prüfe per Glob, ob eigene Discovery-Outputs im heutigen Run-Verzeichnis vorliegen, z. B. `output/YYYY-MM-DD/discovery/feedback-clusters.md`, Interview-Synthesen oder andere `.md`-Dateien unter `output/YYYY-MM-DD/discovery/` bzw. einem vom Anwender genannten Ordner. Wenn vorhanden: Das ist deine primäre Quelle. Lies alle gefundenen Dateien vollständig, bevor du Personas ableitest.

### Modus B — Schreibtisch-/Web-Recherche (niedrigere Konfidenz)

Wenn keine oder zu dünne Primärbelege vorliegen — etwa ganz am Anfang eines Projekts, bevor eigene Interviews existieren —, verdichtest du stattdessen öffentlich zugängliche Quellen zur Zielgruppe: Branchenberichte und Analystenstudien, Produktbewertungen (z. B. auf Vergleichsportalen), Foren und Communities, Stellenanzeigen (sie zeigen reale Aufgaben, Tools und Verantwortlichkeiten der Zielrolle), sowie Fallstudien und Vergleichsseiten von Anbietern im relevanten Markt.

Jede verwendete Quelle wird mit Titel und URL zitiert. Die Konfidenz wird ehrlich niedriger eingeordnet als bei Primärbelegen — Schreibtisch-/Web-Recherche ersetzt keine eigenen Interviews, sie liefert eine geprüfte erste Hypothese. Wo eine Quelle selbst ein wirtschaftliches Interesse an einer bestimmten Sichtweise hat (z. B. ein Anbieter-Blog im gleichen Markt), notiere das als möglichen Bias statt es unkommentiert als neutrale Evidenz zu behandeln.

## Vorgehen

1. **Kontext lesen** — wie oben.
2. **Belege sammeln** — Modus A: alle gefundenen Discovery-Dateien vollständig lesen. Modus B: mehrere unabhängige Quellen recherchieren, nicht nur eine; wo möglich Originalseiten abrufen statt nur Suchergebnis-Schnipsel zu übernehmen.
3. **Ohne zu werten lesen, dann Muster suchen** — sammle wiederkehrende Verhaltens- und Bedarfsmuster, bevor du sie einer Persona zuordnest.
4. **Segmentieren** — bilde 1–3 Personas entlang unterschiedlicher Verhaltens-/Bedarfsmuster, nicht entlang Demografie oder Meinungen einzelner Stakeholder (siehe Anti-Muster unten).
5. **Pro Persona die volle Struktur füllen** (siehe unten) — jede Aussage einzeln als Beleg oder Annahme kennzeichnen.
6. **Anti-Muster-Check** — bevor du abschließt, prüfe jede Persona explizit gegen die vier Anti-Muster unten. Wenn eine Persona durchfällt, schärfe sie nach oder streiche sie.
7. **Konfidenz und offene Annahmen dokumentieren** — pro Persona.
8. **Schreiben.**

## Evidenzdisziplin — der eigentliche Wert dieses Skills

Jede Aussage in einer Persona ist eine von zwei Kategorien, und das wird im Text sichtbar markiert:

- **Beleg** — mit Quelle. Bei Modus A: Zitat oder konkrete Paraphrase mit Verweis auf Datei/Interview. Bei Modus B: Zitat oder Datenpunkt mit Quellentitel und URL.
- **Annahme** — ausdrücklich als Annahme gekennzeichnet, inklusive eines kurzen Hinweises, wie sie sich prüfen ließe ("so ließe sich das prüfen: …").

Es gibt keine dritte Kategorie. Keine erfundenen Demografie-Details ("Anna, 34, zwei Kinder, mag Yoga"), die als Fakt auftreten, nur weil sie eine Persona lebendiger wirken lassen. Wirkt eine Persona dünn, weil die Evidenz dünn ist — dann ist das die ehrliche Aussage, nicht ein Anlass, Lücken mit erfundenen Details zu füllen.

## Struktur pro Persona

Jede Persona (ca. eine halbe Seite) deckt ab:

- **Archetyp/Rolle** — ein Rollen- oder Verhaltensbegriff, kein Stockfoto-Steckbrief. Beschreibt, welche Position/Situation diese Person hat, nicht wer sie als Privatperson ist.
- **Kontext/Situation** — in welchem Umfeld agiert diese Person, welche Constraints prägen ihren Alltag.
- **Jobs-to-be-Done** — funktional, emotional, sozial. Was will diese Person erledigen, wie will sie sich dabei fühlen, wie will sie vor anderen dastehen.
- **Pains** (mit Beleg) — konkrete Reibung, nicht abstrakt.
- **Gains / gewünschte Ergebnisse** — was zählt als Erfolg aus ihrer Sicht.
- **Aktuelle Workarounds** — was tut diese Person heute, in Ermangelung einer besseren Lösung.
- **Auslöser/Entscheidungsmoment** — welches Ereignis bringt diese Person dazu, aktiv zu werden oder eine Kaufentscheidung zu treffen.
- **Wo unterversorgt** — welche Bedürfnisse bestehende Lösungen (inkl. Wettbewerber) erkennbar nicht abdecken.
- **Konfidenz-Einschätzung** — hoch/mittel/niedrig, mit Begründung (Modus, Anzahl unabhängiger Quellen, Qualität der Evidenz).
- **Annahmen, die wir noch prüfen müssen** — eigener Abschnitt, keine Fußnote. Je Annahme: was wir annehmen und wie wir es prüfen könnten.

## Segmentierung

Segmentiere nach **Verhalten und Bedarf**, nicht nach Demografie (Alter, Geschlecht, Branche als alleiniges Kriterium). Zwei Personen mit identischem Jobtitel können unterschiedliche Personas sein, wenn sie unterschiedlich handeln und unterschiedliche Jobs-to-be-Done haben — und zwei Personen mit unterschiedlichem Titel können dieselbe Persona sein, wenn ihr Verhalten und Bedarf übereinstimmen.

## Anti-Muster, die dieser Skill ausdrücklich vermeidet

- **Der "elastische Nutzer"** — eine Persona, so vage formuliert, dass sie zu jedem beliebigen Stakeholder-Wunsch passt und sich nie widerspricht. Wenn eine Persona jede Feature-Idee im Raum rechtfertigen könnte, ist sie zu elastisch.
- **Demografie-Theater** — Alter, Hobbys, erfundene Vornamen und Stockfotos, die Tiefe vortäuschen, aber nichts über Verhalten, Pains oder Jobs-to-be-Done aussagen.
- **Persona-als-Marketing-Fiktion** — eine Persona, geschrieben um eine bereits getroffene Entscheidung im Nachhinein zu rechtfertigen, statt um sie zu prüfen.
- **Eine Persona pro Stakeholder-Meinung** — die Anzahl der Personas folgt der Anzahl der Meinungen im Raum ("Vertrieb will X, Support will Y, also zwei Personas"), statt der Anzahl beobachtbarer Verhaltensmuster in den Belegen.

## Ehrlicher Rahmen

Persona-Erstellung ist angreifbar — das lässt sich nicht wegargumentieren, es lässt sich nur ehrlich machen. Diese Personas erheben nicht den Anspruch, "die Wahrheit" über eine Zielgruppe zu sein. Sie sind der aktuell beste, nachvollziehbare Stand: was belegt ist, ist belegt; was angenommen wird, ist als Annahme sichtbar. Das ist der Unterschied zwischen einer Persona, die einer Design-Kritik standhält, und einer, die bei der ersten kritischen Nachfrage in sich zusammenfällt.

## Output-Format

```markdown
# Personas: [Projekt/Produkt]

**Modus:** [A – Primärbelege / B – Schreibtisch-/Web-Recherche / kombiniert]
**Quellenbasis:** [kurze Zusammenfassung: welche Dateien bzw. wie viele unabhängige öffentliche Quellen]

---

## Persona 1: [Archetyp/Rolle]

**Kontext/Situation:** [1–2 Absätze]

**Jobs-to-be-Done**
- Funktional: [...]
- Emotional: [...]
- Sozial: [...]

**Pains**
- [Pain] — Beleg: "[Zitat]" ([Quelle])
- [Pain] — Annahme: [Aussage] (so ließe sich das prüfen: [...])

**Gains / gewünschte Ergebnisse**
- [...]

**Aktuelle Workarounds**
- [...]

**Auslöser/Entscheidungsmoment**
- [...]

**Wo unterversorgt**
- [...]

**Konfidenz-Einschätzung:** [hoch/mittel/niedrig] — [Begründung]

**Annahmen, die wir noch prüfen müssen**
- [Annahme] — so ließe sich das prüfen: [...]

---

## Persona 2: ...

---

## Quellen
[Bei Modus B: Titel + URL je Quelle. Bei Modus A: Dateipfade der verwendeten Discovery-Outputs.]
```

## Output

Schreibe `output/YYYY-MM-DD/discovery/personas.md` (1–3 Personas, je ca. eine halbe Seite, beleg-zitiert). Nennt der Anwender explizit einen anderen Pfad, verwende diesen stattdessen.

## Qualitätskriterien

- Jede Aussage ist eindeutig als Beleg oder Annahme markiert — keine Vermischung, keine dritte, unmarkierte Kategorie
- Keine erfundenen Demografie-Details, die als Fakt auftreten
- Segmentierung folgt Verhalten/Bedarf, nicht Demografie oder Stakeholder-Meinung
- Maximal 3 Personas, jede auf das Wesentliche begrenzt (~halbe Seite)
- Bei Modus B: jede Quelle mit Titel und URL zitiert, Konfidenz explizit niedriger markiert als bei Primärbelegen, wirtschaftliche Interessen von Quellen (z. B. Anbieter-Blogs) benannt statt verschwiegen
- Jede Persona explizit gegen die vier Anti-Muster geprüft
- Abschnitt "Annahmen, die wir noch prüfen müssen" ist substanziell, nicht ein Pflicht-Halbsatz
- Alle Outputs auf Deutsch mit korrekten Umlauten (ä, ö, ü, ß)

## Fehlerbehandlung

- Fehlt `context/company.md` oder `context/strategy.md`: abbrechen, Anwender informieren, keinen Output schreiben.
- Weder Primärbelege noch verwertbare Recherche-Ergebnisse verfügbar: keine Persona erzwingen. Dem Anwender ehrlich melden, dass die Evidenzlage nicht reicht, statt eine Persona ohne Substanz abzuliefern.
- Widersprüchliche Belege innerhalb einer Zielgruppe (z. B. eine Quelle sagt X, eine andere das Gegenteil): den Widerspruch benennen statt ihn zu glätten — entweder als zwei unterschiedliche Personas abbilden, wenn er ein echtes Verhaltensmuster widerspiegelt, oder als offene Annahme markieren, wenn unklar ist, welche Seite zutrifft.
