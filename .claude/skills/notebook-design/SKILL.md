---
name: notebook-design
description: Use when adding or changing any page in agentic-ai-beginner. It keeps the hand-written notebook look (ruled paper, sticky notes, highlighter, doodles), with no 3D, web fonts or CDN scripts.
---

# Notebook design for agentic-ai-beginner

Every page in this repo looks like one sheet of a hand-written notebook lying on a desk. The readers are engineers meeting agents for the first time. Write in a friendly, step-by-step voice: one idea at a time, a concrete running example, and lots of "try this". `STYLES.md` has the full token and component reference. This skill covers how to apply it.

## Hard rules

- **No 3D, WebGL, canvas animation, Three.js or importmaps.** The field-manual sites use those; they don't match this look. To show a flow over time, use a step-by-step sticky-note row (`ol.walk`, below) or a hand-drawn `svg.doodle`.
- **No web fonts and no CDN scripts or styles.** Pages must work offline from a single file. Use only the system handwriting stacks: `--hand`, `--title` and `--mono`.
- **No links to other DevLCodes sites.** Each page stands alone. Link only to pages in this repo and to primary external sources (docs, papers, specs).
- **Inline everything.** Each page carries its own `<style>` and `<script>`. There is no build step and no shared asset folder.
- **Don't add the grey field-manual palette, numbered TOC rails, dense numeric tables or diagram layer colours.** If a topic needs that depth, simplify it for this audience. Don't import the other look.

## Starting a new page

1. Copy `agentic-loop.html` and keep its whole `<style>` block: the `:root` tokens, `.page`, ruled lines, punched holes and margin. Don't retype tokens from memory.
2. Set the `<title>` and `<meta name="description">`. Set `og:url` to `https://devlcodes.github.io/agentic-ai-beginner/<page>.html` and `og:image` to `https://devlcodes.github.io/agentic-ai-beginner/og-image.png`.
3. Structure the page: a header with the topic title in `--title`, then numbered `h2` parts (`1 · …`, `2 · …`), each introduced by a one-line `.lede`. Use a red uppercase `.part` label when the page has several parts.
4. Add at least one hands-on element: a clickable `svg.doodle` diagram, a small lab with buttons and an `.out` panel, or a step-through.
5. End with the sticky-note quiz (`.cards`), with options, right and wrong colouring, and a `.why` reveal.
6. Add the page to the roadmap in `index.html` (the `T` array that draws the ring, or the numbered `ol.topic-list` for the retrieval and model track) and to the README topic list.

## Components to reach for

| Need | Component |
| --- | --- |
| Key takeaway | `.sticky` (`.pink`, `.blue` or `.mint`), slightly rotated with a tape strip |
| Aside or definition | `.box` with the wobbly `border-radius: 255px 15px 225px 15px / 15px 225px 15px 255px` |
| The one line to remember | `<span class="hl">` highlighter |
| Diagram | `svg.doodle`: round line caps, `--ink` strokes, `--tan` fills, handwriting labels |
| A flow over time (one run, step by step) | `ol.walk`: numbered sticky notes, one per step, introduced by `<h3>Step by step: …</h3>` and a one-sentence summary |
| Lab output | `.out` with `.good` or `.bad` |
| Small table | `table.hand` with dashed rows; keep it short |
| Check understanding | `.cards` quiz at the end |

`ol.walk` markup:

```html
<h3>Step by step: one run of the loop</h3>
<p>One-sentence summary of the whole flow.</p>
<ol class="walk">
  <li>Perceive: what arrives and who builds the request.</li>
  <li>Reason: what the model decides and returns.</li>
  <!-- 5 to 7 steps; each says what happens and who does it -->
</ol>
```

The `.walk` CSS is already inlined in every concept page. Copy it from any of them.

## Before you commit

- Check it at 390px and 1280px wide: no horizontal scroll, and a 16px side gutter on phones. Wide doodles need a `viewBox` and `width: 100%`.
- Check there are no console errors and no requests to any CDN.
- Run `grep -n "three@\|importmap\|fonts.googleapis\|agentic-ai-notebook" *.html`. It should find nothing.
- Respect `prefers-reduced-motion`: drop rotations and transitions.
