# PredictiveBack [pattern] v0.1.0
On Android 13+ predictive back lets users peek at the destination during the back-gesture: as the user drags from the screen edge, the OS shows a preview of where they'll land. If the app intercepts back via the legacy `OnBackPressedCallback` synchronously, the gesture loses its preview animation. Use `PredictiveBackHandler` (compose-foundation 1.7+) or Compose Navigation's built-in support — both wire into the gesture progress so screen content can animate as the user drags.
domain: android-compose

## Label
Implement predictive-back via PredictiveBackHandler / Compose Navigation

## Problem
An app uses `BackHandler { closeBottomSheet() }` to dismiss a sheet on back press. With predictive back, the user expects to see the underlying screen during the drag — but the app intercepts before the OS can preview, so the gesture flickers or freezes. Worse, on the user's release, the sheet may dismiss but no transition was shown.

## Solution
```
    Use the predictive variant which gives a Flow of gesture progress:

      PredictiveBackHandler(enabled = isOpen) { progress: Flow<BackEventCompat> ->
        try {
          progress.collect { event ->
            // event.progress  : 0f..1f drag progress
            // event.swipeEdge : LEFT or RIGHT
            sheetOffset.snapTo(event.progress)
          }
          // user committed — finish the dismiss
          onDismiss()
        } catch (_: CancellationException) {
          // user cancelled — animate back to fully open
          sheetOffset.animateTo(0f)
        }
      }

    For Compose Navigation (Nav3 / Nav-Compose 2.8+) predictive back is
    handled automatically for the standard NavHost transitions; opt in
    by setting `enablePredictiveBack = true` in the Activity and using
    the default forward/back animations.
  
```

## Label
Implement predictive-back via PredictiveBackHandler / Compose Navigation

## Problem
An app uses `BackHandler { closeBottomSheet() }` to dismiss a sheet on back press. With predictive back, the user expects to see the underlying screen during the drag — but the app intercepts before the OS can preview, so the gesture flickers or freezes. Worse, on the user's release, the sheet may dismiss but no transition was shown.

## Solution
```
    Use the predictive variant which gives a Flow of gesture progress:

      PredictiveBackHandler(enabled = isOpen) { progress: Flow<BackEventCompat> ->
        try {
          progress.collect { event ->
            // event.progress  : 0f..1f drag progress
            // event.swipeEdge : LEFT or RIGHT
            sheetOffset.snapTo(event.progress)
          }
          // user committed — finish the dismiss
          onDismiss()
        } catch (_: CancellationException) {
          // user cancelled — animate back to fully open
          sheetOffset.animateTo(0f)
        }
      }

    For Compose Navigation (Nav3 / Nav-Compose 2.8+) predictive back is
    handled automatically for the standard NavHost transitions; opt in
    by setting `enablePredictiveBack = true` in the Activity and using
    the default forward/back animations.
  
```
