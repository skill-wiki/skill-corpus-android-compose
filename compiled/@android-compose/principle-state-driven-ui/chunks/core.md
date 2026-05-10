# StateDrivenUi [principle] v0.1.0
The UI is a function of state: `UI = f(state)`. The composable tree describes what the screen looks like for the current state value; it does not imperatively mutate views to reach that state. To change the screen, mutate the state and let Compose re-derive the tree. The agent never holds a reference to a `Button` and calls `setEnabled(false)` on it — instead, `enabled` is a piece of state that the button reads at composition time.
> Treat every screen as a pure projection of a State object onto pixels. Inputs (clicks, text, gestures) update the State; the State drives the projection; the projection is the UI. There is no in-between mutable handle to a view — there are no views, only the latest description of one.
domain: android-compose

## Applies To
- All screen-level composables — they receive a state object (often a ViewModel-exposed `StateFlow` collected as state) and emit UI as a function of it.
- All component composables — they take parameters (read-only state) and callbacks (event-up); they do not own state they could have hoisted.
- All animations — drive by `animateXAsState(targetValue = state.x)`; do not hand-tune frame-by-frame mutations.
- All form inputs — `TextField(value = state.email, onValueChange = ...)`; the field DISPLAYS the state, it does not own it.
