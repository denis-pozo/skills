---
name: npm-audit
description: "Use when the user runs /npm-audit or asks to audit dependencies, check npm vulnerabilities, or review `npm audit` results. Runs a read-only npm audit, compares it against the baseline in docs/audit.md, suggests next actions, and keeps docs/audit.md up to date."
---

# npm audit

Read-only audit, compare with `docs/audit.md`, review findings with the user, update the doc.

Never run `npm audit fix`, `npm install` or `npm update`, never edit `package.json` or the lockfile, never commit or push. Suggest those for the user to run.

## Steps

1. Load `docs/audit.md`. If it doesn't exist, offer to create it.
2. Run `npm audit --json` and `npm audit --omit=dev`. Compare with the baseline: label each finding Unchanged, New, Resolved or Changed.
3. Go through New and Changed findings one by one with the user. For each: advisory in one line, dev-only or production, and what the offered fix would install (flag downgrades). Recommend an action; the user decides.
4. Once the list is done, update `docs/audit.md`: history row, "Last reviewed" line, and each finding as Accepted (with reasoning), fixed, or still open.
