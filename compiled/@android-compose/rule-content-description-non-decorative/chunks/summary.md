# ContentDescriptionNonDecorative [rule] v0.1.0
TalkBack reads `contentDescription` aloud when focusing an image or icon. Every non-decorative visual that conveys information OR is the only label for an action must have a non-empty `contentDescription`. Purely decorative visuals (a divider flourish, a background pattern) must pass `contentDescription = null` so TalkBack skips them and does not read meaningless 'image' announcements. The choice is binary and required: passing the default `""` (empty string) is a bug.
domain: android-compose
