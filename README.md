# The Five Biggest AI Transformation Traps

Slides for the talk *"The Five Biggest AI Transformation Traps"*, built with
[Slidev](https://sli.dev).

## Working on the talk

| File | What it holds |
|---|---|
| [slides.md](./slides.md) | The deck. Speaker notes carry the argument; slides stay sparse. |
| [DECISIONS.md](./DECISIONS.md) | Settled decisions and why, including what was rejected. |
| [OPEN-QUESTIONS.md](./OPEN-QUESTIONS.md) | Open questions, risks, and what only rehearsal can settle. |
| [RESTART.md](./RESTART.md) | Paste into a fresh session to resume work against those files. |

## Develop

```bash
npm install
npm run dev
```

Then visit <http://localhost:3030>. Edit [slides.md](./slides.md) to change content.

## Build / export

```bash
npm run build    # static site -> dist/
npm run export   # PDF export
```

## Deploy

`npm run build` produces a static site in `dist/` that can be hosted on GitHub
Pages, Netlify, or Vercel (config for the latter two is already included).
