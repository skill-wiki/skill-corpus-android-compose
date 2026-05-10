# HoistStateUp [rule] v0.1.0
A composable that displays a piece of state should NOT own it. Owning means calling `remember { mutableStateOf(...) }` inside the composable that renders. Instead the composable accepts the value as a parameter and emits change events through a callback. The caller hoists the state to the lowest common ancestor of every composable that needs to read or change it. This makes the component stateless, reusable, testable, and previewable, and lets the caller wire the same component to a ViewModel, a saved state, or a parent composable.
domain: android-compose

## Checks
- [ ] Components take `value: T` and `onValueChange: (T) -> Unit` parameters; they do not own their displayed state internally.
- [ ] If a `remember { mutableStateOf(...) }` lives inside a reusable component, audit it — it likely belongs hoisted up.
- [ ] Stateful wrappers exist as a convenience overload that internally creates the state and forwards to the stateless implementation; both ship.
- [ ] Previews can render every interesting state by passing different `value` parameters — no need to drive interaction.

## Label
Hoist state to the lowest common ancestor; pass value-down, event-up

## Label
Hoist state to the lowest common ancestor; pass value-down, event-up
