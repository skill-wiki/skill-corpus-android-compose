# EdgeToEdgeInsets [pattern] v0.1.0
On Android 15+ activities are edge-to-edge by default — content draws behind the status bar and navigation bar, all the way to the screen edges. The app must consume the system insets per component so interactive content is not hidden under the bars. Using `Scaffold` or applying `Modifier.windowInsetsPadding(WindowInsets.systemBars)` to specific containers gives the right result; setting a single padding around the whole app reintroduces a black band and defeats the visual.
domain: android-compose
