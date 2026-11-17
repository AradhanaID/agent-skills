# Reference — ship

The template and commands behind the steps. Read the PR template before step 6.

## Telling new from update

```bash
git status --short --branch          # uncommitted? which branch? ahead/behind?
gh pr list --head <branch> \
  --json number,state,baseRefName,url --jq '.[] | "\(.number) \(.state) -> \(.baseRefName): \(.url)"'
gh pr view <number> --json state,mergeable,baseRefName,files \
  --jq '{state,mergeable,base:.baseRefName,files:[.files[].path]}'
```

An open PR for the branch means update: `git push`, then `gh pr edit <number> --body-file -` to revise. Opening a second PR splits the review across two places.

## Proving a failure pre-existing

```bash
git stash push -u -m "verify-baseline"
npx tsc --noEmit        # or the repo's type check
git stash pop
```

Same error with the work stashed means it was already there. Name it pre-existing in the PR and say how it was proved; do not silently drop it.

## Commit body

Summary says *what*; the body says *why*. Three or four sentences beats a bulleted changelog.

```
feat(users): label the signed-in user's row with (You)

The Manage User table showed every registered user the same way, so an
admin had to match names by eye to find their own assignment.

The proxy now returns `viewerUserId` from the caller's token -- the same
directory id stored per row -- and the table compares it against
`user.userId`. The claim is not signature-verified: it drives a label
only, and the gateway still validates every write.
```

A body that recites file names ("modified ManageUserView.tsx, users.ts") is the diff restated; it carries no why.

## PR body template

```markdown
## What

<The problem in the user's terms, then what now happens instead. Two or three sentences.>

## How

- **<File or area>** — <the decision made there and why that mechanism>. 
- **<File or area>** — <same>.

## Verification

- `<command>` — <what it actually printed>.
- <What was exercised in the browser, against which data>:

  | Case | Result |
  | --- | --- |
  | <input> | <observed> |
  | <input> | <observed> |

## Security notes

<Only when the change touches auth, input boundaries, identifiers, or data. Drop the section when it does not apply -- an empty heading trains reviewers to skip it.>

## Not verified

- <What was not run, and why it was not possible. Never leave this empty; "everything, perfectly" is not a thing.>
```

## Body rules

- **Verification quotes real output.** `npx eslint` printing nothing is a result; "linting passes" is a claim.
- **Not verified names the gap**, not an apology. "Live integration service untested: the dev server has no session cookie" tells a reviewer exactly what to click.
- **Security notes earn their place.** State the risk and the reasoning that closes it, or omit the section.
- **Update the docs in the same PR** when an interface, response shape, or contract changes — a README line is cheaper than a question in review.
