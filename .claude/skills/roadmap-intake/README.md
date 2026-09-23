# Roadmap Intake

Rohe Stakeholder-Anfrage → Vollständigkeits-Check (Completeness Gate) mit Verdikt „Aufgenommen" oder „Zurück an Stakeholder".

## Input
Ein beim Aufruf übergebener Text, oder eine beim Aufruf benannte Datei unter `input/roadmap-requests/`, plus `context/company.md` + `context/strategy.md` + `context/metrics.md`. Ist nichts benannt und liegen mehrere Dateien unter `input/roadmap-requests/`, werden sie nacheinander geprüft, jede mit eigenem Verdikt.

## Invocation
`/roadmap-intake "<kurze Beschreibung der Anfrage>"`
oder
`/roadmap-intake input/roadmap-requests/<datei>.md`
oder ohne Argument: prüft alle Dateien unter `input/roadmap-requests/` nacheinander.

## Output
Bei Aufgenommen: `output/roadmap/intake/<slug>.md`, mit Hinweis auf den PM-Termin als nächsten Schritt.
Bei Zurück an Stakeholder: keine Datei — nur die Rückmeldung mit konkreten Nachschärfungs-Hinweisen und dem Hinweis auf die erneute Einreichung.
Bei mehreren geprüften Anfragen gilt das für jede einzeln.

## Verdikt
- **Aufgenommen** — alle fünf Dimensionen (Was, Für wen/Problem, Nutzen + Erfolgssignal, Größe/Aufwand, Strategie-Fit) beantwortet.
- **Zurück an Stakeholder** — mindestens eine Dimension fehlt oder ist zu vage; der Skill liefert konkrete Hinweise zur Nachschärfung statt einer bloßen Ablehnung.

## Weiter mit
Nach „Aufgenommen" folgt ein menschlicher Termin mit dem PM (kein Skill). Danach sequenziert `/product-roadmap` die Idee in die Roadmap ein.
