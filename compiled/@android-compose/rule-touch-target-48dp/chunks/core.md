# TouchTarget48dp [rule] v0.1.0
Any element a user can tap, click, or long-press — buttons, icon buttons, list rows, switches, links — must have a hit area of at least 48 dp by 48 dp. This is both a Material 3 baseline and a platform accessibility requirement (WCAG 2.5.5). The visual element may be smaller (e.g. a 24 dp icon), but the surrounding tappable region must reach 48 dp via padding, `Modifier.minimumInteractiveComponentSize()`, or component defaults.
domain: android-compose

## Checks
- [ ] Material 3 components (`IconButton`, `Switch`, `Checkbox`, `RadioButton`) ship with a built-in 48 dp hit slop — do NOT shrink them with `Modifier.size(...)` smaller than 48 dp.
- [ ] Custom `Modifier.clickable` regions wrap the visual at minimum 48 dp: `Modifier.size(48.dp).clickable { ... }` or add padding around a smaller icon.
- [ ] Use `Modifier.minimumInteractiveComponentSize()` on a Composable that should expand to the platform-mandated minimum.
- [ ] Adjacent tappable rows in a list have ≥ 8 dp spacing OR distinct full-width tap regions so the user does not mis-tap.
- [ ] Verify with the Compose UI testing API: `onNodeWithText("...").assertHeightIsAtLeast(48.dp).assertWidthIsAtLeast(48.dp)`.

## Label
Every interactive element has a minimum 48x48 dp touch target
