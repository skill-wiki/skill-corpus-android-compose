# SemanticTreeViaModifierSemantics [rule] v0.1.0
The Compose accessibility tree is what TalkBack and ui-test see. By default it mirrors the composable tree, but custom widgets, merged groupings, and dynamic state often need explicit shaping via `Modifier.semantics { }` and `Modifier.clearAndSetSemantics { }`. Set roles (Button, Switch, Heading), state (`stateDescription`, `selected`, `toggleableState`), labels (`contentDescription`, `text`), and relationships (`liveRegion`, `error`, `traversalIndex`). Do NOT control screen-reader output by hiding views with `alpha(0f)` or by cramming everything into one giant contentDescription.
domain: android-compose

## Checks
- [ ] Custom controls declare their role: `Modifier.semantics { role = Role.Button }`.
- [ ] Composite rows that should be announced as a single unit use `Modifier.semantics(mergeDescendants = true) { contentDescription = "$user, $time, $unread unread" }`.
- [ ] Live announcements (toast-equivalents, async results) use `Modifier.semantics { liveRegion = LiveRegionMode.Polite }`.
- [ ] Headings get `Modifier.semantics { heading() }` so TalkBack rotor users can jump between them.
- [ ] Form errors use `Modifier.semantics { error("Email is invalid") }` — TalkBack reads it after the field label.
- [ ] Decorative wrappers that confuse the screen reader use `Modifier.clearAndSetSemantics { }` to drop their contribution.

## Label
Shape the accessibility tree with Modifier.semantics, not visual hacks
