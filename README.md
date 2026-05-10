# @android-compose — Jetpack Compose + Material 3, atom-shaped

> 21 typed Prime atoms distilled from the AndroidX Jetpack Compose API
> guidelines and Material 3 design tokens — the conventions an Android
> Compose codebase must respect before component-by-component review is
> meaningful.

This is a **starter seed corpus** for the Skill Wiki marketplace. It gives
an AI coding agent a small, audited reference set covering Compose
component-API shape, Material 3 tokens, accessibility, and adaptive
layout patterns.

The corpus answers a recurring question for AI agents writing Android
UI: *what are the rules my Compose code has to follow before an Android
engineer would call it idiomatic?* The answer is no longer "read these
three guideline documents and grep the Material 3 docs" — it is "load
this Prime, follow the rules, avoid the anti-pattern."

---

## What's in the box

21 atoms across five concerns.

| Category | Atoms | Kinds |
|---|---|---|
| Compose component API | 9 | rule x 7, anti-pattern x 1, (incl. modifier, slot, state hoisting, lazy keys, side effects) |
| Material 3 tokens | 4 | rule x 4 (color roles, typography, elevation, motion) |
| Accessibility | 3 | rule x 3 (touch target, content description, semantics) |
| Layout patterns | 3 | pattern x 3 (WindowSizeClass, edge-to-edge, predictive back) |
| Principles | 2 | principle x 2 (state-driven UI, recomposition as source of truth) |
| **Total** | **21** | — |

Each atom carries source attribution to a specific AndroidX or Material
3 document at the top of the `.prime` file.

---

## License

This Prime is dual-attributed under permissive licenses:

| Layer | License |
|---|---|
| **Code** (pack.yaml, domain.yaml, build glue, packaging) | Apache-2.0 |
| **Atom content derived from AndroidX Compose docs / source** | Apache-2.0 |
| **Atom content derived from Material 3 m3.material.io** | CC-BY 4.0 |
| **Compiled outputs** (`compiled/`) | Apache-2.0, with attribution headers preserved |

Each `.prime` file links the specific document or source location it
summarises. The compiled output keeps attribution intact.

If you adapt or extend the corpus, you must:

1. Keep the per-file `// Source: …` attribution headers.
2. Note your changes near the original attribution.
3. Carry both upstream licenses forward (Apache-2.0 + CC-BY 4.0).

See `LICENSE` for the full text and attribution table.

---

## How to compile

The corpus is checked-in pre-compiled (`compiled/_index.xml` + per-atom
directories). To rebuild from sources:

```bash
# from the repo root
bun ../prime-system/scripts/build-atom-dirs.ts \
  --src primes/sources \
  --out compiled
```

The build script lives in the
[`prime-system`](https://github.com/skill-wiki/prime-system) repo. Clone
both side-by-side, or vendor the script in if you prefer.

---

## How to install

### As an MCP server in Claude Code

```json
{
  "mcpServers": {
    "android-compose": {
      "command": "bunx",
      "args": ["@prime-lang/mcp-server-core"],
      "env": {
        "PRIME_DIR": "/abs/path/to/skill-corpus-android-compose/compiled"
      }
    }
  }
}
```

The agent now sees a 21-atom Android Compose index on every turn. It
pulls the relevant atoms when the task touches a Compose concern —
component shape, state, theming, accessibility — and ignores them
otherwise.

### From the marketplace

After this Prime is registered in
[`skill-wiki/website`](https://github.com/skill-wiki/website)'s
`data/skills.yaml`, it will appear on the public marketplace.

---

## Reading order

If you're learning the corpus from scratch:

1. **`principle-state-driven-ui`** + **`principle-recomposition-as-source-of-truth`**
   — the root mental model every other atom follows from.
2. **`rule-composable-annotation-not-raw-fn`** + **`rule-hoist-state-up`**
   + **`rule-single-source-of-truth`** — the function-shape and state
   triple that makes every Compose codebase comprehensible.
3. **`rule-modifier-as-first-optional-param`** + **`rule-slot-content-via-composable-lambda`**
   — the API conventions that make components composable in the
   English-language sense, not just the Compose sense.
4. **`rule-no-side-effects-in-composables`** +
   **`anti-pattern-side-effects-in-composables`** — the discipline
   recomposition demands.
5. **Material 3 token rules** — colour, typography, elevation, motion;
   these are the contracts a brand theme can swap without rewriting
   screens.
6. **Accessibility rules** — touch target, content description,
   semantics; non-negotiable.
7. **Layout patterns** — WindowSizeClass, edge-to-edge, predictive
   back; the modern Android surface contract.

---

## Contributing

This is a seed set. The full Compose and Material 3 surface has hundreds
of atom-shaped facts; we picked 21 because that's the smallest set that
demonstrates the model and is useful by itself.

Good additions:

- More **anti-patterns** mirroring the existing rules — modifier
  ordering, hoisting violations, hex colors, missing keys.
- More **patterns** — Scaffold layout, BottomSheet, NavHost graph
  shape, Pager, dialog handling.
- More **kinds** — `value` atoms for the actual M3 token tables,
  `check` atoms for ui-test assertions, `persona` for an Android
  reviewer.
- **Tradeoffs** — Compose-vs-Views interop, dynamic-color-vs-brand,
  performance-vs-readability tensions worth surfacing explicitly.

Open a PR. Keep:

- Atoms terse — atom-shaped, not paraphrased prose.
- One `.prime` file per atom.
- The `// Source: …` header pointing to the originating document.
- Edges (`requires` / `enhances` / `contradicts` / `related`) where the
  relationship is real, not for decoration.
- A passing `bun ../prime-system/scripts/build-atom-dirs.ts ...` run.

---

## Provenance

- **Knowledge sources:**
  - AndroidX Jetpack Compose — Apache-2.0,
    https://github.com/androidx/androidx (compose/docs and material3 modules)
  - Material 3 — CC-BY 4.0, https://m3.material.io/
- **Atom packaging:** Skill Wiki contributors, Apache-2.0
- **Distillation:** the prose in each atom is heavily compressed and
  re-shaped from the originals; this is permitted by both upstream
  licenses provided attribution is kept, but the substance is the work
  of the AndroidX and Material teams.
