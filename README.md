# Games for Nerds

Two daily-style number games sharing one Memphis-Group look. `index.html`
is a landing page that links to each:

- **Bingpot!** (`bingpot.html`) — a target-building game.
- **Number Connections** (`connections.html`) — a grouping/insight game in
  the spirit of NYT Connections, but with numbers.

---

## Bingpot!

A math riff on The New Yorker's [Shuffalo](https://www.newyorker.com/puzzles-and-games-dept/shuffalo),
crossed with Countdown's numbers round and the classroom game Krypto.

### How to play

- Numbers appear as connected wedges of a wheel (Shuffalo-style) with the
  **target** in the center hub. The look is Memphis Group: loud colors,
  chunky outlines, geometric confetti.
- Build an expression that equals the target, using **every number on the
  wheel exactly once**. Operators: `+ − × ÷` and parentheses, reusable as
  often as you like. No fractions, like Countdown: every division must
  come out even, or the expression doesn't count.
- Round 1 starts with 5 numbers. Each solve adds one more number to the
  wheel **and the target climbs** — 101–200 with five numbers, up to
  501–700 with eight — so every round demands a fresh structure instead
  of building off your last solve. The optional 9-number bonus round
  reaches for 701–999. (Five is a gentler opener than four: with the
  use-every-number rule, more numbers means more ways to reach the
  target, so the first round has the most slack.)
- One big number (25, 50, 75, or 100) joins the wheel somewhere from
  round 4 on.
- The running total only appears once every number is placed — work the
  intermediate math yourself (or on the scratch pad).
- After each solve, up to three other known solutions are revealed.
- Shuffle rearranges the wheel; Hint reveals one step of a known solution.
- Click anywhere in your expression to move the caret (arrow keys work
  too) — handy for dropping in a parenthesis without retyping.
- Input however you like: tap the wheel and keypad, or use a physical
  keyboard (digits, `+ - * / ( )`, Backspace, Esc to clear — typed digits
  wait a beat so "1" can become 10/11/12). Tap a used wedge to take that
  number back out of your expression.
- Each number gets its own color when it joins the wheel and keeps it
  all game, so the newcomer is always obvious.
- A collapsible scratch pad evaluates each line you scribble as you
  type (any numbers allowed there — it's scratch paper).
- The timer is off by default — click the ⏱ chip in the status bar to
  play timed (remembered between visits). Time appears in your results
  and share text only when it's on.
- Finish to see a spoiler-free share row — one square per round (green:
  clean solve, yellow: a hint or two, red: leaned on hints; star: bonus
  round) — plus your time.

### Design rules

- Wheel numbers are 2–12, no duplicates; 1 may appear only among the
  opening set (a later 1 would make every round trivially extendable
  via ×1).
- Targets rise with the wheel (101–200 with five numbers, then 201–350,
  351–500, 501–700, bonus 701–999): targets stay far above what the
  numbers can sum to, so rounds require multiplicative structure and the
  moving goal keeps later rounds from being easy extensions of earlier
  ones.
- Every round is guaranteed to have at least one integer-only solution.
  A subset-DP solver (Countdown-style) verifies this during generation:
  it picks a solvable 4-number set, then greedily adds numbers that keep
  the full set solvable for the same target.

---

## Number Connections

NYT Connections, but with numbers. Sixteen numbers hide four groups of
four, each group sharing a number property (multiples of 7, perfect
squares, primes, Fibonacci, …). Select four and submit; four wrong
guesses ends the game.

### How to play

- Tap four numbers you think share a hidden property, then **Submit**.
- A correct group locks in with its category revealed and a colour tier
  (yellow easiest → green → blue → purple trickiest).
- Four mistakes and the game ends, revealing every group. "One away…"
  warns when three of your four belong together.
- Shuffle rearranges the grid; finishing gives a spoiler-free coloured
  share grid (one row of squares per guess), just like Connections.

### Design rules

- Numbers run 2–100. Categories are recognizable in hindsight — the
  "aha" depends on it (multiples of K, squares, cubes, powers of 2,
  Fibonacci, triangular numbers, primes, repdigits).
- The magic is **misdirection**: a number can satisfy several properties
  (64 is a square, a cube, *and* a power of 2; 8 is a cube, a power of 2,
  *and* Fibonacci), so it looks like it belongs to multiple groups.
- Generation guarantees a **unique** solution: it picks four categories,
  fills a 16-number board biased toward overlap traps, then runs an
  exact-cover check and rejects any board with more than one valid way to
  partition it. Boards with too few traps are also rejected, so every
  puzzle has real bait but exactly one answer.

---

## Running

All static — open `index.html` (the landing page) in a browser, or serve
the folder with anything (`python3 -m http.server`). Each game generates
fresh puzzles in the browser for endless replay; an eventual daily mode
would swap the on-the-fly generators for pregenerated dated puzzles.
