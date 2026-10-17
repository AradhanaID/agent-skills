---
name: design-system
description: UI styling rules - one font, spacing over borders, 80-20-10 color. Fire when writing UI.
---

# Design System

The project's UI preferences, applied while building, not after. Writing UI without consulting `reference.md` breaks the flat-treatment rule before any step runs; the rules are the [context in reference.md](reference.md), loaded first.

## Steps

1. **Read the rules, then the existing UI.** Take the [style rules in reference.md](reference.md), then find what the codebase already uses — its font, palette, icon pack and rounding already chosen.
   Done-when: rules are named in the implementation plan; every rule already in the codebase is matched, not refreshed.
2. **Space before borders.** Separate elements with whitespace; a border is added only when spacing out of space.
   Done-when: each element boundary renders through space alone; borders exist only where the plan names why spacing fell short.
3. **Color in three bands.** Assign neutral → 80%, secondary → 20%, accent → 10% per surface before writing styles; a pill or badge is where accent fills its seat.
   Done-when: the controls and text render in only one or two neutral tones; the accent appears in at most one seat per view.
4. **Verify responsive and readable.** Run the view at a mobile width before declaring it styled; text near pure black or pure white moves off the extremes.
   Done-when: the mobile layout holds without horizontal scroll; every text color is an off-extreme tone.
5. **Adapt the icons.** Detect the project's icon library and reuse one unit of it everywhere it appears.
   Done-when: one icon was picked by the book and no new icon set was introduced.

## Reference

- [reference.md](reference.md) — the eleven style rules, the color split, and the one-full-set icon rule. Point knowledge here; this file never must adapt.
