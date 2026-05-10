# StateDrivenUi [principle] v0.1.0
The UI is a function of state: `UI = f(state)`. The composable tree describes what the screen looks like for the current state value; it does not imperatively mutate views to reach that state. To change the screen, mutate the state and let Compose re-derive the tree. The agent never holds a reference to a `Button` and calls `setEnabled(false)` on it — instead, `enabled` is a piece of state that the button reads at composition time.
> Treat every screen as a pure projection of a State object onto pixels. Inputs (clicks, text, gestures) update the State; the State drives the projection; the projection is the UI. There is no in-between mutable handle to a view — there are no views, only the latest description of one.
domain: android-compose
