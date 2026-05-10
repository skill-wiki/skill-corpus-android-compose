# MotionEasingTokens [rule] v0.1.0
Material 3 motion is built on a small set of named easing curves and duration tokens — `MotionTokens.EasingEmphasizedCubicBezier`, `EasingStandardCubicBezier`, durations `Short1` (50 ms) through `ExtraLong4` (1000 ms). Two curves cover most cases: *emphasised* (defaults for outgoing/incoming UI elements; expressive accel/decel) and *standard* (small reversible state changes). Picking custom cubic-bezier values per animation creates inconsistency; using the OS Animator default (`FastOutSlowIn`) ignores M3 expressiveness.
domain: android-compose
