# AvoidRecompositionViaRemember [rule] v0.1.0
A composable's body re-runs on every recomposition. Anything allocated or computed at the top level of the body — a parser, a Regex, a sorted list, a formatted string — runs every recomposition unless wrapped in `remember`. Pure observable derivations should use `derivedStateOf`, which only emits when its result changes (skipping recompositions whose inputs change but whose output does not). Remember keys must be the inputs that, when changed, require recomputation.
domain: android-compose

## Checks
- [ ] Allocations or expensive computations are wrapped: `val parser = remember { JsonParser(...) }`.
- [ ] Derived state from snapshot reads uses `remember { derivedStateOf { ... } }` so consumers only recompose when the derived value changes.
- [ ] Remember keys list every input the computation depends on: `remember(query, locale) { fuse(query, locale) }`.
- [ ] Functions defined inside a composable body that capture state are wrapped in `remember` to keep referential equality stable across recompositions.

## Label
Cache expensive values across recompositions with `remember` / `derivedStateOf`
