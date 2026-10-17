# Reference — plan

Supporting details for the [SKILL.md](SKILL.md) steps. The template lives here so the procedure stays readable.

## Context pointer

"Frontend specifics" below holds what a plan in this repo must account for. Replace the placeholders with the repo's real values as they settle, instead of appending.

## Plan template

```
Outcome: <one sentence, user-visible>
Slices:
  1. <thinnest end-to-end slice> — check: <observable behavior that can fail>
  2. ...
  N. <one clause each, uncommitted>
Seams: <handler / component boundary / route per check>
Open questions: <one line each, answered before the slice that needs them>
```

## Frontend specifics

- Each slice names its level of the stack: markup, state, data fetching — the first slice touches all three even if trivially.
- Fallback states (loading, empty, error) are named in the slice that first renders real data, not deferred to a final polish slice.
- Design tokens and layout conventions live here when defined; until then the plan names the closest existing component to imitate.
