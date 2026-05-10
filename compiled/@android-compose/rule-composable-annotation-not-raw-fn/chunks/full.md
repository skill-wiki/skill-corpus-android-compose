# ComposableAnnotationNotRawFn [rule] v0.1.0
A function that emits Compose UI or invokes other @Composable functions must itself be marked @Composable. The annotation is a contract — it tells the compiler this function may only be called from another composable scope, may participate in recomposition, and reads CompositionLocals. Calling a composable from a non-composable site is a compile error; writing UI logic in a plain `fun` discards the contract and will not compile when it tries to emit content.
domain: android-compose

## Checks
- [ ] Every function that emits Text, Box, Column, or any Material 3 / Foundation widget is annotated @Composable.
- [ ] Composable function names use PascalCase (e.g. `UserCard`), matching how Compose APIs read at the call site.
- [ ] Composable functions return Unit — they emit, they do not produce values; values come back through hoisted state callbacks.
- [ ] Helper code that does NOT emit UI (data shaping, formatting) is a plain `fun`, not @Composable.

## Label
Compose UI functions are annotated @Composable, not plain Kotlin fns

## Label
Compose UI functions are annotated @Composable, not plain Kotlin fns
