# ColorRolesNotRawHex [rule] v0.1.0
Material 3 defines 30+ semantic color *roles* — `primary`, `onPrimary`, `surface`, `onSurfaceVariant`, `error`, `outline`, etc. — exposed in Compose as `MaterialTheme.colorScheme.<role>`. Components and screens reference roles. The role-to-hex mapping lives in the theme and changes between light/dark, dynamic-color (Material You), high-contrast, and per-app brand schemes. Hard-coding a hex value bypasses every one of those swaps and breaks the moment a user toggles dark mode or dynamic color.
domain: android-compose

## Checks
- [ ] All `Color(0xFF...)` and `Color.Red`-style literals in app code are replaced with `MaterialTheme.colorScheme.<role>`.
- [ ] Backgrounds use `surface`, `surfaceVariant`, or `surfaceContainer*`; foreground content on top uses the matching `onSurface*` role.
- [ ] Tinted brand actions use `primary` for the action and `onPrimary` for content drawn on it; never invert this pair manually.
- [ ] Errors use `error` + `onError`; warnings/info derive from `tertiary`/`secondary` rather than ad-hoc orange/blue.
- [ ] Dynamic color (Material You) is enabled on Android 12+ via `dynamicLightColorScheme` / `dynamicDarkColorScheme` so user wallpaper colors flow through.

## Label
Reference Material 3 color roles, never raw hex literals

## Label
Reference Material 3 color roles, never raw hex literals
