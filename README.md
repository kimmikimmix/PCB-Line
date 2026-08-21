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
- **`DETAILS`** — optional detail pages, keyed by step number (e.g. `"02"`)
  or by name for standalone reference pages (e.g. `"mat"`, reached by link).
  Any step with an entry automatically gets a "상세 페이지 DETAIL PAGE →"
  button that opens a full-screen page (link `#d/02`, back button and Escape
  to return). Each page is a list of sections with bilingual headings
  (`hko`/`hen`); a section may carry paired Korean/English rows (`k`/`e`),
  paragraphs (`pko`/`pen`), a table (`table: {head, rows, nw}` — `nw` lists
  column indexes kept on one line) and a footnote (`nko`/`nen`). Table cells
  are plain strings or `{k, e}` pairs that follow the language toggle. Pages
  can also declare `eyebrow`, a lede (`lko`/`len`) and cross-`links`.
- **`MAT`** — the CCL materials master chart (87 rows) shown on the
  `#d/mat` reference guide, which is linked from the step 02 detail page.
  Dk/Df values are typical published figures near 10 GHz; rows flagged in
  the guide's section 7 still need internal confirmation.
