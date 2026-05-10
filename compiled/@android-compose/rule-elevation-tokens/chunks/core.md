# ElevationTokens [rule] v0.1.0
Material 3 elevation is expressed via six tokens — `level0` (0dp) through `level5` (12dp) — that map to BOTH a shadow elevation and a tonal-color overlay drawn on top of `surface`. Higher elevations get a stronger primary-tinted overlay, which is how dark mode shows depth without bright shadows. Always pass elevation through Compose Material 3 component params (`elevation = CardDefaults.cardElevation(...)`) or use `Surface(tonalElevation = N.dp, shadowElevation = N.dp)` — never fake depth with `Modifier.shadow(...)` alone, which won't tint the surface and will look wrong in dark mode.
domain: android-compose

## Checks
- [ ] Cards: `Card(elevation = CardDefaults.cardElevation(defaultElevation = 1.dp, ...))` — ship with `level1` resting elevation.
- [ ] Top app bars: `TopAppBar(colors = ..., scrollBehavior = ...)` — let the component swap to `level2` on scroll.
- [ ] FABs: `FloatingActionButton(elevation = FloatingActionButtonDefaults.elevation())` — defaults are `level3` resting / `level4` pressed.
- [ ] Custom containers: `Surface(tonalElevation = 3.dp, shadowElevation = 3.dp)` — keep the two values equal unless you have a specific reason to diverge.
- [ ] Do not stack `Modifier.shadow(8.dp)` on a Material container; it doubles the shadow and skips tonal overlay.

## Label
Use Material 3 elevation tokens; M3 elevates with surface tone, not shadows alone
