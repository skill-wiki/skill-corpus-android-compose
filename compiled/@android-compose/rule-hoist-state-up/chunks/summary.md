# HoistStateUp [rule] v0.1.0
A composable that displays a piece of state should NOT own it. Owning means calling `remember { mutableStateOf(...) }` inside the composable that renders. Instead the composable accepts the value as a parameter and emits change events through a callback. The caller hoists the state to the lowest common ancestor of every composable that needs to read or change it. This makes the component stateless, reusable, testable, and previewable, and lets the caller wire the same component to a ViewModel, a saved state, or a parent composable.
domain: android-compose
