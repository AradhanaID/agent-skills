---
name: plan
description: Plan a piece of frontend work before any code - slices, seams, and what proof of done is.
disable-model-invocation: true
---

# Plan

One run plans one piece of work and produces a plan the implementing agent can run as-is. It writes nothing but the plan; implementation happens after, in separate runs.

Before writing the plan, follow the [context pointer in reference.md](reference.md).

## Steps

1. **Inventory what exists.** Read the touched area before proposing anything. Name the affected files, handlers, and entry points as they are today, not as imagined.
   Done-when: nothing in the plan refers to a file that was never opened.
2. **Fix the outcome.** Write what a user sees or does when the work is done, in one sentence. That sentence is the work unit; everything beneath it supports it. **Outcome before artifact**: what changes for the user, not which files change.
   Done-when: the outcome fits in one sentence and the user agreed.
3. **Cut vertical slices.** Order the work so each slice ships user-visible progress end to end — a **tracer bullet** first: the thinnest slice that touches every layer of the feature, however small the layers. Fog of war covers the later slices: plan them one clause each, they will be re-planned once the first slice lands.
   Done-when: no slice is "then implement the rest"; the first slice can ship alone.
4. **Name the seams.** Where will behavior be observed and tested: which handler, which component boundary, which route. Unagreed seams are not in the plan.
   Done-when: every acceptance check below points at a named seam.
5. **Write acceptance checks.** One check per slice, phrased as observable behavior, and phrased so it can fail: "signup with a taken email shows the inline error", not "handle errors".
   Done-when: the user can tell, without asking the agent, that a slice passed its check.

## Reference

- [reference.md](reference.md) — the plan template and the pre-plan checklist for frontend work.
