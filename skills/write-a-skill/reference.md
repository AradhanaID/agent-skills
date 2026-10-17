# Reference — write-a-skill

Frontmatter mechanics, pointer-writing rules, and the review checklist. The procedure in [SKILL.md](SKILL.md) stays readable without them.

## Frontmatter mechanics

The two invocation types, and what each pays:

- **User-invoked**: `disable-model-invocation: true`. The agent never fires it; no other skill can reach it — only the human typing the name. Zero always-on context load; the cost is memory, cured by a **router skill** that names the set and *hints, never fires*. Trigger lists are left out: the description is a human-facing one-liner, under 100 characters.
- **Model-invoked**: omit the flag. The description is permanently loaded — the skill's top-level context pointer — written model-facing, with the trigger branches stated. One or two trigger moments, not every use of the area: fires where it saves a mistake, not where it repeats general knowledge.
- The tests file a skill needs against all drafts: does its name fire from the words you naturally use, and does its description read as *when this happens* rather than *what I want*?

## Pointer-writing rules

A pointer's wording, not its target, decides whether it is followed:

- name *when* to read, not just *where*: "read before step 2" beats "see reference.md"
- put the branch condition in the pointer: material only one path needs is behind it, material every run needs stays in the file
- a pointer to a file outside the skill system is how two user-invoked skills share reference — neither can reach the other, but both can point at plain files
- a pointer to content stubbed for later replacement is marked for replacement in place — never appended next to, so sediment never grows

## Checklist

The battery applied step 5 to an existing skill, one question each:

- **No-op test**: per sentence — would deleting it change what an agent does?
- **Single source**: is each meaning stated once, either in the body or pointed at, never both?
- **Sediment**: does every line still bear on what the skill does today? Legacy advice and unused branches go.
- **Duplication**: the same rule, worked example, or template repeated, whether reworded or not?
- **Trigger audit**: is it load-bearing — could the agent reach it before the mistake it prevents? Fire the description to find out.
- **Done-condition audit**: can each step be checked false as well as true? An unchecked step does not stop the run.
- **Leading word audit**: does every dominant term appear at least once in a done-condition? Terms that never touch the outcome check are decoration.
