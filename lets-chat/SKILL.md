---
name: lets-chat
description: "Use when the user wants to align with the agent before doing any work: \"let's chat\", \"lets-chat\", \"let's get on the same page\", \"talk this through\". Interviews the user down a decision tree until every branch is resolved, then outputs a concise summary as context for the next steps."
inspired-by: "grill-me skill by Matt Pocock: https://github.com/mattpocock/skills/tree/main/skills/productivity/grill-me"
---

# Let's Chat

Interview me until we share the same understanding. Don't implement anything.

## Rules

- Walk the decision tree: list the decisions my prompt left open, then resolve them one
  branch at a time, depth-first. Settle a decision before the ones that depend on it.
- One question per turn. Short. Include your recommended answer so I can just say "yes".
- If the repo or docs can answer it, read them instead of asking.
- Skip branches my prompt already settled. Challenge anything vague or contradictory.
- Don't stop while a branch is open. Stop when none are.

## Output

When every branch is resolved, output only this. Max one line per item, omit empty ones.

```
## Context
**Goal:** …
**Decisions:** 
- …
**Out of scope:** …
**Assumptions / open:** …
**Next:** …
```

Then wait for my confirmation. Save to a file only if I ask.
