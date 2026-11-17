# Reference — comments

The verdict table, the language rules, and the before/after from a real pruning pass. The procedure in [SKILL.md](SKILL.md) stays readable without them.

## The four jobs

| Job | Question it answers | Verdict |
|---|---|---|
| **Why** | Why is this done the surprising way? | Keep — one line |
| **Contract** | What must never change here? | Keep — one line |
| **Pointer** | Where is the truth this depends on? | Keep — path or URL |
| **Narration** | What does the code do? | Delete |
| **Tombstone** | What did it used to do? | Delete — git has it |
| **Apology** | Unfinished, wrong, or suppressed | Fix it, or file it — never comment it |

The test between a *why* and a *narration* is whether the line beneath already states it. `// increment the counter` before `counter++` is narration. `// the API counts from 1, not 0` before `index + 1` is a why, and survives.

## Language rules

- **English in code**, whatever the team speaks. Indonesian or mixed-language comments are unsearchable by the next reader and by the agent.
- **Imperative, present tense**: "Never translate these keys", not "These keys aren't translated".
- **No pronoun "we"** — the comment states a fact about the code, not a team decision that needs attribution.
- **No history, no tickets, no dates, no authors.** A commit message and `git blame` carry all four.
- **One line.** If it needs two, it is either two comments or a paragraph that belongs in the rule file.

## Before and after — a real pass

A 22-line header above a build script, and what survived:

```ts
/**
 * i18n validation, run automatically before `npm run build` via the
 * `prebuild` script.
 *
 * Ported from `scripts/generate-auto-i18n.js` in
 * wg-production-workspace-prod-execution-web, limited to the validation half:
 *   1. Every locale must declare the same key shape as the base locale.
 *   2. Every route folder under `(main)` must have a translation namespace
 *      containing its menu-title key.
 *
 * This script is READ-ONLY. Unlike the reference implementation it never
 * rewrites `messages/*.json`; auto-adding keys during a build would make the
 * output non-deterministic and would be discarded by the Docker builder stage.
 *
 * Executed directly by Node's native type-stripping, so it must use erasable
 * syntax only (no `enum`, `namespace`, or parameter properties).
 */
```

```ts
// Read-only: this script never rewrites `messages/*.json`.
```

Everything else lost its job. The `prebuild` hook is visible in `package.json`; the ported-from note is history; the two numbered behaviors are the function bodies below; the erasable-syntax rule is enforced by the script failing on its own. One line constrains future edits — the rest narrated.

A three-line block that explained a ternary the ternary already explained:

```ts
// Only resolve a heading when the current route actually has messages.
// Passing `undefined` lets phoenix-ui fall back to the URL-derived title
// instead of showing `common`'s generic title.
const menuTitle = useMemo(
  () => (namespace ? t("MENU_TITLE") : undefined),
  [namespace, t],
);
```

```ts
const menuTitle = useMemo(
  () => (namespace ? t("MENU_TITLE") : undefined),
  [namespace, t],
);
```

A two-line block collapsed to the clause that carries the constraint — the file format, not the spreadsheet:

```ts
// Excel column headers are a fixed contract with the uploaded
// spreadsheet file and must not be translated.
```

```ts
// Keys below are the spreadsheet's column headers; never translate them.
```

## Auditing an existing diff

Read the added lines only; do not rewrite what the branch did not touch.

1. List every added comment with `git diff <base> -- '*.ts' '*.tsx' '*.yml'`.
2. File each against the four jobs. Anything that lands in Narration, Tombstone, or Apology is deleted in the same change.
3. Re-read the survivors out of context. A survivor that only makes sense next to the block it replaced was a tombstone.
4. Count: if the branch added more comment lines than code lines, at least one job was misunderstood.
