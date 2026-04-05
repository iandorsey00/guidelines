# Interface Guidelines

## Purpose

Use this document to keep products visually and behaviorally consistent across apps.

The target outcome is a calm, modern interface language that feels clear, capable, and restrained. Prefer continuity over novelty.

## Design Principles

- Design for usefulness first. The interface should help people complete tasks with low friction.
- Use only what is needed. Remove decoration, noise, and optional complexity unless it clearly improves comprehension.
- Prefer clarity over customization. Minimal customization is good when it does not reduce usability.
- Make hierarchy obvious. Users should be able to tell what matters at a glance.
- Use progressive disclosure. Hide advanced or rarely needed controls until they are relevant.
- Be consistent across apps. Similar actions and patterns should look and behave the same.
- Respect system behavior. Follow platform expectations, including system light and dark mode.
- Standardize systems, not sameness. Reuse shared rules for typography, spacing, density, controls, and behavior without forcing identical page compositions across different products.

## Visual Tone

Core references:
- Helvetica-era modernism
- Massimo Vignelli
- Apple interface guidance and design philosophy
- restrained functionalism, with Dieter Rams and Michael Bierut as secondary influences

Desired qualities:
- usable
- modern
- contemporary
- minimal
- forward-thinking
- calm
- deliberate

Avoid:
- flashy visual effects
- decorative clutter
- overly branded UI
- dense control surfaces shown by default
- novelty that fights comprehension

## Typography

- Prefer Helvetica when it is legally and practically available.
- For open-source Latin UI typography, default to Inter.
- For Chinese text, default to Noto Sans CJK or the platform equivalent.
- Use a sans-serif system with neutral tone, strong legibility, and minimal personality drift.
- Keep type hierarchy tight and intentional. Fewer sizes, fewer weights, clearer roles.
- Use body text sizes and line heights that remain comfortable on mobile.
- Define a small shared type scale across apps, but do not require every app to use the same page-title treatment.
- Standardize role-based typography such as page title, section title, body, secondary text, label, and caption. Let exact placement respond to the product's needs.

## Iconography

- Prefer Lucide icons for cross-app consistency and interoperability.
- Use icons to support comprehension, not as decoration.
- Pair icons with labels when meaning may be ambiguous.
- Choose simple, contemporary shapes with restrained stroke-based styling.
- Do not require icons everywhere. Use them when they improve scanning, recognition, or action clarity.
- In data-heavy or map-oriented products, icons should stay sparse and functional. In action-heavy products, they can play a larger supporting role.

## Standard App Icon Baseline

For simple monogram-based app icons, use this default production baseline unless a product clearly needs an exception.

Specifications:
- artboard: `512 x 512 px`
- background: black rounded rectangle
- background fill: `#000000`
- corner radius: `112 px`
- foreground: white monogram or initials
- foreground fill: `#FFFFFF`
- typeface: `Inter ExtraBold`
- starting type size: `280 pt`
- tracking: `-30`
- placement: visually centered around `(256, 256)`

Rules:
- treat the numeric center as a starting point, then optical-center by eye if needed
- prioritize small-size legibility over typographic purity
- use a monogram only when it remains unmistakable at small sizes
- keep contrast maximal
- avoid decorative effects, gradients, shadows, strokes, or textures
- prefer flat, quiet, high-confidence geometry
- export from the design source as a clean production asset

Recommended output:
- source design file in the design tool of choice
- production asset as `PNG 512 x 512`
- optional `SVG` only if export fidelity is reliable

## Color And Accent Usage

- Support both light and dark mode by default, following system preference unless a product has a strong reason not to.
- Use neutral surfaces and typography as the foundation.
- Reserve accent color for actions, focus states, selection, status emphasis, and moments that benefit from guidance.
- Do not let accent color dominate the interface.
- Where appropriate, inherit the MiniTickets accent approach: present, recognizable, restrained.

## Spacing And Density

- Favor generous spacing over dense packing.
- Group related content clearly.
- Reduce visual noise before reducing spacing.
- Default to comfortable density on mobile and laptop screens.
- Tight layouts are acceptable only when they improve scanning without feeling cramped.
- Define a small shared spacing system across apps so rhythm feels related even when layouts differ.

## Layout And Hierarchy

- Build layouts around one primary action or task at a time.
- Let pages breathe. Avoid filling space just because it exists.
- Use strong section hierarchy and predictable alignment.
- Keep navigation simple and stable.
- Prefer obvious page structure over clever layout moves.
- Standardize alignment logic and spacing rhythm before standardizing exact header position or page chrome.

## Forms And Controls

- Keep forms calm and direct.
- Show only the controls needed for the current step.
- Use clear labels, useful defaults, and inline help where needed.
- Make destructive or irreversible actions distinct.
- Prefer standard controls over custom-styled novelty components.

For shared-account products:
- if a shared auth or account system owns cross-app preferences, signed-in non-admin users should get a small account-preferences surface rather than a dead-end page
- keep that surface focused on genuinely shared values such as language, theme, and accent
- keep admin-only management clearly separate from ordinary user preference controls

## Lists And Detail Views

- Lists should optimize for scanning, comparison, and next action.
- Detail views should surface the most important information first.
- Secondary metadata should be visible but not dominant.
- Use consistent row rhythm, spacing, and affordances across products.

## Mobile Behavior

- Design mobile intentionally, not as a desktop layout squeezed smaller.
- Preserve clear hierarchy, tap comfort, and text readability.
- Collapse secondary actions before compromising primary flow.
- Treat responsive behavior as product design, not only layout adjustment.

## Responsive Design

- Adapt task flow, not only layout.
- Preserve the primary action and most important information at every screen size.
- Stack or reflow content before shrinking text below comfortable reading sizes.
- Collapse, group, or hide secondary controls before degrading the main workflow.
- Use max content widths where readability benefits from restraint.
- Avoid horizontal scrolling except when the interaction genuinely requires it.
- Let spacing and density adjust with screen size, but keep the interface calm and readable.
- Treat map-heavy, data-heavy, and form-heavy screens as separate responsive cases rather than forcing one pattern everywhere.
- Make responsive states feel intentionally designed, not like accidental leftovers from the desktop layout.

## Accessibility Expectations

- Meet accessibility requirements by default, not as cleanup.
- Maintain strong contrast in both light and dark mode.
- Ensure keyboard access, visible focus, and clear interaction states.
- Avoid relying on color alone to communicate meaning.
- Write labels and actions so they are understandable out of context.

## Copy And Labeling

- Use plain, direct language.
- Prefer short labels that describe the action or object clearly.
- Avoid filler text, internal jargon, and clever phrasing.
- When products are bilingual, prioritize consistency of meaning across languages over literal symmetry.

## Do

- reduce interfaces to the essential
- hide advanced functionality until needed
- use consistent spacing, hierarchy, and action patterns
- design for both human calm and fast comprehension
- make light and dark mode feel equally intentional
- remove visual separators that do not carry meaning

## Avoid

- exposing every possible option at once
- adding visual treatment without functional benefit
- mixing icon styles or type voices
- over-customizing controls at the cost of usability
- letting one app drift into a different design language without a clear reason
- using borders, dividers, and containers as a substitute for hierarchy

## Shared Metrics

Define a small set of shared metrics across apps:

- type scale
- spacing scale
- corner radius options
- control heights
- max content widths where relevant
- icon sizes
- minimum tap target sizes

Starter set:
- body text: default to 14-16px equivalent depending on platform and density
- section and page titles: use consistent role-based sizing across apps, but allow product-specific placement
- spacing: define a compact shared scale such as 4, 8, 12, 16, 24, 32
- control heights: define a small range and reuse it consistently
- icon sizes: keep to a small set such as small, default, and large
- tap targets: maintain mobile-friendly minimum target sizes

Do not over-specify:

- exact page-header position for every app
- identical navigation structures
- one mandatory card or panel style
- icons on every page or every primary action

Use shared metrics to create family resemblance. Use product-specific composition to serve the actual workflow.
