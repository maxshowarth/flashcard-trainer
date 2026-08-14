# 🃏 Flashcard Trainer

A single-file web app for practicing a memory game: a referee shows an
increasingly long sequence of flashcards from a fixed set, and players repeat
the sequence back one card at a time. Last player standing wins. This is your
training ground.

**Live app:** just open `index.html` in any browser — no build step, no server,
no dependencies. (If GitHub Pages is enabled on this repo, it's also served at
`https://maxshowarth.github.io/flashcard-trainer/`.)

## How it works

Each round has three phases that mirror the real game:

1. **Watch** — cards flash one at a time at your configured interval (~1.5s by
   default, like the real game). A brief blank between cards means two identical
   cards in a row are still distinguishable.
2. **Repeat** — click the cards back in the same order. Undo/Clear are
   available, and you can use number keys (`1`–`9`) to pick cards, `Backspace`
   to undo, `Enter` to lock in.
3. **3-2-1 Reveal** — lock in your answer and a countdown reveals your cards
   against the true sequence, one position at a time, marking each ✅/❌. The app
   knows the truth, so scoring is automatic — no self-honesty required.

Get the **whole** sequence right to advance. Miss one card and the game ends.

## Progression modes

- **Grow by 1** (default) — start at a length (e.g. 3) and add one card each
  round you clear. Out on a miss. This is the real-game format.
- **Fixed length** — practice the same length repeatedly.

## Sessions & scoring

A **session** is standalone (per browser session — closing the tab resets it).
A session can contain many games. The **session best** tracks the longest
sequence you've repeated back perfectly. **Reset session** clears it.

## Settings

Everything is tunable in the ⚙ Settings panel:

| Setting | What it does |
|---|---|
| **Card set size** | Number of distinct cards in play (3–20). Fewer cards = more repeats = harder. |
| **Progression** | Grow-by-1 or fixed length. |
| **Starting / fixed length** | Sequence length for round 1 (grow) or every round (fixed). |
| **Reveal interval** | How long each card shows during the sequence (0.5–3s). |
| **Countdown** | The 3-2-1 before your answer is revealed. |
| **Auto-lock when full** | Auto-reveal once you've entered the full length. |

Settings changes mid-game apply to the **next** game.

## Cards

Cards are emoji glyphs (⛵🪣🐴🏠⭐…) drawn from a 20-card pool; the set size
control picks the first *N*. To swap the pool, edit the `POOL` array near the
top of the `<script>` block in `index.html`.

## Tech

Plain HTML/CSS/JS in one file. State persists in `sessionStorage` so a refresh
doesn't wipe your session, but a new browser session starts fresh.
