# Style guide: the notebook

Every page in this repo uses one look: a hand-written notebook on a desk. It's for engineers learning agents for the first time, so the voice is friendly and step by step, one idea at a time, with lots of "try this".

Deeper, numbers-heavy material lives elsewhere in a different (field-manual) style:
- Agentic system designs: https://devlcodes.github.io/agentic-ai-notebook/system-design/
- Classic system design: https://github.com/DevLCodes/classic-system-designs

Link out to those freely ("go deeper"), but don't borrow their components.

| | |
| --- | --- |
| Feel | Ruled paper, sticky notes, highlighter, doodles |
| Fonts | System handwriting only, so it works offline: `--hand` (Noteworthy, Bradley Hand, Segoe Print…), `--title` (Marker Felt, Chalkboard SE…), `--mono` (Courier New) |
| Base size | 19px body on a 30px ruled line (`--lh`) |

## Details

**Tokens** (copy the `:root` block from `agentic-loop.html`; don't invent new colours):
`--desk #e9edf2` (dotted desk background), `--paper #fdfbf3`, `--rule #c9dcef` (ruled lines), `--margin #e8a0a0` (red margin line), `--ink #1f3a93` (headings, strokes), `--pencil #555` (muted), `--red #c0392b`, `--green #1e8449`, `--hl #ffe066` (highlighter), stickies `--sticky #fff59d`, `--pink #ffd1dc`, `--blue #cdeafe`, `--mint #c8f0d8`, `--tan #fbe6a2`.

**Layout**: one `.page` sheet (max 1040px) with punched holes and a margin line, text sitting on the ruled lines. `h2` gets a tilted highlighter stroke behind it. Parts are introduced with a red uppercase `.part` label.

**Components**
- `.sticky` (and `.pink` / `.blue` / `.mint`): key takeaways, slightly rotated, with a tape strip.
- `.box`: hand-drawn bordered aside (the wobbly `border-radius: 255px 15px 225px 15px / 15px 225px 15px 255px`).
- `svg.doodle`: diagrams drawn as if by hand: round line caps, `--ink` strokes, `--tan` fills, handwriting labels.
- Buttons share the wobbly border and turn highlighter-yellow on hover. Focus is a dashed red outline.
- `.out` (`.good` / `.bad`): lab output panels. `table.hand`: dashed rows.
- `.cards` quiz: sticky-note cards with option buttons, right/wrong colouring, and a `.why` reveal. Every concept page ends with one.
- Progress lives on the roadmap (`index.html`) in `localStorage`.

- `.fig3d`: a few concept pages embed a 3D scene via `assets/scene3d.js` + `assets/scene3d.css` (three@0.160.0 importmap). The field-manual palette is scoped to `.fig3d` so it never leaks into the notebook. Use it sparingly, for one mechanism a flat doodle can't show.

**Don't**: load web fonts, use the grey palette outside `.fig3d`, or write long tables of numbers. If a section needs that depth, it belongs on the [agentic system design site](https://devlcodes.github.io/agentic-ai-notebook/system-design/), with a link from the concept page.

## Checklist for a new page
1. Copy the `:root` tokens and base CSS from `agentic-loop.html`, not from memory.
2. End with a sticky-note quiz.
3. Add the page to the roadmap in `index.html` and to the README topic list.
4. Check it at 390px wide: no horizontal scroll, 16px side gutter.
