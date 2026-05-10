# SingleSourceOfTruth [rule] v0.1.0
Every value that drives the UI lives in exactly one place — a ViewModel, a remembered state holder, or a state-hoisted parameter. Composables read it and emit it. They do NOT copy it into a second `remember { mutableStateOf(...) }` they then keep in sync with the original via LaunchedEffect. Two copies of the same fact will drift the moment the synchronisation code has a bug, and you cannot tell which is correct.
domain: android-compose

## Checks
- [ ] No `LaunchedEffect(externalValue) { internalState = externalValue }` patterns — that is a duplicated source of truth.
- [ ] Forms read directly from the ViewModel state object; they do not snapshot it into a local copy at composition time.
- [ ] When a composable needs a derived value from another value, use `derivedStateOf` or compute it directly — do not store the derived result.
- [ ] Selection, scroll, and focus state belong to a hoisted state holder (e.g. `LazyListState`, `TextFieldState`), used by both reader and writer.

## Label
Each piece of state has exactly one owner; UI reads, never duplicates
