# Calm (Low Stimulation) theme

LightCraft had one hard-coded look. It now has two, chosen from **View › Interface Theme** or
with `view.theme {"theme":"calm"}`. The choice persists in the library's `prefs.json` as
`theme: "calm"`.

## Why it exists

The reference look is tuned for photo judgement: near-black surfaces so the image carries all the
contrast, a saturated blue accent, 22 px rows, 0.08 s animation. Calm keeps the dark surround that
photo work needs but takes out the signal that costs attention — for ADHD and autistic users in
particular.

## What it changes

| | Dark | Calm |
|---|---|---|
| Chrome / canvas | neutral `#2d2d2d` / `#1c1c1c` | warm `#242422` / `#1a1a19` |
| Accent | saturated blue `#0165dd` | one soft blue `#85b7eb` |
| Mask overlay | alarm red `#e02030` | the accent, at lower alpha |
| Star | near-white | amber `#e0a94a`, so rating reads without counting |
| Row height | 22 px | 26 px |
| Animation | 0.08 s | 0.14 s |

Only `reject` and `caution` keep a hue of their own. Both are paired with a glyph elsewhere in
the UI — **colour is never the sole carrier of meaning**, which is the rule this theme is built
around.

## What this added to the codebase

`ThemeKind` did not exist here before. It does now (`crates/ui-egui/src/theme.rs`), with
`Tokens::for_kind`, an `apply(ctx, kind)` that used to take no argument, a `theme` field on
`Session` persisted through `prefs.json`, and a View-menu submenu. `Tokens::default()` is still
the Dark set, so nothing that read it changed behaviour.

## Where the values come from

The surface, text and accent tokens are the dark half of the INT Digital design system
(warm-neutral greys with a faint warm bias, one semantic accent, a dark theme designed in its own
right rather than inverted from the light one).
