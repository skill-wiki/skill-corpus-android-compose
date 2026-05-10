# AvoidRecompositionViaRemember [rule] v0.1.0
A composable's body re-runs on every recomposition. Anything allocated or computed at the top level of the body — a parser, a Regex, a sorted list, a formatted string — runs every recomposition unless wrapped in `remember`. Pure observable derivations should use `derivedStateOf`, which only emits when its result changes (skipping recompositions whose inputs change but whose output does not). Remember keys must be the inputs that, when changed, require recomputation.
domain: android-compose
