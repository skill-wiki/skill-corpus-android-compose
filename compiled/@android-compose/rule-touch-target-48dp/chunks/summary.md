# TouchTarget48dp [rule] v0.1.0
Any element a user can tap, click, or long-press — buttons, icon buttons, list rows, switches, links — must have a hit area of at least 48 dp by 48 dp. This is both a Material 3 baseline and a platform accessibility requirement (WCAG 2.5.5). The visual element may be smaller (e.g. a 24 dp icon), but the surrounding tappable region must reach 48 dp via padding, `Modifier.minimumInteractiveComponentSize()`, or component defaults.
domain: android-compose
