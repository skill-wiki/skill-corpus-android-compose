# MotionEasingTokens [rule] v0.1.0
Material 3 motion is built on a small set of named easing curves and duration tokens — `MotionTokens.EasingEmphasizedCubicBezier`, `EasingStandardCubicBezier`, durations `Short1` (50 ms) through `ExtraLong4` (1000 ms). Two curves cover most cases: *emphasised* (defaults for outgoing/incoming UI elements; expressive accel/decel) and *standard* (small reversible state changes). Picking custom cubic-bezier values per animation creates inconsistency; using the OS Animator default (`FastOutSlowIn`) ignores M3 expressiveness.
domain: android-compose

## Checks
- [ ] `animateColorAsState`, `animateDpAsState`, `updateTransition` use M3 easing: `tween(durationMillis = 300, easing = MotionTokens.EasingEmphasizedCubicBezier)` (or read from the `MotionScheme` in compose-material3 1.3+).
- [ ] Page transitions and list-reorder animations use the *emphasised* family (longer durations, expressive curve).
- [ ] Small reversible flips (checkbox tick, switch thumb, ripple) use the *standard* family (Short2/Short4 durations).
- [ ] Custom cubic-beziers are reserved for brand signature motion only and live behind a named token in your theme — not inline in 30 places.
- [ ] Reduced-motion settings are honoured: gate decorative animations behind `LocalAccessibilityManager.current` or the OS animation-scale read.

## Label
Use Material 3 easing/duration tokens (emphasised, standard, legacy)

## Label
Use Material 3 easing/duration tokens (emphasised, standard, legacy)
