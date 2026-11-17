---
name: comments
description: Comment rules - keep a why the code cannot show, delete what the line beneath already says. Fire when writing or reviewing comments.
---

# Comments

One run leaves the comments a reader needs and nothing else. The default is fewer: a comment earns its line by carrying knowledge the code cannot, and everything that restates, narrates, or remembers is deleted on sight. The verdict table is in [reference.md](reference.md) — read it before judging the first comment.

## Steps

1. **Name the job.** Every comment is one of four: a **why** (the reason behind a surprising choice), a **contract** (what a caller or a file format depends on), a **pointer** (where the external truth lives), or **narration** (what the line beneath already says) / **tombstone** (what the code used to do) / **apology** (a TODO, a `hack`, a disabled rule).
   Done-when: each comment in the run is filed under one job, in one word.
2. **Run the no-op test.** Delete it and ask what breaks. Nothing breaks — narration, tombstones, apologies, and commented-out code never survive.
   Done-when: no survivor can be reconstructed by reading the line beneath it.
3. **Keep the why whole.** A survivor names the failure it prevents or the constraint it obeys, in one line, present tense. It never restates a type, a name, or a history of the code.
   Done-when: every survivor maps to one behavior that breaks if a future editor ignores it.
4. **Move long-form out.** A header taller than two lines, a ported-from note, or a tour of an algorithm belongs in the repo's rule file or module docs — not above a function.
   Done-when: no function carries a header taller than its signature, and every external reference resolved to a path in the repo.
5. **Read the diff as the reader.** Scan what was added, top to bottom, before declaring done.
   Done-when: the added lines carry no comment an editor would skip past, and no comment repeats its neighbor.

## Reference

- [reference.md](reference.md) — the four jobs with keep/delete verdicts, the language rules, and the before/after from a real pruning pass.
