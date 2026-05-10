# PreferStableKeysInLazyColumn [rule] v0.1.0
`LazyColumn`, `LazyRow`, and `LazyVerticalGrid` use the `key` parameter on each item to identify it across recompositions. Without a key, Compose falls back to position — which means inserting at the head re-keys every following item, animations break, scroll position drifts, and per-item state (like a remembered expand flag) jumps to the wrong row. Pass a `key = { item -> item.id }` whose value is stable for the lifetime of that item.
domain: android-compose
