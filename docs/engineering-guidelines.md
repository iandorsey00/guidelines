# Engineering Guidelines

## Purpose

Use this document to keep engineering and release behavior consistent across projects.

These rules should stay implementation-neutral and AI-implementation-neutral unless a specific tool, framework, or workflow detail is genuinely necessary.

This repo should define the stable default. Project repos or local overlays may add person-specific or implementation-specific guidance when it helps, but shared standards should remain the baseline wherever practical.

## Core Principles

- Shared guidance should be durable, practical, and easy to reuse.
- Prefer implementation-neutral and AI-implementation-neutral rules in this repo.
- Keep app-specific implementation details inside app repositories.
- Keep person-specific preferences and local workflow overlays separate from shared defaults unless they are broadly reusable.
- Treat good security as a central engineering philosophy, not a final pass or special-case concern.
- Optimize for maintainability, repeatability, and low ambiguity.
- Write docs so both humans and Codex can apply them quickly.
- Standards are good and should be used wherever practical.

## Shared Shorthand

- `DSR` = docs refresh if applicable, security pass, and release
- `DR` = docs refresh required
- `DR(r)` = docs refresh recommended
- `SP` = security pass required
- `SP(r)` = security pass recommended
- `Release` implies version bump when appropriate, commit, push, and deploy instructions

Use shorthand only when the meaning is already clear to the team or documented in the relevant repo. Prefer `DSR` when the intent is to run the full docs/security/release flow.

## What Belongs Here

- shared interface and engineering guidance
- cross-project conventions
- release and process expectations that apply broadly
- Codex collaboration defaults
- guidance that should remain useful across different tools, stacks, and AI workflows
- rules for separating shared guidance from project-specific implementation

## What Belongs In App Repos

- deployment scripts and operational runbooks tied to one project
- framework-specific implementation details
- environment-specific setup steps
- reusable project scripts that only matter inside that app
- release notes and deployment details unique to that app

Project-specific scripts may live in app repos when they are reusable inside that project, even if they should not be promoted to shared guidance.

## Overlays And Exceptions

- Use shared standards by default.
- Add project-specific overlays only when the product, stack, deployment target, or team workflow truly requires them.
- Add person-specific overlays only when they improve execution without weakening the shared baseline.
- Keep overlays additive where possible. They should clarify local practice, not replace stable shared guidance without reason.
- When an exception becomes broadly useful across projects, promote it back into shared guidance.

## Documentation Conventions

- Keep shared docs concise, opinionated, and scannable.
- Prefer practical defaults over exhaustive policy.
- Update shared docs when a convention should apply across multiple projects.
- Keep implementation-neutral product guidance separate from implementation-specific scripts and ops.
- Run `DR` when behavior, conventions, or workflows change enough to make docs stale.

## Release Expectations

- Treat release work as an explicit activity, not an implied side effect.
- If asked to `Release`, include the full chain unless told otherwise:
  1. version bump if appropriate
  2. commit
  3. push
  4. deploy instructions or deployment action as defined by the project
- Deployment does not need to use the same mechanism across apps, but it should meet the same shared standard: documented, repeatable, secure, verifiable, and recoverable.
- Record app-specific release mechanics in the app repo, not here.
- Prefer predictable versioning and repeatable release steps.

## Security Hygiene

Security should be built into normal engineering decisions from the start, including architecture, defaults, credential handling, deployment, and maintenance.

- Run `SP` for meaningful changes, especially around auth, data handling, dependencies, configuration, and deployment.
- Never commit secrets.
- Never commit machine-specific filled environment files.
- Commit only safe templates such as `.env.example` when needed.
- Keep dependency and access decisions conservative by default.
- Prefer the least privilege and least exposure that still supports the product.
- Prefer secure credential flows that reduce unnecessary repeated password entry when an approved, safer persistent mechanism exists, such as platform keychains, credential managers, passkeys, or short-lived authenticated sessions.
- Reduce avoidable security friction, but not by weakening core protections or expanding access beyond what is needed.

## Prisma Database Management

Use this guidance for small self-hosted apps that use Prisma and need calmer, safer database management without enterprise-heavy process.

Core rule:
- Do not let production database location, connection behavior, or migration behavior depend on accidental defaults. Be explicit.

Recommended practices:
- Require an explicit `DATABASE_URL` in production.
- Avoid repo-root SQLite defaults such as `file:./dev.db` for deployed environments.
- If SQLite is still used in production, place it in a dedicated app-data path outside the repo working tree.
- Use one shared helper or config path for resolving database URLs instead of repeating fallback strings across app code and scripts.
- Keep uploads and other derived storage paths clearly separated from the app code directory.
- Make backup targeting obvious by using stable database and data-directory paths.
- Ignore local database files and local data directories in git.
- Keep development examples and production examples distinct.
- Prefer production env examples that show a durable external path, not a local dev shortcut.

SQLite guidance:
- SQLite is acceptable for small single-server apps when concurrency is modest, operational simplicity matters, backups are understood, and restore steps are documented.
- If SQLite is used in production, choose a durable file path, make backup and restore steps explicit, avoid ambiguous working-directory-relative paths, and document how related file storage is resolved.

Prisma-specific guidance:
- Prisma runtime, seeds, cron scripts, and admin or bootstrap scripts should all resolve the database URL the same way.
- Do not let one script quietly talk to a different database because it carries its own fallback.
- Keep schema management and runtime database targeting aligned.
- If a release changes database shape destructively, document the exact one-time deploy step clearly.
- Prefer calm, explicit migration notes over hidden assumptions.

Example pattern:
- local development: `DATABASE_URL="file:./data/app-name.db"`
- production: `DATABASE_URL="file:/path/to/app-data/app-name.db"`

Anti-patterns:
- `file:./dev.db` as an implicit production fallback
- multiple hard-coded fallback database URLs across different scripts
- storing the production SQLite file in the repo root
- relying on deploy-time working-directory quirks
- mixing production data location with build artifacts or transient app files

Operational standard:
- Database location should be easy to explain, easy to back up, and easy to verify.
- A new operator should be able to answer where the database lives, what env var points to it, what scripts touch it, how it is backed up, and how it is restored.

## Small-App Infra Baseline

Treat this as a lightweight minimum viable operations standard for small self-hosted apps, not enterprise policy.

The baseline should combine:
- offsite backups
- tested backups, not just successful backup jobs
- disposable or rebuildable hosts where practical
- rehearsed rebuild and recovery steps
- security defaults that do not make solo maintenance unnecessarily painful

Defaults:
- Classify each app as `rebuildable`, `config-backed`, or `data-backed`.
- Define explicit `RPO` and `RTO` targets, even for solo projects.
- Keep one documented bootstrap path for rebuilding a server from scratch.
- Document per-app build, deploy, health-check, and rollback steps.
- Require at least one offsite backup destination independent from the primary server.
- Keep a separate infrastructure-backup stream for host config and recovery metadata, not only app-data backups.
- Prefer pull-based infra backups into an off-host location you control when that reduces dependence on the server being healthy.
- Verify infra backups with an automated dry-restore check that confirms the archive is readable, expected files are present, and extraction succeeds.
- Add retention pruning so backup automation does not quietly create an unbounded pile of snapshots.
- Rehearse disaster recovery instead of assuming documentation alone is sufficient.
- Disable SSH password auth and root login by default.
- Prefer SSH host aliases that describe the machine or role, especially when a host serves more than one app.
- Pair security hardening with friction-reducing habits such as stable SSH aliases and copy-pasteable bootstrap commands.
- Verify guidance automatically when possible, then add live checks near the actual infrastructure.
- When reviewing a user environment, default to metadata-only safety checks and avoid inspecting secret-bearing contents unless explicitly necessary.
- Schedule automation for times when the user device is realistically available, and prefer a load or login catch-up path when supported instead of assuming an ideal overnight schedule.

## Public Vs Private Infra Guidance

Keep public guidance focused on reusable operating principles.

Keep private details out of this repo, including:
- exact hostnames and IPs
- secret locations and credential names
- personal machine paths
- recovery ordering that exposes private architecture in unnecessary detail

## Git Expectations

- Keep commits intentional and understandable.
- Separate unrelated work where practical.
- Push only when the branch is in a coherent state.
- Do not bury significant product, security, or release changes inside vague commits.
- Keep shared-guidance changes especially clear because they affect future work.

## Codex Collaboration Conventions

- Start from shared guidance before inventing new local conventions.
- Prefer reusable patterns over one-off decisions.
- When a rule is app-specific, document it in the app repo instead of mutating shared guidance prematurely.
- Do not bind shared guidance too tightly to one AI tool's quirks, prompt style, or execution model.
- Keep output high-signal, practical, and easy to apply.
- Default toward cleaner, calmer, more consistent, and more reusable solutions when ambiguity exists.
- Flag exceptions clearly when deviating from shared guidance.

## Decision Rule

When deciding whether guidance belongs here or in an app repo, use this test:
- if it should apply across multiple current or future apps, put it here
- if it depends on one stack, one deployment target, one AI workflow, one person, or one product workflow, keep it in the app repo or a local overlay
