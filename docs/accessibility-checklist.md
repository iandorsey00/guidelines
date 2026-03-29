# Accessibility Checklist

## Purpose

Use this checklist during design, implementation, and review.

Accessibility is a default quality standard, not a final cleanup step.

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
