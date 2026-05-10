# ColorRolesNotRawHex [rule] v0.1.0
Material 3 defines 30+ semantic color *roles* — `primary`, `onPrimary`, `surface`, `onSurfaceVariant`, `error`, `outline`, etc. — exposed in Compose as `MaterialTheme.colorScheme.<role>`. Components and screens reference roles. The role-to-hex mapping lives in the theme and changes between light/dark, dynamic-color (Material You), high-contrast, and per-app brand schemes. Hard-coding a hex value bypasses every one of those swaps and breaks the moment a user toggles dark mode or dynamic color.
domain: android-compose
