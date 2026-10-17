---
name: structure
description: Where frontend files belong in this repo. Fire when creating a new file or moving one.
---

# Structure

This skill orients where frontend code lives: folder conventions, naming, and what marks a file misplaced. The conventions move with the codebase, so the authoritative list is in [reference.md](reference.md) — read it before placing a file.

## Steps

1. **Ask what the file is, not where it fits.** Component, hook, utility, test, asset, config. Kind decides placement; the kind is a leading word for the conventions in [reference.md](reference.md).
   Done-when: the kind is stated in one word.
2. **Place by the rules, whole units at a time.** A component moves with its test, story and styles — never the component alone.
   Done-when: the placement matches the rules verbatim; anything name-bending is listed at the end of the run with a reason.
3. **Confirm naming against the neighbors.** Name matches sibling files and the overall convention: singular/plural, period-splitting, case.
   Done-when: a directory listing reads uniformly; nothing needs renaming to blend in.

## Reference

- [reference.md](reference.md) — the placement rules and naming conventions. Update it when the repo's layout settles; it is the single source of truth, and conventions stated anywhere else are near-places of this file.
- When two rules seem to conflict, the more specific one wins, and the conflict is reported so the rules can be corrected.
