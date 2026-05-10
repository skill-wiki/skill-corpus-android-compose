# RecompositionAsSourceOfTruth [principle] v0.1.0
Recomposition is the runtime mechanism that keeps the UI consistent with state. When a snapshot read inside a composable changes, the runtime invalidates that scope and re-runs it. Recomposition can happen at any time, in any order, often, and may be cancelled mid-way. Code that assumes a composable runs 'once' or 'exactly when the user pressed the button' is wrong; the only contract is 'the body returns the latest projection of inputs to UI'.
> Recomposition is the source of truth, not the developer's intuitions about call frequency. Design every composable so that running it 1 time, 100 times, or being aborted at line 7 all produce identical user-visible behaviour. Side effects, expensive allocations, and impure operations belong outside the composition path (effect APIs, `remember`, ViewModel).
domain: android-compose

## Applies To
- Frequency: assume a composable body runs hundreds of times per user interaction during animations or when typing in a TextField it observes.
- Order: assume sibling composables run in arbitrary order; do NOT use one's body to set up state another reads.
- Cancellation: assume a composition can be aborted; never observe partial work.
- Stability: types Compose can compare with `==` skip recomposition when inputs are equal — annotate state holders `@Stable` / `@Immutable` to enable that skipping.
- Reading: only state read inside a composable causes its recomposition; don't 'optimise' by passing state through plain references that bypass snapshots.
