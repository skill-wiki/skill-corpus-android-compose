# TypographyScaleTokens [rule] v0.1.0
Material 3 defines a 15-step type scale across five role families — `displayLarge/Medium/Small`, `headlineLarge/Medium/Small`, `titleLarge/Medium/Small`, `bodyLarge/Medium/Small`, `labelLarge/Medium/Small` — exposed as `MaterialTheme.typography.<role>`. Reference the role; do not set `fontSize`, `fontWeight`, `lineHeight`, and `letterSpacing` ad hoc. Roles encode hierarchy, density, and accessibility-tested defaults; ad hoc styles drift across screens and break Dynamic Type.
domain: android-compose

## Checks
- [ ] Text styles come from `MaterialTheme.typography.<role>` passed via `Text(text, style = ...)`.
- [ ] Screen titles use `titleLarge` or `headlineSmall` depending on prominence; do not invent 24sp+bold yourself.
- [ ] Body copy uses `bodyLarge` (default reading text) or `bodyMedium`; captions and metadata use `bodySmall` or `labelSmall`.
- [ ] Buttons inherit `labelLarge` from `Button` defaults; don't override with custom sp values.
- [ ] Custom typography overrides happen by replacing the `Typography` in the `MaterialTheme(...)` setup, not by passing inline `TextStyle` everywhere.

## Label
Use Material 3 type scale roles (display/headline/title/body/label)

## Label
Use Material 3 type scale roles (display/headline/title/body/label)
