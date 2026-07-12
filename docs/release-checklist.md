# Release Checklist

## Purpose

Use this checklist when work is being prepared for commit, push, or release.

Release work should be proportional to the scope and risk of the change. Proportional does not mean skipping basic release safety.

## Shared Terms

- `RC` = proportional release cycle
- `FRC` = full release cycle using every available release gate
- `CP` = review, commit, and push without an implied release
- `RRC` = recommended release cycle: assess the changes, choose `RC` or `FRC`, briefly explain the choice, and perform it
- `DSR` = legacy alias for `RRC`

## CP: Commit And Push

Use `CP` when the work only needs an intentional commit and push.

Include:
- review the intended diff
- check for secrets and unintended files
- create an appropriate commit
- push the branch

`CP` does not imply:
- version bump
- documentation work
- dependency audit
- comprehensive release testing
- deployment

## RC: Release Cycle

Use `RC` for normal releases where release work should scale with the risk and breadth of the changes.

Always include:
- review the intended diff
- refresh relevant documentation
- run relevant automated tests
- check for secrets and unintended files
- run basic release metadata checks
- bump the version when appropriate
- commit and push

Broader changes should receive broader testing and security review.

## FRC: Full Release Cycle

Use `FRC` for milestones, substantial features, architectural changes, security-sensitive work, or releases with broad user-facing impact.

Include:
- complete documentation review
- security review and dependency audit
- full automated test suite
- browser or end-to-end tests where applicable
- release metadata and cache-busting validation where applicable
- version bump
- post-bump consistency check
- commit and push
- deployment and rollback instructions when applicable

## RRC: Recommended Release Cycle

Use `RRC` when the appropriate release depth is not obvious.

Process:
- assess the scope, risk, and release impact of the current changes
- choose `RC` or `FRC`
- briefly state the choice
- perform the selected release cycle

Treat legacy `DSR` requests as `RRC`.

## Baseline Rule

Every release cycle should include:
- `git diff --check` or equivalent
- review for secrets and unintended files
- relevant automated tests
- documentation updates where behavior or usage changed
- version consistency checks when a version is changed
- intentional commit and push

Proportional release work changes the breadth of review and testing. It does not remove basic release safety.

## Versioning Guidance

Classify changes using standard release concepts:
- patch: fixes, copy changes, styling adjustments, and narrow behavioral changes
- minor: meaningful new features or expanded functionality
- major: incompatible behavior, major architecture changes, or significant product redefinition

Pre-1.0 projects may map these classifications onto their existing alpha or beta version scheme conservatively.

## Notes

- Keep app-specific release mechanics in the app repo.
- Keep this checklist shared, short, and reusable.
- If a project needs a more detailed release runbook, link to it from the app repo rather than expanding this document too far.
