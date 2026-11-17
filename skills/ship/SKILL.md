---
name: ship
description: Commit finished work on a branch and open a pull request against dev.
disable-model-invocation: true
---

# Ship

One run ships one unit of finished work: a branch, one commit, one pull request against `dev`. It never bundles unrelated changes, never commits to the base branch, and never force-pushes.

## Steps

1. **Check state first.** Run `git status --short --branch`, then `gh pr list --head <branch>`. Work already committed, pushed, or under an open PR is an **update**: push to that branch and revise the body. A second branch or a second PR for the same work is the failure this step exists to prevent.
   Done-when: the run knows whether it is a new PR or an update, and can say which.
2. **Branch off, never on.** On `dev` or `main` with uncommitted work, create `type/area-what` — `feat/users-you-label`, `fix/brands-dup-rows`. Commits land on the branch; the base only moves at merge.
   Done-when: `git status` names a branch that is not the base.
3. **Read the diff as a reviewer.** `git diff --stat`, then `git diff`. Revert incidental churn — re-indentation, reformatting, blocks moved for tidiness — that the change does not need. Confirm no untracked secret (`.env*`, keys, dumps) is about to be staged.
   Done-when: every remaining hunk is one the change would not work without, and nothing secret is staged.
4. **Verify, then report actual output.** Run the repo's lint, type check and tests; keep what they print. A failure that predates the branch is *proved* so — stash the work, re-run, restore — and named as **pre-existing** rather than hidden or blamed on the change.
   Done-when: each command's real output is in hand, not a claim about it.
5. **Write the commit.** `type(scope): summary` under ~72 characters, ticket key when known. The body carries **the why**: the problem, the decision, what was traded away. Take the repo's voice from `git log -3`.
   Done-when: the body stands on its own to someone who cannot see the diff.
6. **Push and open the PR.** Base is `dev` unless told otherwise. Body follows the [template in reference.md](reference.md) — What, How, Verification with the step-4 output, Not verified.
   Done-when: `gh pr create` returns a URL and `gh pr view` reports base `dev`.
7. **Report the short version.** PR link, one line on what changed, and the honest gap: what was not verified and why.
   Done-when: the report names a URL and at least one thing not verified — or states plainly that everything was.

## Reference

- [reference.md](reference.md) — the PR body template, commit body examples, and the state commands that tell new from update.
