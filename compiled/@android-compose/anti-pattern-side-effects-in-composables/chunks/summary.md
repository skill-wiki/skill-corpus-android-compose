# SideEffectsInComposables [anti-pattern] v0.1.0
Putting impure work — `viewModel.fetchUser()`, `analytics.log("viewed")`, `scope.launch { ... }`, or `someState.value = computed` — at the top level of a @Composable function, where it executes on every recomposition rather than inside a controlled effect API.
domain: android-compose
