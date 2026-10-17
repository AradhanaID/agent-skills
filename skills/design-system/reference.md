# Reference — design-system

The project's UI preferences. This file is the single source of truth for style; a rule stated anywhere else — a comment, a component, a chat answer — is restated here or corrected there.

## The rules

1. **One font for the whole project.** No second family unless the user specifies the mix. Weight and size carry hierarchy; family does not.
2. **No gradient text.** Text renders solid, one color.
3. **Borders minimal.** Separate UI elements by spacing first; a border is the fallback when spacing cannot distinguish, not the default.
4. **80–20–10 color.** 80% neutral, 20% secondary, 10% accent — measured per view. The accent is small and deliberate; if every button is accent, the balance is broken and the view is re-ordered.
5. **No all-caps text** unless the user specifies. Emphasis comes from weight and tone, not capitals.
6. **Responsive for mobile.** Every surface is built to a mobile width first and grows outward, not the reverse.
7. **Never pure black on pure white.** The pairing flares; soften one side so the contrast sits easy on the eye.
8. **Text is neither pure black nor pure white.** Off-extremes only (e.g. `#111`–`#1a1a1a` rather than `#000`).
9. **One icon set, always the same one.** Detect what the project already uses and reuse that pack; a new icon migrates into the existing set, never a second set in.
10. **No AI-slop left-border highlight.** No colored left border as a highlight or card style. The accent band belongs to the accent rule, which this is not.
11. **Rounding minimal, 4px to start.** Radius starts at `4px` and grows only when the user names a reason; large radii are per-feature decisions, not defaults.

## Adapting to what exists

Rules 1, 9 and 11 settle against the codebase: if the project already carries a different rounding, icon pack or font, the existing choice wins and these rules hold the line against drift — the preference is consistency with the settled value, and the settled value is re-used, not re-litigated.

## Rule order in a conflict

An explicit user instruction beats this list. Between two rules of this list, the more specific beats the more general, and the conflict is named to the user so the list can be corrected here — this file, not the component.
