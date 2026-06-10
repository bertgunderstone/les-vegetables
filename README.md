# Bingpot!

A math riff on The New Yorker's [Shuffalo](https://www.newyorker.com/puzzles-and-games-dept/shuffalo),
crossed with Countdown's numbers round and the classroom game Krypto.

## How to play

- Numbers appear as connected wedges of a wheel (Shuffalo-style) with the
  **target** in the center hub. The look is Memphis Group: loud colors,
  chunky outlines, geometric confetti.
- Build an expression that equals the target, using **every number on the
  wheel exactly once**. Operators: `+ − × ÷` and parentheses, reusable as
  often as you like. Fractions mid-expression are allowed — only the final
  value has to match.
- Round 1 starts with 4 numbers. Each solve adds one more number to the
  wheel **and the target climbs** — two digits with four numbers, up to
  501–700 with eight — so every round demands a fresh structure instead
  of building off your last solve. The optional 9-number bonus round
  reaches for 701–999.
- Shuffle rearranges the wheel; Hint reveals one step of a known solution.
- Input however you like: tap the wheel and keypad, or use a physical
  keyboard (digits, `+ - * / ( )`, Backspace, Esc to clear — typed digits
  wait a beat so "1" can become 10/11/12). Tap a used wedge to take that
  number back out of your expression.
- Each number gets its own color when it joins the wheel and keeps it
  all game, so the newcomer is always obvious.
- A collapsible scratch pad evaluates each line you scribble as you
  type (any numbers allowed there — it's scratch paper).
- Finish to see a spoiler-free share row — one square per round (green:
  clean solve, yellow: a hint or two, red: leaned on hints; star: bonus
  round) — plus your time.

## Design rules

- Wheel numbers are 2–12, no duplicates; 1 may appear only among the
  initial four (a later 1 would make every round trivially extendable
  via ×1).
- Targets rise with the wheel (13–99 with four numbers, then 101–200,
  201–350, 351–500, 501–700, bonus 701–999): a gentle on-ramp, after
  which targets stay far above what the numbers can sum to, so rounds
  require multiplicative structure and the moving goal keeps later
  rounds from being easy extensions of earlier ones.
- Every round is guaranteed to have at least one integer-only solution.
  A subset-DP solver (Countdown-style) verifies this during generation:
  it picks a solvable 4-number set, then greedily adds numbers that keep
  the full set solvable for the same target.

## Running

It's a single static page — open `index.html` in a browser, or serve it
with anything (`python3 -m http.server`). Each "New game" generates a
fresh puzzle in the browser; the eventual daily-puzzle mode would swap
the on-the-fly generator for a pregenerated dated puzzle file.
