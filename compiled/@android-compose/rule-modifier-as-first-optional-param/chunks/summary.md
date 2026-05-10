# ModifierAsFirstOptionalParam [rule] v0.1.0
Every component composable that emits layout exposes a `modifier: Modifier = Modifier` parameter. It comes after all required parameters and before all other optional ones. The modifier is applied to the ROOT element of the component's emitted layout — never to an inner child. This convention lets the caller adjust size, padding, click behaviour, semantics, or test tags from the outside without the component having to anticipate every possible adjustment.
domain: android-compose
