# NoSideEffectsInComposables [rule] v0.1.0
A @Composable function's body is called by the runtime on a schedule it controls — many times per second during animations, possibly with stale snapshots, possibly aborted half-way. The body must therefore be a pure function of its inputs and remembered state. Anything that touches the world — network calls, navigation, analytics events, mutating ViewModel state, registering listeners — goes inside a controlled effect: `LaunchedEffect`, `DisposableEffect`, `SideEffect`, or `rememberCoroutineScope`.
domain: android-compose
