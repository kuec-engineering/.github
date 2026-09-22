# KUEC Engineering

Software team at Khalifa University Enterprises Company.

📋 **[Team board](https://github.com/orgs/kuec-engineering/projects/4)** · ✅ **[Definition of Done](https://github.com/kuec-engineering/.github/blob/main/docs/definition-of-done.md)**

## How we work
- **Stack for new projects:** ASP.NET Core API + Angular, started from `tpl-dotnet-angular`.
- **Branches:** short-lived, off `main`, named `feat/123-short-desc`, `fix/123-short-desc`, `chore/short-desc`.
- **Merging:** PR → 1 approval → CI green → squash merge. Nobody pushes to `main`.
- **Secrets:** never in code. Use `.env.example` for names; real values live in GitHub/Render secrets.
- **AI tools:** allowed. You must be able to explain every line you submit. Mark AI usage in the PR template.

### Task flow
1. **No issue, no branch.** Every change starts as an issue with acceptance criteria and a Size.
2. **One assignee per issue.** Pairing is fine; one person is accountable.
3. **Pick from the top.** Take the highest-priority Todo item, assign yourself, move it to In Progress.
4. **Link it.** Branch `feat/123-short-desc`; PR body contains `Closes #123`.
5. **Finish before starting.** Max 1 item In Progress per developer. Blocked? Comment on the issue, tag @kuec-engineering/leads, and help review instead of starting new work.
6. **Size L means split it** into smaller issues before starting.

## Repo naming
| Pattern | Use |
|---|---|
| `<product>` | one repo per product (API + web together) |
| `tpl-<stack>` | template repos |
| `sandbox-<name>` | experiments, deleted after 30 days |

Lowercase, kebab-case, no personal names. Every repo gets topics: stack (`dotnet` / `nextjs`) and status (`active` / `parked` / `legacy`).

## Projects
| Repo | Stack | Status |
|---|---|---|
| `uventure` | Next.js | parked |
| `kuecattar` | Next.js | active |

## Need help?
Ask in the team channel or tag `@kuec-engineering/leads` on the issue.
