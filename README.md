# Fraction Cove — Interactive Fraction Game

A browser-based game for practicing fractions, built for the *Interactive Fraction Game Development* assignment (Cove Genius). Players shade wedges of a circular "porthole" to match a target fraction, level by level.

**Live demo:** https://shivam7388.github.io/Interactive-Fraction-Game-Development/

**File:** `index.html` (also saved as `fraction-cove.html`) — self-contained, no install or build step. Double-click to open in any modern browser (Chrome, Safari, Edge, Firefox), or play it instantly at the live link above.

---

## 1. Objective

Teach fraction concepts (numerator, denominator, part-of-a-whole) through a hands-on circular model, with immediate right/wrong feedback and increasing difficulty across levels.

## 2. Core Gameplay

| Requirement | Implementation |
|---|---|
| Fraction Representation | A circle ("porthole") is divided into equal wedges, one per denominator unit. |
| User Interaction | Players shade/unshade wedges with **Add Piece** / **Remove Piece** buttons, or by tapping a wedge directly. |
| Target Fraction | Each of the 8 levels shows a target (e.g. `5/8`) the player must recreate. |
| Feedback Mechanism | Pressing **Check My Answer** gives instant visual + audio feedback: green success message and confetti on a match; red shake and the current (and simplified) fraction on a miss. |

## 3. Interaction Rules

- **Add Piece:** finds the first unshaded wedge (in order) and shades it.
- **Remove Piece:** finds the last shaded wedge and clears it.
- Direct tap on a wedge is allowed only if it's the *next* correct wedge to fill/clear — this keeps the ordering rule intact while feeling responsive.
- Keyboard support: `→` = Add, `←` = Remove, `Enter` = Check.

## 4. Progression

- 8 levels, denominators stepping from 4 up to 12 (`4, 6, 5, 8, 6, 10, 8, 12`).
- Each level generates a random non-trivial target numerator (never 0, never the full circle).
- Score = 10 points + streak bonus per correct answer; streak resets on a miss.
- Progress dots at the bottom of the stage show completed / current / upcoming levels.
- Clearing level 8 shows a "Treasure Found!" end screen with final score and a **Dive Again** button to restart.

## 5. Visual Design

- **Theme:** ocean/treasure-cove, matching the "Cove Genius" name — a brass-rimmed porthole over a gradient deep-sea background with drifting ambient bubbles.
- **Palette:** deep ocean navy/teal background, seafoam/turquoise for filled (shaded) wedges, warm sand for unfilled wedges, coral for the Remove action, brass/gold for the Check action and target fraction text.
- **Type:** Baloo 2 (display/headers, rounded and playful) paired with Nunito (body/UI text).
- **Signature element:** the porthole itself — filled wedges render with a radial "gem" gradient so the fraction circle reads like a glowing treasure dial rather than a flat chart.
- Motion is used sparingly: a small "pop" when a wedge is added, a shake on wrong answers, and confetti on success. All animation respects `prefers-reduced-motion`.

## 6. Sound

All sound effects are generated at runtime with the Web Audio API (oscillator tones) — no external audio files to load or license:

- **Add piece:** short rising two-tone chime
- **Remove piece:** short falling two-tone chime
- **Correct:** ascending four-note major arpeggio
- **Incorrect:** low buzz
- **Level up:** quick ascending square-wave sequence

A mute toggle (🔊/🔇) sits in the top-right of the HUD.

## 7. Technical Notes

- Pure HTML/CSS/JS, SVG for the pie chart — no external libraries or frameworks, so it loads instantly and runs smoothly on low-end devices and mobile.
- Fully responsive layout (porthole and controls scale down for mobile widths).
- Keyboard-accessible controls with visible focus states.
- Score, streak, and level state are held in memory only (no login/save system) — a full session is a few minutes, matching classroom/practice use.

## 8. Possible Extensions

- Difficulty settings (timed mode, fewer allowed mistakes).
- A denominator-comparison mode (e.g. reduce `6/8` and confirm it equals `3/4`).
- Persistent high scores via local storage or a backend.
- Additional wedge "skins" (pizza, pie, compass) as a cosmetic unlock system.

---

## Deliverables Mapping

| Assignment Deliverable | Where it is |
|---|---|
| Functional game | `fraction-cove.html` |
| Well-commented, organized code | Inline comments in the `<script>` block of `fraction-cove.html`; logic is separated into level generation, SVG rendering, gameplay actions, audio, and UI wiring. |
| Design document (mechanics, visuals, UX) | This README. |
