# Story Map

Spec → Story Map: Aktivitäten, Tasks und Release-Slices vom Walking Skeleton zur vollen Tiefe.

Backbone zuerst (Aktivitäten → Tasks), dann Stories, dann jede Story einer Release-Slice zugeordnet. „Neglect no one" — Setup- und Admin-Aktivitäten gehören ins Skelett.

## Input
`output/YYYY-MM-DD/spec-eval/spec.md` (Fallback: Pfad zu einem Brief, beim Aufruf übergeben) + `context/company.md`, `context/strategy.md`, `context/product.md`, `context/team.md`

## Invocation
`/story-map`

## Output
`output/YYYY-MM-DD/spec-eval/story-map.md`

## Weiter mit
`/eval-writer` oder `/option-stormer`
