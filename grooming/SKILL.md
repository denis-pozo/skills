---
name: grooming
description: Interactively prioritize an existing initiative backlog and capture selected commitments in minimal individual Markdown files. Use for initiative grooming and pipeline selection, rather than brainstorming new ideas or planning implementation.
---

# Grooming

Turn an existing backlog into an agreed, prioritized set of initiatives that can advance through the delivery pipeline. Keep the handoff focused on what is wanted and why; leave how to the investigation when someone takes the initiative on.

## Interactive selection

- Read the initiative tracker and relevant project context. Default to `docs/initiatives.md`.
- Recommend the most actionable, highest-value initiatives based on the project's audience, goals, dependencies, and existing commitments. Default to three when the user does not specify a count.
- Explain the suggested order briefly and resolve meaningful overlaps so each selected initiative has a distinct scope. Do not invent implementation decisions to make an initiative appear actionable.
- Discuss the proposed selection and ordering with the user. Ask focused questions only for unresolved decisions; preserve choices and authorization already given.
- Use two planning statuses: **Committed** means selected to advance through the delivery pipeline; **Backlog** means retained for future consideration. Commitment does not imply immediate implementation, simultaneous work, or a Git commit. Once the user agrees to advance the selected initiatives, mark all of them Committed unless instructed otherwise; do not limit commitment to priority 1 or introduce Ready as an intermediate status.

## Individual initiative files

Default to `docs/initiatives/`, following existing project conventions when available. Prefix filenames with `1-`, `2-`, `3-`, and so on in the agreed order; 1 is highest priority. Use descriptive slugs and update existing files rather than creating duplicates. If reordering existing files, update their links and priority fields together.

Use this minimal format:

```markdown
# Initiative title

**Priority:** 1
**Status:** Committed

Brief description of the intended change, who benefits, and why it matters.
```

The description gives the person taking this on enough context to understand the **what**. Include scope boundaries only when they clarify the intended change or distinguish overlapping initiatives. Avoid **how**: no next steps, task checklists, technical approaches, architecture, estimates, investigation plans, or acceptance-criteria sections unless explicitly requested. Describing decisions or results that the eventual content should communicate is appropriate; choosing how to produce or present that content belongs to investigation.

## Update the tracker

- Include **Priority**, **Initiative**, **Purpose**, and **Status** in the overview table, linking selected initiatives to their individual files.
- Mark selected initiatives Committed and remaining initiatives Backlog. Keep unselected items unranked unless the user prioritizes them too.
- Define Committed and Backlog briefly in the tracker. Keep status and priority consistent across the table, individual files, and any existing summaries.
- Preserve unrelated ideas, context, and deferred decisions. Replace duplicated descriptions of selected initiatives with links where useful, and remove obsolete priority or status statements.
- Check the resulting files and links. Report the selected priorities and statuses without starting implementation or committing to Git unless asked.

The tracker is the source of truth for current priorities and commitments; do not hardcode a past session's selected initiatives into future grooming.
