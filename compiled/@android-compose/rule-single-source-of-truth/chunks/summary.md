# SingleSourceOfTruth [rule] v0.1.0
Every value that drives the UI lives in exactly one place — a ViewModel, a remembered state holder, or a state-hoisted parameter. Composables read it and emit it. They do NOT copy it into a second `remember { mutableStateOf(...) }` they then keep in sync with the original via LaunchedEffect. Two copies of the same fact will drift the moment the synchronisation code has a bug, and you cannot tell which is correct.
domain: android-compose
