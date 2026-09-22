# Dev Workflow

## Branching (GitHub Flow)
- `main` is always deployable. Every merge to `main` deploys to the demo environment.
- Branch from the latest `main`. One branch = one issue.
- Name: `feat/123-short-desc` · `fix/123-short-desc` · `chore/short-desc` · `docs/short-desc`
- Keep branches short: **merge within 2 days**. Longer? The issue is too big, so split it.
- No `develop`, `release`, or `hotfix` branches. Urgent fixes use the same flow, just reviewed first.

### Daily commands
```bash
git switch main && git pull                    # start from latest main
git switch -c feat/123-login-form              # new branch
git add -p && git commit -m "wip: form layout" # commit often, messages can be rough
git fetch origin && git rebase origin/main     # update your branch with main
git push -u origin feat/123-login-form         # push, then open PR on GitHub
```
Rough commit messages are fine. Only the **PR title** ends up in `main`'s history (squash merge).

## PR titles
Format: `type: short description` (lowercase, imperative, no period)

| type | use for |
|---|---|
| `feat` | new user-visible behavior |
| `fix` | bug fix |
| `refactor` | code change, same behavior |
| `test` | tests only |
| `docs` | documentation only |
| `chore` | tooling, deps, config, CI |

Examples: `feat: add booking cancellation` · `fix: prevent double submit on login`

## Opening a PR (author)
1. **Self-review first.** Read your own diff on GitHub, top to bottom, before asking anyone.
2. **Keep it small:** aim for < 400 changed lines (lockfiles and generated files don't count).
3. Fill in the PR template and link the issue with `Closes #123`.
4. **CI must be green before you request review.** Red CI = not ready.
5. Want early feedback? Open it as a **Draft PR**.

## Reviewing (reviewer)
- **Reviewing beats starting new work.** Respond the same working day (within ~4 hours).
- Prefix every comment so the author knows what blocks the merge:
  - `blocker:` must fix before merge
  - `question:` explain this to me (an answer may be enough)
  - `suggestion:` better way, author decides
  - `nit:` tiny style point, never blocks
- **Approve** when there are no blockers left. Don't hold a PR hostage for nits.

### What to check
1. Does it do what the issue's acceptance criteria say? Nothing more?
2. Would I understand this code in 3 months?
3. Errors handled, not swallowed? Edge cases (empty, null, duplicate, unauthorized)?
4. Tests cover the new logic, and **no tests were deleted or weakened** to make CI pass?
5. No secrets, hardcoded URLs, or real user data?

### Extra checks for AI-generated code
- **Ask "why?"** about any line that looks unfamiliar. If the author can't explain it, it goes.
- **New dependency?** Confirm the package really exists, is maintained, and is actually needed. AI tools invent package names.
- **Invented APIs:** methods or config options that look plausible but don't exist in our library version.
- **Unrequested changes:** reformatted files, renamed things, or "improvements" outside the issue's scope. Ask to split them out.
- **Copy-paste duplication** instead of reusing existing code.

## Merging
- Squash merge only (enforced). The PR title becomes the commit message.
- The author merges their own PR after approval and green CI.
- After merge: check the change on the demo environment, then confirm the issue moved to Done.

## Something broke after a merge
1. Open the merged PR on GitHub, click **Revert**. This creates a revert PR.
2. Get a quick approval and merge it. The demo redeploys with the old code.
3. Fix properly on a new branch, with a test that would have caught the problem.

Revert first, investigate second. Never "quick-fix" directly under pressure.

## Releases
- **Now:** no versions. `main` = what's on the demo.
- **When a client has production:** we tag releases (`v1.4.0`) on GitHub. A tag deploys to production.
  Release notes are generated automatically from PR titles, which is why the titles matter.
