# Release Checklist

## Purpose

Use this checklist when work is being prepared for release.

This document turns shared shorthand into a repeatable workflow.

## Shared Terms

- `DR` = docs refresh required
- `DR(r)` = docs refresh recommended
- `SP` = security pass required
- `SP(r)` = security pass recommended
- `Release` = version bump if appropriate, commit, push, and deploy or provide deploy instructions

## Pre-Release

- Confirm the work is in a coherent, reviewable state.
- Confirm scope matches the intended release.
- Run `DR` or `DR(r)` as appropriate.
- Run `SP` or `SP(r)` as appropriate.
- Verify any project-specific checks defined in the app repo.

## Release Action

When asked to `Release`, do the following unless the project defines a documented exception:

1. Bump version if appropriate.
2. Commit with a clear, intentional message.
3. Push the branch or release commit.
4. Deploy or provide the exact deployment instructions defined by the project.

## Documentation Refresh

Run `DR` when:
- behavior changed enough to make docs stale
- shared conventions changed
- setup, release, or operator instructions changed
- UI or workflow changed in a way future contributors need to know

Use `DR(r)` when a docs update would be helpful but is not strictly necessary for safe continuation.

## Security Pass

Run `SP` when:
- auth, permissions, or secrets handling changed
- data handling changed
- dependencies changed in a meaningful way
- deployment or configuration changed
- external integrations changed

Use `SP(r)` when risk is lower but a quick security-minded review is still worthwhile.

## Notes

- Keep app-specific release mechanics in the app repo.
- Keep this checklist shared, short, and reusable.
- If a project needs a more detailed release runbook, link to it from the app repo rather than expanding this document too far.
