# Definition of Done

An issue is Done only when **all** of these are true.
If one can't be met, say why in the PR. Don't silently skip it.

## Ready to start (Definition of Ready)
- [ ] Acceptance criteria are written and checkable
- [ ] Size is S or M (L = split first)
- [ ] Nothing blocking it

## Done
**Works**
- [ ] Every acceptance criterion is met and was checked by hand
- [ ] Tested on the demo environment after merge (once the demo environment is set up)

**Quality**
- [ ] CI is green: build, lint, tests, secret-scan
- [ ] New logic has tests (legacy repos: existing smoke test still passes)
- [ ] No new compiler/linter warnings

**Reviewed**
- [ ] PR approved by a teammate, all comments resolved, squash-merged
- [ ] Author can explain every line without the AI tool

**Safe & documented**
- [ ] No secrets, keys, or real user data in the code
- [ ] README / `.env.example` updated if setup, config, or env vars changed

**Closed**
- [ ] PR used `Closes #123` so the issue closed automatically
