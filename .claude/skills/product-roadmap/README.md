# Product Roadmap

Ideen mit Opportunity-Scorecard oder Decision Brief → lebende Now/Next/Later-Roadmap (optional Timeline). Sequenziert, bewertet nicht neu. Eine aufgenommene Idee ohne eigenes Priorisierungssignal reicht dafür nicht und landet unter „Ungeklärt".

## Input
`output/roadmap/intake/*.md` + Opportunity-Scorecards/Decision-Briefs (datiert oder undatiert) + `context/strategy.md` + `context/roadmap.md` + `context/team.md` + `context/metrics.md`

Scorecards/Briefs werden Intake-Einträgen über Thema/Titel zugeordnet — es gibt keine ID-Verknüpfung.

## Invocation
`/product-roadmap`
oder für die Zeitstrahl-Ansicht: `/product-roadmap timeline`

## Output
`output/roadmap/roadmap.md` — wird bei jedem Lauf aktualisiert, nicht neu geschrieben.

## Weiter mit
Roadmap ist lebend — erneut ausführen, sobald neue Kandidaten aufgenommen (`/roadmap-intake`) oder neu bewertet (`/opportunity-scorer`, `/decision-brief`) wurden.
