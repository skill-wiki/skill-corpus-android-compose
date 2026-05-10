# EdgeToEdgeInsets [pattern] v0.1.0
On Android 15+ activities are edge-to-edge by default — content draws behind the status bar and navigation bar, all the way to the screen edges. The app must consume the system insets per component so interactive content is not hidden under the bars. Using `Scaffold` or applying `Modifier.windowInsetsPadding(WindowInsets.systemBars)` to specific containers gives the right result; setting a single padding around the whole app reintroduces a black band and defeats the visual.
domain: android-compose

## Label
Draw under system bars; respect insets per-component

## Problem
Without explicit handling, edge-to-edge means a button at the bottom of the screen is partly under the gesture bar (untappable) and a TopAppBar looks fine but the column underneath starts beneath the status bar (overlapping clock). Inversely, naively adding `Modifier.padding(16.dp)` everywhere brings back letterbox bands — the OS is now drawing the bars on top of empty space.

## Solution
```
    Enable edge-to-edge once at the activity:
      enableEdgeToEdge()  // androidx.activity.compose

    Then consume insets at the Scaffold or composable boundary:
      Scaffold(
        topBar    = { TopAppBar(...) },                   // consumes top insets
        bottomBar = { BottomAppBar(...) },                // consumes bottom insets
        content   = { padding -> Column(Modifier.padding(padding)) { ... } },
      )

    For non-scaffolded screens, scope insets explicitly:
      Modifier.windowInsetsPadding(WindowInsets.systemBars)
      Modifier.windowInsetsPadding(WindowInsets.navigationBars)
      Modifier.imePadding()      // for keyboard
      Modifier.safeDrawingPadding()  // catch-all for safe content area

    Do NOT set the activity background to an opaque color and re-add
    margins matching the system bars — the bar tint should come from
    the OS over your content, not the other way around.
  
```
