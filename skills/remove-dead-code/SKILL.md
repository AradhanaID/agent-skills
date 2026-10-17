---
name: remove-dead-code
description: Find and delete dead frontend code safely - prove unused, delete whole units, verify.
disable-model-invocation: true
---

# Remove Dead Code

One run clears one dead region: prove it is unused, delete the whole unit, verify what remains. It never refactors what it keeps; nearby living code that looks wrong is named, not touched.

## Steps

1. **Enumerate candidates.** List whole units that may be dead: untouched files, unreferenced exports, components no route renders, props and states no caller passes, CSS classes no markup uses. **Whole units, not lines** — a dead export with live helpers is still one unit.
   Done-when: every candidate names who could have referred to it.
2. **Prove unused at every address.** Search for both direct and dynamic reference: string-based imports, route tables, test templates, story names. A candidate is dead only when every way it can be reached is followed.
   Done-when: each candidate records the searches that found nothing.
3. **Delete in slices and verify each.** Remove one unit at a time — a **tracer bullet** rescue if anything surprising appears: stop, re-prove the boundary, then resume. After each deletion the build, type check and tests run.
   Done-when: at least one full build plus tests passes after the last deletion.
4. **Close the loose ends.** Re-check what used to import the removed units: an import chain, a stale fixture, a now-empty folder. **Shake the tree**: what falls out second is part of this run.
   Done-when: a fresh search for the deleted names returns nothing.

## Reference

- [reference.md](reference.md) — where frontend code hides from search, and the proof checklist per unit type.
