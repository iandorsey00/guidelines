# Accessibility Checklist

## Purpose

Use this checklist during design, implementation, and review.

Accessibility is a default quality standard, not a final cleanup step.

## Targets

Default to `WCAG 2.1 Level AA` as the shared conformance target across apps unless a product documents a stronger goal.

Concrete values to design and review against:

- text contrast: at least `4.5:1` for normal body text against its background
- large text contrast: at least `3:1` for text that is `18pt` or larger, or `14pt` bold or larger
- non-text contrast: at least `3:1` for UI components, focus indicators, icons with meaning, and graphical elements needed to understand content
- focus indicator: visible in both light and dark mode, and distinct from hover
- tap targets: at least `44 x 44 pt` on touch surfaces unless spacing around a smaller control keeps activation comfortable; treat this as the shared default
- minimum interactive target size for non-touch pointers: at least `24 x 24 CSS px` per `WCAG 2.2 Target Size (Minimum)`
- text resize: content must remain usable at `200%` zoom without loss of functionality or horizontal scrolling at common breakpoints
- motion: respect `prefers-reduced-motion`; avoid parallax, auto-playing motion, or non-essential animation by default

When a product has a documented reason to aim higher (for example, `AAA` contrast of `7:1` for critical text), record that target in the app repo rather than loosening the shared default here.

## Core Checks

- Verify sufficient contrast in light mode and dark mode.
- Ensure all interactive elements have visible focus states.
- Confirm keyboard access for navigation and core actions.
- Ensure tap targets are large enough on mobile.
- Do not rely on color alone to communicate meaning.
- Provide clear labels for inputs, actions, and navigation.
- Ensure error states are understandable and recoverable.
- Check that icons with important meaning have text labels or accessible names.
- Preserve readability at common zoom levels and smaller screen sizes.
- Confirm screen-reader-relevant names and roles exist for key interactions.

## Forms

- Every field has a visible label.
- Helper text is associated with the correct field.
- Error messages identify the problem clearly.
- Required fields are indicated clearly and consistently.
- Focus order follows the visual and logical flow.

## Lists And Data Views

- Row structure is easy to scan visually and semantically.
- Repeated actions are labeled consistently.
- Dense data remains readable without relying on tiny text.
- Status indicators are understandable without color alone.

## Mobile

- Text remains readable without precision zooming.
- Controls can be tapped comfortably.
- Sticky headers, sheets, or bottom actions do not block important content.
- Responsive changes preserve meaning and task flow.

## Review Trigger

Run an accessibility check when:
- introducing new interface patterns
- changing forms or navigation
- adding new status or validation states
- adjusting light or dark theme behavior
- compressing layouts for mobile or dense data
