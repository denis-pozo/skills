---
name: initiatives-brainstorming
description: Help brainstorm project initiatives and capture them in a concise Markdown backlog for later comparison and prioritization. Use for concept-stage idea collection, refinement, and documentation rather than implementation planning or coding.
---

# Initiatives brainstorming

Turn an informal stream of project ideas into a useful list of initiatives to tackle later, one by one. Keep enough context to understand each idea later, compare it with others, and prioritize it. Stay at the concept level unless the user asks for more detail.

## Conversation

- Accept ideas incrementally. Give each a short, concrete title and a brief description of its purpose or expected benefit.
- Carry forward the user's audience priorities, choices, and deferred decisions. Ask focused questions when ambiguity would materially change an initiative; avoid making every idea an interview.
- Offer improvements and creative additions when useful. Distinguish suggestions from agreed requirements and priorities.
- Explain overlaps or dependencies briefly. Related ideas may remain separate initiatives when that helps comparison.
- Do not implement features, produce technical specifications, or choose an execution order merely because ideas have been collected.

## Capture the backlog

When asked to document the discussion, inspect the existing project documentation and update the appropriate tracker. Default to `docs/initiatives.md` if none exists. Preserve unrelated content and existing initiative identities.

Use a compact structure:

- A short statement of purpose and audience priorities.
- An overview table with initiative, purpose, and status.
- Numbered entries with a title and a short description, plus only the decisions, considerations, or open questions needed to understand the idea later.
- A brief note about deferred brainstorming or decisions when relevant.

Mark unimplemented concepts as ideas. Listing order is not priority unless the user says so. Include all ideas the user asks to capture; do not silently drop suggestions or turn them into approved commitments. Record suggested priorities as suggestions.

Keep documentation lightweight: no estimates, acceptance criteria, detailed architecture, task breakdowns, or exhaustive risk lists unless requested. Mention a conflict with existing project scope only when it affects later decisions.

## Lessons from the originating session

The original session concerned a professional showcase website. Potential employers were the primary audience and the professional community the secondary audience. The user collected content, role-based login, and visual design initiatives first, then requested creative additions and asked to record all of them. Detailed content for each visitor profile was explicitly deferred until after the initial initiatives.

Use this as an example of preserving audience, scope, and deferrals, not as a default requirement for other projects. For that website, `docs/initiatives.md` is the source of truth for the current ideas; read it when continuing its brainstorming instead of relying on this historical summary.

