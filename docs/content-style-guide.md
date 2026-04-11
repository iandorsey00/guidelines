# Content Style Guide

## Purpose

Use this document to keep product language clear, calm, and consistent across apps.

The goal is simple, useful copy that supports the interface without adding noise.

## Core Principles

- Write for clarity first.
- Use plain language over clever language.
- Keep copy short, specific, and actionable.
- Match the visual system: calm, modern, restrained.
- Prefer consistency over novelty.
- In bilingual products, preserve meaning and tone across languages rather than forcing literal symmetry.

## Tone

Use a voice that is:
- clear
- calm
- direct
- helpful
- respectful

Avoid copy that feels:
- flashy
- overly branded
- cute at the expense of clarity
- bureaucratic
- vague

## Labels And Actions

- Prefer short labels with strong verbs or clear nouns.
- Name actions by what they do.
- Keep similar actions named the same way across apps.
- Avoid synonyms for the same action unless the meaning truly differs.
- Prefer explicit labels over abstract product language.

Examples:
- use `Save` instead of `Confirm Changes`
- use `Delete ticket` instead of `Remove`
- use `Search places` instead of `Explore`

## Buttons

- Primary buttons should describe the main action clearly.
- Secondary buttons should stay short and predictable.
- Avoid generic button text like `Submit` unless the context is already obvious.
- Prefer consistent action verbs across products.

## Form Copy

- Labels should identify the field, not explain the whole workflow.
- Helper text should appear only when it reduces confusion.
- Placeholder text should support the field, not replace the label.
- Error text should explain what is wrong and what to do next.

## Errors And Validation

- State the problem plainly.
- When possible, tell the user how to fix it.
- Avoid blame and avoid internal system language.
- Keep validation messages consistent across products.

Examples:
- `Enter a valid email address.`
- `Choose a date before continuing.`
- `We couldn't load this data. Try again.`

Avoid:
- `Invalid input`
- `Submission failed`
- `Unexpected error occurred`

## Empty States

- Explain what is missing.
- Provide the next useful action if there is one.
- Keep empty states brief and calm.
- Do not fill empty states with decorative language.

## Status And Feedback

- Confirm success without being noisy.
- Keep status text short and specific.
- Use consistent wording for loading, saving, success, and failure states.

Examples:
- `Saved`
- `Saving...`
- `No results found`
- `Location updated`

## Saved Success Messages

Standardize short save-confirmation messages across apps so the experience feels calmer, more consistent, and easier to recognize.

Core rule:
- Use one shared success message for ordinary save-style actions.
- Chinese: `你的更改已保存。`
- English: `Your changes have been saved.`
- Do not create page-by-page variants unless the action result truly changes what the user needs to do next.

Use this message for routine save outcomes such as settings changes, record edits, workspace or object updates, and create, update, or delete flows that return to the same page.

Avoid variants such as:
- `设置已保存。`
- `工作区已保存。`
- `已更新。`
- `Changes saved successfully.`

Visual treatment:
- use a calm success treatment
- use a green success tone with a soft light background
- keep the message short and single-line
- do not add an extra icon by default

Placement:
- show the message once per page
- place it immediately below the page header
- place it above the first primary panel or content section

Use the shared save message when:
- the user stays on the same page after the action
- the result is a normal successful save
- no extra next-step instruction is needed

Do not use the generic saved message for:
- destructive actions such as delete or archive
- authentication changes
- background jobs or maintenance actions
- upload-specific results when the file action itself is the key outcome
- warnings or partial-success states

Cross-app consistency rule:
- related apps in the same product family should share the same saved-message copy
- related apps in the same product family should share the same success tone
- related apps in the same product family should share the same placement rule

## Bilingual Guidance

- Translate for meaning, not word count.
- Keep action labels parallel in intent across languages.
- Prefer terms that feel natural to native readers.
- Maintain consistent terminology for repeated product concepts.
- When one language must be primary, make that choice deliberate and consistent at the product level.

## Do

- use direct verbs and concrete nouns
- keep labels short
- reuse established terms
- write error messages that help recovery
- make bilingual wording consistent in meaning and tone

## Avoid

- filler text
- clever slogans in functional UI
- inconsistent naming for the same action
- placeholder-only forms
- literal translation that makes the interface feel unnatural
