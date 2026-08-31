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

## Codex support

This repository configures Slidev's MCP server in [`.codex/config.toml`](./.codex/config.toml),
giving Codex slide-aware tools for inspecting and editing the deck. After cloning the
repository or installing dependencies, restart Codex and open a new task in this project.
Use `/mcp` in Codex or run `codex mcp list` to confirm that `slidev` is connected.

The server uses `npx --no-install`, so it runs the repository's installed Slidev version
without downloading another package. Run `npm install` first if dependencies are absent.

## Build / export

```bash
npm run build    # static site -> dist/
npm run export   # PDF export
```

## Deploy

`npm run build` produces a static site in `dist/` that can be hosted on GitHub
Pages, Netlify, or Vercel (config for the latter two is already included).
