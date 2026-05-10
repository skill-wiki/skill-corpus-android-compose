# ContentDescriptionNonDecorative [rule] v0.1.0
TalkBack reads `contentDescription` aloud when focusing an image or icon. Every non-decorative visual that conveys information OR is the only label for an action must have a non-empty `contentDescription`. Purely decorative visuals (a divider flourish, a background pattern) must pass `contentDescription = null` so TalkBack skips them and does not read meaningless 'image' announcements. The choice is binary and required: passing the default `""` (empty string) is a bug.
domain: android-compose

## Checks
- [ ] `Image(painter, contentDescription = "User avatar for $userName")` for informational images.
- [ ] `Image(painter, contentDescription = null)` for decorative-only visuals.
- [ ] `IconButton(onClick = { ... }) { Icon(Icons.Default.Delete, contentDescription = "Delete item") }` — the icon is the action label, so it MUST be described.
- [ ] When an icon sits NEXT TO a Text label (e.g. a labelled button), the icon is decorative — `contentDescription = null` — so TalkBack does not announce the same word twice.
- [ ] Descriptions are user-facing strings from a localised resource (`stringResource(R.string.delete_item)`), not hard-coded English.

## Label
Non-decorative images/icons get a contentDescription; decorative ones get null

## Label
Non-decorative images/icons get a contentDescription; decorative ones get null
