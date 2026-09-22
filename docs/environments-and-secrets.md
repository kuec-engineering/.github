# Environments & Secrets

## Environments
| Env | Where | Database | Deploys |
|---|---|---|---|
| Local | Your machine | Neon `dev` branch | You run it |
| Demo | Render (free) | Neon `demo` branch | Automatically on merge to `main`, after checks pass |

Staging and production are created per client, when a client exists.

## Where secrets live
| Secret type | Lives in | Who can see it |
|---|---|---|
| Demo runtime (DB URL, API keys) | Render → service → Environment | Leads only |
| CI-only | GitHub → repo → Settings → Secrets and variables → Actions | Leads set them; workflows use them |
| Local dev | Your own `.env` (gitignored), Neon `dev` branch only | You |

## Rules
- Never commit a real value. `.env.example` has names only.
- Never paste secrets in chat, issues, PRs, docs, or AI tools.
- New variable? Add it to `.env.example` **and** `render.yaml` (with `sync: false`) in the same PR, then tell a lead to set the value in Render.
- A secret was exposed? Tell a lead immediately. We rotate it first, then investigate.
- Never connect to the `demo` database from your machine. Local work uses `dev` only.

## Demo broke after a merge
1. Fastest: Render → service → **Events** → pick the last good deploy → **Rollback**.
2. Then: **Revert** the PR on GitHub so `main` matches what's running.
3. Fix properly on a new branch.
