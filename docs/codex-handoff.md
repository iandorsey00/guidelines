# Codex Handoff

## Purpose

Use this document at the start of a ChatGPT Codex thread to load the most important repo guidance into context quickly.

This is a fast handoff layer, not the full source of truth. The full guidance remains in the other documents in this repo.

## What This Repo Is

This repo is the shared standards baseline for Ian Dorsey projects.

It exists to:
- keep interface and design choices consistent across apps
- keep engineering and release behavior consistent across apps
- stay implementation-neutral where practical
- stay AI-implementation-neutral where practical
- allow project-specific overlays only when they are genuinely needed

Primary current consumers:
- MiniTickets
- MiniAuth
- GeoCompare Web

## Core Working Rule

Start from shared standards. Do not invent project-local patterns unless the app clearly needs an exception.

When in doubt, prefer:
- cleaner
- calmer
- more consistent
- more reusable
- more implementation-neutral

## Interface Summary

Design philosophy:
- useful first
- modern, contemporary, minimal
- only what is needed and nothing that is not
- restrained, calm, deliberate
- standardize systems, not sameness

Primary inspirations:
- Helvetica-era modernism
- Massimo Vignelli
- Apple interface guidance and design philosophy

Secondary influences:
- Dieter Rams
- Michael Bierut

Visual defaults:
- support light and dark mode following system preference
- use neutral surfaces with restrained accent usage
- favor progressive disclosure over exposing everything at once
- reduce clutter before reducing space
- remove dividers and borders that do not carry meaning

Typography defaults:
- Helvetica when legally and practically available
- otherwise Inter for Latin UI text
- Noto Sans CJK or platform equivalent for Chinese text
- use a small shared type scale with role-based consistency
- do not force identical page-title placement across apps

Icon defaults:
- prefer Lucide for interoperability and consistency
- icons are optional and functional, not decorative
- use more icons in action-heavy products
- use fewer icons in data-heavy or map-heavy products
- for Lucide-style glyph favicons and app icons, default to a `272 px` maximum glyph dimension and `40 px` production stroke on a `512 x 512` artboard unless a product clearly needs an exception

Form-control defaults:
- both boxed inputs and bottom-line-only inputs are allowed depending on use case
- default to clear, low-noise, highly legible controls
- use bottom-line-only fields only when the workflow stays simple and usability remains strong

Shared metrics to preserve where practical:
- type scale
- spacing scale
- control heights
- icon sizes
- tap target sizes
- radius options

## Writing Summary

Copy should be:
- plain
- direct
- calm
- helpful
- short

Rules:
- prefer clear verbs and concrete nouns
- keep labels consistent across apps
- avoid clever phrasing in functional UI
- translate bilingual interfaces for meaning, not literal symmetry
- write errors so recovery is obvious

Saved-message rule:
- for routine same-page save outcomes, use the shared confirmation copy
- Chinese: `你的更改已保存。`
- English: `Your changes have been saved.`
- keep the treatment calm, use one page-level message, and place it below the page header above the first primary panel
- do not create custom variants unless the result changes what the user needs to do next

## Accessibility Summary

Treat accessibility as a default quality bar.

Always check:
- contrast in light and dark mode
- visible focus states
- keyboard access
- clear labels
- sufficient tap targets
- no color-only meaning
- understandable errors and status states

## CLI Summary

CLI tools should be:
- standardized
- accessible
- keyboard-first
- predictable
- automation-friendly where practical

Rules:
- use clear command and flag naming
- make `--help` useful and complete
- keep output readable without relying on color
- provide actionable errors and consistent exit-code behavior
- avoid surprise prompts in automation contexts
- prefer secure credential handling and avoid unnecessary repeated password entry

## Engineering Summary

Shared standards:
- implementation-neutral by default
- AI-implementation-neutral by default
- security-minded by default
- durable and reusable across projects
- practical and high-signal

Shorthand:
- `DSR` = docs refresh if applicable, security pass, and release
- `DR` = docs refresh required
- `DR(r)` = docs refresh recommended
- `SP` = security pass required
- `SP(r)` = security pass recommended
- `Release` = version bump if appropriate, commit, push, deploy or provide deploy instructions

Rules:
- shared guidance belongs here
- stack-specific, project-specific, person-specific, or AI-workflow-specific details belong in the app repo or a local overlay
- standards should be used wherever practical
- overlays should be additive, not replacements for the shared baseline without reason
- never commit secrets or machine-specific filled env files
- prefer secure credential handling that avoids unnecessary repeated password entry when approved tools like keychains, credential managers, passkeys, or short-lived sessions are available

Cross-app boundary defaults:
- a shared auth system may own identity, sessions, account active or inactive state, app-access grants, and a small shared preference surface
- downstream apps should keep app-specific authorization, workflow rules, and product-local settings
- if workspaces are truly shared across apps, centralize workspace identity and membership truth, but keep downstream authorization local
- if shared login is enabled, move shared preference controls such as locale, theme, and accent into the shared account surface rather than duplicating them in each app
- keep auth mail in the shared auth layer and product mail in each product, even when both use the same verified sending domain

## Small-App Infra Summary

For small self-hosted apps, use a lightweight minimum viable ops baseline:
- classify apps as `rebuildable`, `config-backed`, or `data-backed`
- define `RPO` and `RTO` targets
- keep at least one offsite backup destination independent from the primary server
- maintain a separate infra-backup stream for host config and recovery metadata
- verify backups with dry-restore checks, not only successful backup jobs
- add retention pruning
- keep one bootstrap path for rebuilding a server from scratch
- document build, deploy, health-check, and rollback steps
- rehearse recovery instead of assuming docs are enough
- disable SSH password auth and root login by default
- use security defaults that reduce avoidable maintenance friction

Privacy boundary:
- keep exact hostnames, IPs, secret locations, credential names, personal machine paths, and architecture-revealing recovery detail in private guidance, not public guidance

## Prisma Database Summary

For small Prisma apps:
- require an explicit `DATABASE_URL` in production
- avoid repo-root SQLite defaults such as `file:./dev.db` in deployed environments
- if SQLite is used in production, place it in a durable app-data path outside the repo working tree
- make runtime, seeds, cron scripts, and bootstrap scripts resolve the database URL the same way
- keep database paths, upload paths, and other derived storage clearly separated from app code
- make database location easy to explain, back up, verify, and restore
- keep development examples and production examples distinct

SQLite in production is acceptable for small single-server apps when concurrency is modest and the file location, backup path, and restore story are explicit.

## Shared Preference Summary

For related apps with a shared account system:
- shared systems may own preference values, but each app should own its own rendering, layout, and CSS
- prefer shared values, compatible enums, consistent root attributes, and app-local CSS variables
- keep the shared preference surface small: locale, theme, and accent are the default candidates
- keep app-specific notification settings, layout choices, feature flags, and broader profile customization out of the shared layer unless there is a strong cross-app reason
- use shared enums where practical, such as locale `ZH_CN` and `EN`, theme `SYSTEM`, `LIGHT`, and `DARK`, and a small shared accent set
- let each app read the shared value, apply root attributes like `data-theme` and `data-accent`, and render its own CSS variables and components
- standardize systems, not sameness
- do not let shared preference management quietly become a broad profile platform

## How Codex Should Use This Repo

At the start of a project or thread:
1. Read this file first.
2. Use it to set default design, writing, engineering, and release assumptions.
3. Open the full docs only for the sections needed by the task.
4. Keep decisions aligned with shared standards unless the app requires an explicit exception.
5. If creating an exception, document it in the app repo rather than mutating shared guidance too early.

## Source Documents

For fuller detail, use:
- `docs/interface-guidelines.md`
- `docs/content-style-guide.md`
- `docs/accessibility-checklist.md`
- `docs/engineering-guidelines.md`
- `docs/release-checklist.md`
- `docs/cli-guidelines.md`
