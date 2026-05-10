# ModifierAsFirstOptionalParam [rule] v0.1.0
Every component composable that emits layout exposes a `modifier: Modifier = Modifier` parameter. It comes after all required parameters and before all other optional ones. The modifier is applied to the ROOT element of the component's emitted layout — never to an inner child. This convention lets the caller adjust size, padding, click behaviour, semantics, or test tags from the outside without the component having to anticipate every possible adjustment.
domain: android-compose

## Checks
- [ ] Signature ends like: `Component(required1, required2, modifier: Modifier = Modifier, optionalA = ..., optionalB = ...)`.
- [ ] `modifier` defaults to `Modifier` (the empty modifier), never to a non-empty value with built-in padding or size.
- [ ] Internally, the modifier is forwarded to the outermost layout: `Box(modifier = modifier) { ... }`. Inner padding uses `Modifier.padding(...)` chained AFTER, e.g. `Box(modifier.padding(8.dp))`.
- [ ] Components do not accept multiple modifier parameters; if an inner element needs styling, expose a slot or a typed parameter, not a second Modifier.

## Label
`modifier: Modifier = Modifier` is the first optional parameter
