# CLI Guidelines

## Purpose

Use this document to keep command-line tools consistent, accessible, and aligned with good engineering practice.

CLI apps should feel predictable, legible, and safe. Prefer usefulness over cleverness.

## Core Principles

- Standardize behavior wherever practical.
- Follow established CLI best practices by default.
- Design for keyboard-first use.
- Make output easy to scan for humans.
- Support automation where practical.
- Treat accessibility as a default quality bar.
- Reduce surprise, ambiguity, and unnecessary friction.

## Command Naming

- Prefer clear, conventional command names.
- Use verbs for actions and nouns for resources where that improves clarity.
- Keep naming consistent across related tools.
- Avoid novelty or branding in core command syntax.

## Flags And Arguments

- Use predictable flag names and keep them consistent across apps.
- Prefer long-form flags that are self-explanatory.
- Use short flags only for common, high-frequency actions.
- Keep argument order logical and stable.
- Do not overload one flag with multiple unrelated behaviors.
- Support `--help` and make it complete and useful.

## Output And Formatting

- Make default output easy to read in a normal terminal.
- Keep status, result, warning, and error output clearly distinguishable.
- Use structured or machine-readable output modes when automation is a realistic use case.
- Keep wording concise and direct.
- Do not require color to understand output.

## Errors And Exit Codes

- Error messages should explain what failed and what the user can do next.
- Prefer actionable errors over raw internal failures.
- Use exit codes consistently.
- Reserve noisy stack traces or debug details for explicit debug modes unless they are necessary for diagnosis.

## Color And Accessibility

- Color should be supportive, not required.
- Do not rely on color alone to communicate meaning.
- Keep contrast strong enough for common terminal themes.
- Assume users may run the CLI in light or dark terminal environments.
- Prefer readable formatting over dense ASCII ornamentation.

## Interactive Behavior

- Interactive prompts are useful, but should not block non-interactive workflows when flags or config can be provided safely.
- Prompt only when necessary.
- Confirm destructive actions clearly.
- Avoid excessive repeated prompts, especially for credentials, when a safer persistent mechanism exists.
- Keep interactive flows keyboard-first and easy to follow.

## Security And Secrets

- Never print secrets unnecessarily.
- Never encourage unsafe credential handling in command history or logs when safer options exist.
- Prefer secure environment, config, keychain, or credential-manager flows as appropriate.
- Use least privilege and least exposure by default.
- Make secure behavior the easy path.

## Configuration

- Keep configuration sources predictable and documented.
- Separate user-specific configuration from shared project configuration where possible.
- Make overrides explicit rather than magical.
- Do not require machine-specific setup to be guessed.

## Do

- keep command behavior predictable
- write useful help text
- make output readable and automation-friendly
- provide actionable errors
- support accessible terminal use
- make safe behavior the default

## Avoid

- inconsistent flag naming
- decorative or confusing output
- color-only meaning
- surprise prompts in automation contexts
- unnecessary credential friction
- unsafe defaults for destructive or security-sensitive actions
