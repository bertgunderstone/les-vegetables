# Numbuffalo

A math riff on The New Yorker's [Shuffalo](https://www.newyorker.com/puzzles-and-games-dept/shuffalo),
crossed with Countdown's numbers round and the classroom game Krypto.

## How to play

- Numbers appear on a wheel with a **target** in the middle.
- Build an expression that equals the target, using **every number on the
  wheel exactly once**. Operators: `+ − × ÷` and parentheses, reusable as
  often as you like. Fractions mid-expression are allowed — only the final
  value has to match.
- Round 1 starts with 4 numbers. Each solve adds one more number to the
  wheel — the target never changes — up through 8 numbers, with an optional
  9-number bonus round.
- Shuffle rearranges the wheel; Hint reveals one step of a known solution.
- Finish to see your time and hint count, with copyable share text.

## Design rules

- Wheel numbers are 2–12, no duplicates; 1 may appear only among the
  initial four (a later 1 would make every round trivially extendable
  via ×1).
- Targets are three-digit (101–500): small numbers can't reach them by
  addition alone, so every round requires multiplicative structure.
- Every round is guaranteed to have at least one integer-only solution.
  A subset-DP solver (Countdown-style) verifies this during generation:
  it picks a solvable 4-number set, then greedily adds numbers that keep
  the full set solvable for the same target.

## Running

It's a single static page — open `index.html` in a browser, or serve it
with anything (`python3 -m http.server`). Each "New game" generates a
fresh puzzle in the browser; the eventual daily-puzzle mode would swap
the on-the-fly generator for a pregenerated dated puzzle file.
