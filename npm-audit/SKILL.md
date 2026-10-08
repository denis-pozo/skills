---
name: npm-audit
description: "Use when the user runs /npm-audit or asks to audit dependencies, check npm vulnerabilities, or review `npm audit` results. Runs a read-only npm audit, compares it against the baseline in docs/audit.md, suggests next actions, and keeps docs/audit.md up to date."
---

# npm audit

Run the audit, compare it with the project's recorded baseline, suggest what to do, and keep `docs/audit.md` current. Read-only on dependencies: never change them.

## Rules
- Never run `npm audit fix` (with or without `--force`), `npm install`, `npm update`, or edit `package.json` / `package-lock.json`. Suggest those as next actions for the user to approve.
- Never commit or push. Edits to `docs/audit.md` are left uncommitted; tell the user.
- Read `docs/audit.md` first. Its "Rules" and "Known non-audit warnings" sections apply to this run.
- Don't mark anything "Accepted" on your own. New findings go in as "New, unreviewed" until the user decides.

## Steps
1. **Load the baseline.** Read `docs/audit.md`: the baseline table, rules, known warnings and history. If the file is missing, say so and offer to create it from the first run.
2. **Run the audit.**
   - `npm audit` for the readable report.
   - `npm audit --json` for `isDirect`, `severity`, `fixAvailable` per package.
   - `npm audit --omit=dev` to separate what affects production.
   - Note the audited versions (`next`, `eslint-config-next` and the Node version from `node -v`) for the history row.
   - If the working tree's `package.json` / lockfile differ from `HEAD`, say which one was audited. To audit `HEAD` without touching the tree, copy `git show HEAD:package.json` and `HEAD:package-lock.json` into the scratchpad directory and run `npm audit --package-lock-only` there.
3. **Compare with the baseline.** Classify every finding:
   - **Unchanged**: same chain and severity as the baseline.
   - **New**: not in the baseline.
   - **Resolved**: in the baseline but gone.
   - **Changed**: same package, different severity, scope, or fix.
   For each new or changed finding, work out: direct or transitive, dev-only or production (`--omit=dev`), what the advisory says, and what the "fix available" line would actually install. Check whether that fix is a downgrade or a semver-major change by comparing it with the current version.
4. **Report to the user**, short and in this order:
   - One-line verdict: counts by severity, and whether anything changed against the baseline.
   - New / changed / resolved findings, each with scope (dev or production) and the advisory in one line.
   - Whether any finding affects production (`--omit=dev`). Lead with this if so.
   - **Suggested next actions**, ranked, with a recommendation. Examples: update a direct dependency, wait for an upstream release, try an `overrides` entry, accept as dev-only risk. Say what each would change and what to check afterwards (`npm run build`, `npm run lint`). Flag any suggested fix that is a downgrade or breaks the Next version pairing.
5. **Update `docs/audit.md`.** Always:
   - Add a row to the History table: date, result, short notes.
   - Update the "Last reviewed" line with the versions audited.
   Also, for the findings:
   - Unchanged: nothing else to change.
   - New: add them to the baseline table with status "New, unreviewed".
   - Resolved: remove them from the baseline and note it in History.
   - Changed: update the row.
   Once the user decides on a new finding, set it to "Accepted" with the reasoning, or record the fix. Add a new lesson under "Rules" if the run taught one.
6. **Tell the user** what was edited in `docs/audit.md`, that it is uncommitted, and offer to commit it.

## Done when
The user has the verdict, the diff against the baseline and ranked next actions, and `docs/audit.md` has the new history row and any new findings.
