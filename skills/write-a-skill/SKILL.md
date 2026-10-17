---
name: write-a-skill
description: Write or rework a skill using the four-check method - trigger, structure, steering, pruning.
disable-model-invocation: true
---

# Write a Skill

One run authors or reworks one skill. The output is judged by behavior when the skill runs, not by how it reads: this run installs the user's process, not generic skill boilerplate.

Before writing, follow the [context pointer in reference.md](reference.md) — frontmatter mechanics live there.

## Steps

1. **Fix the trigger.** Ask who must reach the skill and when. A skill that only ever runs on purpose is **user-invoked** (`disable-model-invocation: true`, description becomes a one-line human summary, <100 chars). A skill the agent must reach unprompted is **model-invoked**: its description is the always-loaded pointer, and its wording decides whether the fire happens.
   Done-when: the invocation choice names the load it is paying — context, or your memory.
2. **Inventory how the work actually runs.** Recall the last real run of this work: what was sent back, corrected, or repeated. Those corrections are the skill's content; what the model does unaided is not.
   Done-when: the draft cites at least one real failure it prevents.
3. **Write steps, then pointers.** Each step is one procedure with an explicit done-condition, ordered so the run ships something checkable first. Supporting material that only some passes need goes in `reference.md` behind a pointer naming *when* to read it.
   Done-when: every step is verifiable without asking the agent whether it succeeded.
4. **Pick the leading words.** For each recurring idea, take the compact word already living in the model's pretraining and let it carry the meaning: the pointers, steps and done-conditions reuse those words. Rename jargon into them rather than explaining around them.
   Done-when: each leading word appears in more than one place and steers in each.
5. **Prune with the no-op test.** Sentence by sentence: delete it, ask what broke. Nothing broke — the sentence goes. Whole sentences delete, never trimmed words; duplication collapses into a single source of truth rather than two fades.
   Done-when: you can no longer run the no-op test without passes; the file is shorter than the last version.

## Reference

- [reference.md](reference.md) — frontmatter mechanics per invocation type, the pointer-writing rules, and the checklist battery for reviewing an existing skill.
- The skill this run produces is iterated against real runs, not written once: when a run misbehaves, the [read reference](reference.md#checklist) qualifies the failure before any rewrite.
