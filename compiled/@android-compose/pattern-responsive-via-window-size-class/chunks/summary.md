# ResponsiveViaWindowSizeClass [pattern] v0.1.0
Read the current window dimensions through `currentWindowAdaptiveInfo()` and switch layout topology by `WindowWidthSizeClass` (Compact / Medium / Expanded) and `WindowHeightSizeClass`. Compact = phone portrait (1-pane). Medium = unfolded foldable / small tablet (1.5-pane or list-detail). Expanded = tablet / desktop / large foldable (2-pane or 3-pane). Don't write `if (configuration.screenWidthDp > 600)`-style breakpoints — that hard-codes thresholds the platform may revise and ignores the proper API.
domain: android-compose
