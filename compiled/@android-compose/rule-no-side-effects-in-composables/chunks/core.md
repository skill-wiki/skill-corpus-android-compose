# NoSideEffectsInComposables [rule] v0.1.0
A @Composable function's body is called by the runtime on a schedule it controls — many times per second during animations, possibly with stale snapshots, possibly aborted half-way. The body must therefore be a pure function of its inputs and remembered state. Anything that touches the world — network calls, navigation, analytics events, mutating ViewModel state, registering listeners — goes inside a controlled effect: `LaunchedEffect`, `DisposableEffect`, `SideEffect`, or `rememberCoroutineScope`.
domain: android-compose

## Checks
- [ ] No coroutine launches, no network calls, no log statements, no analytics emits at the top level of a composable body.
- [ ] One-shot work tied to a key: `LaunchedEffect(userId) { repository.load(userId) }`.
- [ ] Resource registration with cleanup: `DisposableEffect(lifecycleOwner) { ...; onDispose { ... } }`.
- [ ] Synchronising Compose state to a non-Compose system: `SideEffect { Firebase.analytics.setUser(uid) }`, runs only after a successful composition.
- [ ] User-event handlers (button clicks) launch from a `rememberCoroutineScope()` — never from `LaunchedEffect` triggered by clicking.

## Label
Composable bodies are pure; side effects go through effect APIs
