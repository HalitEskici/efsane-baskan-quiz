# Efsane Başkan — What Kind of Manager Are You?

A five-question personality quiz for Efsane Başkan, a football club management game.

Live: https://haliteskici.github.io/efsane-baskan-quiz/

## Scoring model

Answers are scored on two independent axes rather than tallied:

- **X — Pitch (−) ↔ Boardroom (+)** — winning on the field, or through the club's economy.
- **Y — Patience (−) ↔ Impulse (+)** — the long build, or the immediate move.

Every option carries an `{x, y}` vector with each component between −2 and +2, so over
five questions each axis runs −10..+10. The signs select the quadrant:

|               | Patience                 | Impulse                        |
| ------------- | ------------------------ | ------------------------------ |
| **Pitch**     | TAKTİKÇİ / THE TACTICIAN | KAOS TÜCCARI / THE CHAOS AGENT |
| **Boardroom** | MİMAR / THE ARCHITECT    | PAZARLIKÇI / THE DEALMAKER     |

A result within ±2 of centre on *both* axes returns the fifth persona, EFSANE BAŞKAN /
THE CHAIRMAN, badged as rare. That threshold is one constant, `BALANCED`: at ±2 the
centre covers 24.0% of the 1024 possible answer paths, at ±1 it covers 5.7%.

This is used instead of counting the most-picked letter for two reasons. Contradictory
answers still resolve coherently: two pitch answers and three boardroom answers land on a
specific point, not on whichever letter won the count. And a balanced result becomes
expressible at all — a letter tally has no way to say "no strong lean on either axis".

## Bilingual

Turkish and English at full parity. Every user-facing string lives in one `i18n` object
and the HTML body holds no literal copy. Turkish is the default, the selection is kept in
memory only, and switching re-renders the current screen without losing progress or result.

Persona copy was written natively per language rather than translated, so the two
versions reach the same persona through different images.

Strings are stored already-cased and the stylesheet has no `text-transform`: under
`lang="tr"` that transform corrupts English labels (i → İ), and under `lang="en"` Turkish ones.

## Sharing

- PNG export at 1080×1350, drawn on `<canvas>` in vanilla JS, no html2canvas. It awaits
  `document.fonts.load`/`.ready` first: canvas plays no part in CSS font loading, so
  without that wait Turkish glyphs fall back mid-render.
- Telegram, X and WhatsApp share links, plus copy-link.
- On touch devices exposing `navigator.share`, one native share sheet replaces the three
  network links; download and copy remain.

## Stack

Single `index.html`, vanilla JS, no build step, no dependencies beyond Google Fonts.
Deployed on GitHub Pages.

## Running locally

Open `index.html` in a browser — nothing to install or build.
