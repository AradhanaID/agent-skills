# Reference — remove-dead-code

Supporting details for the [SKILL.md](SKILL.md) steps. Hiding places and the proof checklist live here so the procedure stays readable.

## Hiding places

Frontend code is referenced dynamically more than most. Before declaring a unit dead, it was checked against:

- route maps and navigation constants — a component wired only through a route string
- story, test and snapshot names — a fixture or story file keeps it alive in dev trees
- icon or image name lookups — assets referenced by concatenation (`paths/${name}`)
- CSS class names — classes consumed from string templates or class-name logic, not literal markup
- string-typed props and event names passed across component boundaries
- re-distributed setting files that name the module by path

## Proof checklist per unit

```
Unit: <path>
Static: grep for import/default/named usage -> none
Dynamic: route map, stories, tests, name-concat -> none (path noted)
Entry: is it a declared entry (route/config) itself? -> if yes, stop
Verification: build + type check + tests pass after deletion
```

## Delete the whole unit

Fixtures, stories and now-unused styles for a deleted component go in the same slice. An import pruned everywhere but its re-export kept is a half-deletion — follow the re-export to nothing before removing it.
