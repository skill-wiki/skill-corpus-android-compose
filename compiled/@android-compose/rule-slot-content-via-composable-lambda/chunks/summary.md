# SlotContentViaComposableLambda [rule] v0.1.0
When a component has a region the caller might want to customise — header, leading icon, trailing action, body — expose that region as a `@Composable () -> Unit` parameter (a 'slot'), not as a typed config object or a String. The component lays out the slot; the caller fills it with whatever composables it likes. This is how Material 3 components like `Scaffold`, `TopAppBar`, `ListItem`, and `Card` stay flexible without exploding their parameter lists.
domain: android-compose
