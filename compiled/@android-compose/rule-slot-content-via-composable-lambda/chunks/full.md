# SlotContentViaComposableLambda [rule] v0.1.0
When a component has a region the caller might want to customise — header, leading icon, trailing action, body — expose that region as a `@Composable () -> Unit` parameter (a 'slot'), not as a typed config object or a String. The component lays out the slot; the caller fills it with whatever composables it likes. This is how Material 3 components like `Scaffold`, `TopAppBar`, `ListItem`, and `Card` stay flexible without exploding their parameter lists.
domain: android-compose

## Checks
- [ ] Customisable regions are `content: @Composable () -> Unit` (or a typed scope receiver, e.g. `@Composable RowScope.() -> Unit`).
- [ ] Multiple slots are named for the region they fill: `title`, `leadingIcon`, `trailingContent`, `bottomBar`, `content`.
- [ ] The primary content slot is conventionally named `content` and is the LAST parameter — so callers can use trailing-lambda syntax: `Card { ... }`.
- [ ] Slots receive their own scope when geometry context matters (e.g. `RowScope`, `ColumnScope`) so callers can use `Modifier.weight(...)` inside.

## Label
Expose customisable regions as @Composable content lambdas (slots)

## Label
Expose customisable regions as @Composable content lambdas (slots)
