# ResponsiveViaWindowSizeClass [pattern] v0.1.0
Read the current window dimensions through `currentWindowAdaptiveInfo()` and switch layout topology by `WindowWidthSizeClass` (Compact / Medium / Expanded) and `WindowHeightSizeClass`. Compact = phone portrait (1-pane). Medium = unfolded foldable / small tablet (1.5-pane or list-detail). Expanded = tablet / desktop / large foldable (2-pane or 3-pane). Don't write `if (configuration.screenWidthDp > 600)`-style breakpoints — that hard-codes thresholds the platform may revise and ignores the proper API.
domain: android-compose

## Label
Adapt layout to phone / tablet / foldable via WindowSizeClass

## Problem
An app designed for a 360 dp phone screen looks empty on a tablet (huge whitespace, content trapped in a phone-width column) and broken on a foldable (the hinge crosses important content, half the layout is wasted). Writing per-screen-size logic by querying raw dp values scatters magic numbers and misses platform updates.

## Solution
```
    Use the official adaptive API:

      val adaptiveInfo = currentWindowAdaptiveInfo()
      when (adaptiveInfo.windowSizeClass.windowWidthSizeClass) {
        WindowWidthSizeClass.COMPACT  -> SinglePaneScreen(...)
        WindowWidthSizeClass.MEDIUM   -> ListDetailLayout(...)
        WindowWidthSizeClass.EXPANDED -> TwoPaneLayout(...)
      }

    For list-detail flows specifically, use the dedicated scaffold:

      NavigableListDetailPaneScaffold(
        navigator = rememberListDetailPaneScaffoldNavigator(...),
        listPane = { ... },
        detailPane = { ... },
      )

    The scaffold handles back behaviour, hinge avoidance, and pane
    visibility automatically across phone / tablet / foldable.
  
```
