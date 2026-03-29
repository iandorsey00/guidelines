# Guidelines

Shared cross-app guidance for Ian Dorsey projects.

This repo is the single source of truth for:
- interface and design guidance
- engineering, release, and process guidance
- shared writing, accessibility, and CLI defaults

It is written to be:
- implementation-neutral where possible
- AI-implementation-neutral where possible
- reusable across multiple apps
- easy for humans to scan
- easy for Codex to apply at the start of a project

The first intended consumers are MiniTickets and GeoCompare Web, but the guidance should remain durable beyond either app.

## Structure

- `docs/interface-guidelines.md`: shared interface and product design guidance
- `docs/engineering-guidelines.md`: shared engineering, release, and collaboration guidance
- `docs/content-style-guide.md`: shared product copy and bilingual wording guidance
- `docs/accessibility-checklist.md`: shared accessibility review checklist
- `docs/release-checklist.md`: shared release shorthand and execution checklist
- `docs/cli-guidelines.md`: shared standards for CLI consistency, accessibility, and best practices
- `docs/codex-handoff.md`: fast ChatGPT Codex handoff for loading shared repo guidance into thread context

## How To Use

For a new project:
1. Start here before making interface or process decisions.
2. Apply shared rules by default.
3. Add project-specific exceptions in the app repo, not here.
4. Keep this repo concise, opinionated, and durable.

## Scope

Belongs here:
- shared design principles
- shared product language and UI expectations
- shared engineering and release conventions
- shared accessibility and writing defaults
- Codex collaboration defaults

Does not belong here:
- app-specific deployment scripts
- implementation details tied to a single stack or AI workflow
- machine-specific setup
- committed secrets or filled environment files
- one-off project preferences that do not generalize

## Handoff

For this repo, the docs are the primary handoff.

`docs/codex-handoff.md` exists as a fast-loading Codex-specific summary so a new ChatGPT Codex thread can pick up the shared standards quickly. The full source of truth remains the main documents in this repo.
