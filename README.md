# PCB Line — 제조 공정 흐름도 / Interactive Process Flow Map

An interactive, bilingual (한국어 / English) map of the PCB plant. The building
layout — 3F, 2F, 1F, plus the outsourced surface-finish partner — sits at the
top; the 17-step process sequence is listed below. Stepping through the
sequence lights up the current room and draws the panel's transfer route as a
copper trace, with via dots marking floor-to-floor moves.

## How to use

Open `index.html` in any browser — no server or install needed.

- **◀ 이전 / 다음 ▶** or the **← → arrow keys** step through the process
- **자동 재생 AUTO** plays the whole route automatically
- **Click any room** on the map to jump to its next step in the sequence
- **Click any step** in the list to jump there
- **한국어 / 둘 다 / EN** switches the language of the step list
- **인쇄 PRINT** produces a clean A4 printout (both languages, no controls)

## How to edit the content

Everything lives in `index.html`:

- **`STEPS`** (top of the `<script>`) — the process sequence. Each step has a
  number `n`, the room(s) it happens in, Korean/English titles (`ko`/`en`),
  location labels (`lk`/`le`), bullet lists (`k`/`e`), and the transfer note to
  the next step (`mk`/`me`).
- **Room buttons** (in the `.map` markup) — one `<button class="rm">` per room,
  placed on a 12-column grid per floor. `data-room` is the id `STEPS` refers to.
- **`FLOOR`** — maps each room id to its floor row (0 = top row), used to draw
  the transfer traces and via dots between floors.
