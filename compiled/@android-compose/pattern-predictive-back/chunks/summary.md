# PredictiveBack [pattern] v0.1.0
On Android 13+ predictive back lets users peek at the destination during the back-gesture: as the user drags from the screen edge, the OS shows a preview of where they'll land. If the app intercepts back via the legacy `OnBackPressedCallback` synchronously, the gesture loses its preview animation. Use `PredictiveBackHandler` (compose-foundation 1.7+) or Compose Navigation's built-in support — both wire into the gesture progress so screen content can animate as the user drags.
domain: android-compose
