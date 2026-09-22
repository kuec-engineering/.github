# KUEC Engineering

Software team at Khalifa University Enterprises Company.

## How we work
- **Stack for new projects:** ASP.NET Core API + Angular, started from `tpl-dotnet-angular`.
- **Tasks:** every piece of work is an issue on the team Project board. No issue, no branch.
- **Branches:** short-lived, off `main`, named `feat/123-short-desc`, `fix/123-short-desc`, `chore/short-desc`.
- **Merging:** PR → 1 approval → CI green → squash merge. Nobody pushes to `main`.
- **Secrets:** never in code. Use `.env.example` for names, real values live in GitHub/Render secrets.
- **AI tools:** allowed. You must be able to explain every line you submit. Mark AI usage in the PR template.

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
