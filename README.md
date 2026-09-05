# The Five Biggest AI Transformation Traps: Do This, Not That

A one-hour talk by Jim Moore, built with [Slidev](https://sli.dev).

**Slides:** https://jdigger.github.io/five-ai-transformation-traps/

Speaker notes are part of the deck and carry the argument; the slides themselves stay
sparse. Read them at
[`/#/notes`](https://jdigger.github.io/five-ai-transformation-traps/#/notes) or in
[`slides.md`](./slides.md), where each note opens with a `~M:SS` timing cue followed by the
spoken script.

## Run it locally

```bash
npm install
npm run dev      # http://localhost:3030
```

`http://localhost:3030/notes` is the full-width notes view for the lectern — use that rather
than `/presenter/`, which gives the notes only a small corner. `/presenter/` is still the
right view for slide + next + timer together.

Jump to a slide with its reveals fired: `http://localhost:3030/12?clicks=1`.

```bash
npm run build    # confirms the deck compiles
```

## Deploying

Pushing to `main` builds and publishes to GitHub Pages via
[`.github/workflows/pages.yml`](./.github/workflows/pages.yml).

## Layout

| Path | What it is |
|---|---|
| [`slides.md`](./slides.md) | The deck, and the speaker notes with it |
| [`styles/index.css`](./styles/index.css) | The visual language — colors are semantic; read the header comment |
| `public/` | Illustrations and portraits |
