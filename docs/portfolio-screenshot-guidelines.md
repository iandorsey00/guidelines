# Portfolio Screenshot Guidelines

## Purpose

Use this document to create repeatable, representative portfolio screenshots for visual apps.

Portfolio screenshots are curated product demonstrations. They are not visual-regression baselines, exhaustive documentation, or substitutes for interface testing.

## Core Rule

Every portfolio screenshot should be intentional, reproducible, safe to publish, and representative of the real product.

Standardize the capture method and quality bar. Let each app choose the scenes that best explain its value.

## Proportional Scope

Use the smallest screenshot set that explains the product:

- simple app: one strong primary screenshot, plus a social preview when useful
- app with several important surfaces: three to six screenshots that tell a coherent product story
- authenticated or data-backed app: a deterministic demo mode or synthetic fixture path for representative populated states

Do not manufacture extra screenshots merely to reach a target count. Prefer a short sequence with distinct purposes over a gallery of similar pages.

## Standard Repository Pattern

Prefer this structure where practical:

- `docs/portfolio/README.md`: screenshot manifest, narrative order, prerequisites, and capture instructions
- `docs/portfolio/screenshots/`: curated production PNGs
- `scripts/capture-portfolio.*`: repeatable app-local capture script
- `portfolio:capture` or the ecosystem-equivalent command: stable capture entry point

Prefer one capture command from the app root. It may manage the local server itself or document a separate server prerequisite when lifecycle management would add unnecessary complexity. When the capture target needs to be overridden, prefer the neutral `PORTFOLIO_URL` environment variable across apps.

The app repo owns its routes, selectors, fixtures, server command, and implementation details. Browser automation such as Playwright is recommended when the app already supports it, but the shared standard does not require one framework.

## Scene Selection

Choose scenes that explain the product rather than inventorying its pages.

Each screenshot should have a distinct role, such as:

- primary workflow or signature interaction
- meaningful populated state
- important secondary capability
- mobile or responsive behavior when central to the product
- calm empty, completion, or results state when it communicates product quality

Prefer credible in-progress states over sterile landing pages when they better show how the app works. Avoid menus, debug panels, temporary notices, or cursor placement that distract from the intended subject.

## Deterministic Capture

Automated capture should control enough state to produce stable, repeatable images:

- use a fixed viewport and device scale factor
- use an explicit color scheme, locale, timezone, and reduced-motion preference
- disable or finish non-essential animations before capture
- start from clean local state or a known synthetic fixture
- wait for a meaningful ready condition, including required fonts and content, rather than relying only on arbitrary delays
- control random, date-sensitive, or time-sensitive content when it affects the scene
- keep the pointer, focus state, and scroll position intentional
- avoid development overlays and transient loading artifacts

Recommended desktop starting point:

- viewport: `1440 x 1000`
- device scale factor: `2`
- color scheme: light
- locale and timezone: explicit values appropriate to the scene
- reduced motion: enabled
- format: PNG
- capture: viewport rather than full page unless the full page is the intended composition

This is a family baseline, not a universal crop. Add an intentional mobile viewport or dark-mode scene when it materially represents the product.

## Demo Mode And Synthetic Data

Authenticated or data-backed apps should provide a safe, reproducible way to capture realistic states. MiniTickets and similar products will usually need this; simple public or local-first apps may not.

A screenshot demo mode should:

- use clearly synthetic people, organizations, events, files, and account data
- produce the same useful state on every reset
- remain isolated from production data and credentials
- avoid sending email, notifications, payments, webhooks, or other external side effects
- avoid weakening production authentication or authorization
- require an explicit local, test, or otherwise controlled activation path
- fail closed if its environment or safety assumptions are not satisfied
- provide one documented reset or seed path

Prefer a small set of named scenarios over one oversized demo database. Keep screenshot-only fixture logic separate from normal production defaults, while reusing real rendering and workflows wherever safe.

Never capture production accounts, personal information, private hostnames, secrets, access tokens, or machine-specific details. Review visible data as carefully as committed source text.

## Output And Naming

- Use ordered, descriptive filenames such as `01-primary-workflow.png` and `02-results.png`.
- Keep the canonical images in `docs/portfolio/screenshots/` when repository size remains reasonable.
- Document each image's purpose in the portfolio README.
- Use meaningful alt text wherever an image appears in Markdown or HTML.
- Optimize files without visibly degrading text, fine lines, maps, or interface detail.
- Keep source screenshots free of added device frames, captions, or decorative marketing effects unless a separate presentation asset clearly needs them.

## Social Preview

When a repository or portfolio surface supports a social preview, derive it from the strongest representative scene or a deliberately composed equivalent.

Recommended starting point:

- aspect ratio: `2:1`
- output: `1440 x 720` PNG
- filename: `social-preview.png`

Check that the subject remains clear after platform cropping and at small display sizes. A social preview may use a tighter crop than the primary README screenshot, but should still represent the actual product honestly.

## Review And Maintenance

Review generated images before publishing. Confirm:

- the scene is visually stable and free of accidental overlays
- text and data are safe to publish
- the screenshot reflects current product behavior and visual design
- the sequence tells a coherent story without repetition
- light, dark, responsive, and bilingual states are represented when they materially matter
- the README image has accurate alt text and renders at a useful size
- the social preview remains legible in a small thumbnail

Refresh the set after substantial visual or workflow changes, before a portfolio milestone, or when an existing screenshot no longer represents the product. Routine releases do not require recapturing unchanged scenes.

## Do

- automate repeatable setup and capture
- use synthetic data that feels credible without resembling real people or accounts
- keep the set proportional to the product
- show the strongest product value early
- review every image as a public artifact

## Avoid

- using production data for convenience
- treating portfolio screenshots as test snapshots
- capturing unstable loading or animation frames
- requiring complex demo infrastructure for a simple app
- publishing many similar screens without a narrative purpose
- letting old screenshots quietly misrepresent the current product
