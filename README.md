# agent-skills

Frontend skills for AI coding agents, maintained against [Matt Pocock](https://github.com/mattpocock/skills)'s skill-checklist framework — trigger, structure, steering, pruning.

## Skills

| Skill | Invoked | For |
|---|---|---|
| [`plan`](skills/plan/SKILL.md) | user (`/plan`) | Plan frontend work before code: outcome, vertical slices, seams, acceptance checks |
| [`remove-dead-code`](skills/remove-dead-code/SKILL.md) | user (`/remove-dead-code`) | Prove frontend code unused, delete whole units in slices, verify per slice |
| [`structure`](skills/structure/SKILL.md) | **model** (auto) | File placement and naming — fires when creating or moving frontend files |
| [`design-system`](skills/design-system/SKILL.md) | **model** (auto) | Enforces UI preferences while styling: one font, spacing over borders, 80-20-10 color |
| [`write-a-skill`](skills/write-a-skill/SKILL.md) | user (`/write-a-skill`) | Author or rework a skill: trigger, steps, leading words, the no-op test |

## Why the invocation split

- `plan` and `remove-dead-code` are user-invoked (`disable-model-invocation: true`): zero always-on context load, the description is a human-facing one-liner (<100 chars). `/plan` in particular is run on purpose, before work starts — never as a side effect.
- `structure` is model-invoked: its description is the always-loaded context pointer that lets the agent fire it autonomously at the moment a file is created or moved, exactly when placement knowledge pays.

## Framework

- **Structure** — `SKILL.md` holds steps with explicit done-conditions only. All supporting material (templates, hiding-place lists, convention rules) sits in the skill's `reference.md` behind a pointer stating *when* to read it.
- **Steering** — dense leading words anchor behavior: *whole units*, *tracer bullet*, *fog of war*, *seam*, *shake the tree*, *kind decides placement*, *one home per file*.
- **Pruning** — one meaning, one place (structure's `reference.md` owns placement rules; skill bodies point, never restate). No-op test sentence by sentence; placeholders are for replacement, not sediment.
