# ComposableAnnotationNotRawFn [rule] v0.1.0
A function that emits Compose UI or invokes other @Composable functions must itself be marked @Composable. The annotation is a contract — it tells the compiler this function may only be called from another composable scope, may participate in recomposition, and reads CompositionLocals. Calling a composable from a non-composable site is a compile error; writing UI logic in a plain `fun` discards the contract and will not compile when it tries to emit content.
domain: android-compose
