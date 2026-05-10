# PreferStableKeysInLazyColumn [rule] v0.1.0
`LazyColumn`, `LazyRow`, and `LazyVerticalGrid` use the `key` parameter on each item to identify it across recompositions. Without a key, Compose falls back to position — which means inserting at the head re-keys every following item, animations break, scroll position drifts, and per-item state (like a remembered expand flag) jumps to the wrong row. Pass a `key = { item -> item.id }` whose value is stable for the lifetime of that item.
domain: android-compose

## Checks
- [ ] Every `items(...)` and `itemsIndexed(...)` call has an explicit `key = { ... }` lambda when the list is mutable or paginated.
- [ ] Keys are unique within the list and stable across reorderings (typically a primary-key id from the data model).
- [ ] Keys are NOT the index, NOT the hashCode of the whole item, NOT a randomly generated value at composition time.
- [ ] Keys are types Compose treats as Saveable (Int, Long, String, parcelable) so list state survives configuration change.

## Label
Pass stable, unique `key` to LazyColumn / LazyRow items

## Label
Pass stable, unique `key` to LazyColumn / LazyRow items
