# PCB Line — Interactive Facility Map

An interactive HTML map of a PCB manufacturing facility. The floor plan is at
the top; clicking a room shows the process and steps that happen there, and the
copper arrows show the route material takes through the line.

## How to use

Open `index.html` in any browser — no server or install needed. Everything
(map, styling, data) lives in that single file.

## How to put in your own rooms, steps, and routes

Open `index.html` and find the block near the top of the `<script>` marked
**EDIT YOUR DATA HERE**. There are three things to edit:

1. **`FACILITY`** — the page title and subtitle.
2. **`ROOMS`** — one entry per room. Each has:
   - `id` — a short unique name used to reference the room in the route
   - `x`, `y`, `w`, `h` — position and size on the map (the map canvas is
     1000 wide × 560 tall)
   - `name` — the label shown on the map
   - `summary` — one-sentence description shown in the panel
   - `steps` — the list of process steps shown when the room is clicked
3. **`ROUTE`** — the order material flows through the rooms, as a list of room
   ids. The numbered badges and the arrows between rooms are drawn
   automatically from this list, so changing the route is just reordering ids.

A room that is *not* in `ROUTE` (e.g. a QC lab or warehouse) still shows on the
map and is still clickable — it just has no stage number or arrows.

The current contents are placeholder data for a typical PCB line — replace them
with your real layout and process notes.
