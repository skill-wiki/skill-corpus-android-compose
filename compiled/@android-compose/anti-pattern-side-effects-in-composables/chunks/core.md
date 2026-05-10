# SideEffectsInComposables [anti-pattern] v0.1.0
Putting impure work — `viewModel.fetchUser()`, `analytics.log("viewed")`, `scope.launch { ... }`, or `someState.value = computed` — at the top level of a @Composable function, where it executes on every recomposition rather than inside a controlled effect API.
domain: android-compose

## Label
Calling viewModel.load(), launching coroutines, or mutating state directly in a composable body

## Why Bad
The Compose runtime calls a composable's body whenever any state it reads changes. During a single user interaction (typing, scrolling, animating) that can be hundreds of times. Each call re-fires the side effect: hundreds of network requests, hundreds of analytics events, ViewModel state churning in a feedback loop. Worse, the runtime can abort a composition mid-way; work started at the top level may run for a frame that is never displayed. The cumulative result is wasted bandwidth, duplicated rows in analytics, lost write ordering, and bugs that only reproduce under specific recomposition patterns.

## Instead Do
```
    Move every side effect into the appropriate effect API:

      - One-shot work bound to a key:
            LaunchedEffect(userId) { vm.load(userId) }
      - Resources with cleanup:
            DisposableEffect(owner) { register(); onDispose { unregister() } }
      - Sync Compose state to a non-Compose system:
            SideEffect { Firebase.analytics.setUserProperty(...) }
      - Trigger from user events (clicks):
            val scope = rememberCoroutineScope()
            Button(onClick = { scope.launch { vm.save() } }) { ... }

    The composable body itself stays pure: read state, emit UI, return Unit.
  
```
