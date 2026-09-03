# Working in this repository

A one-hour Slidev talk: *The Five Biggest AI Transformation Traps: Do This, Not That*.

Repo-specific knowledge lives **in this repo**, not in agent-tool memory directories.
If you learn something durable about how this deck should be built, record it here or in
the tracking files below — never in `~/.claude`, `~/.codex`, or an equivalent.

## Read these before changing anything

The talk has been through substantial brainstorming and red-teaming. Do not re-derive
what these already answer, and do not restart the conceptual work.

| File | What it holds |
|---|---|
| `RESTART.md` | How to work on this deck. Read it first; it is the onboarding prompt. |
| `DECISIONS.md` | Settled decisions and why, including a rejection list. |
| `OPEN-QUESTIONS.md` | What is genuinely still in flux. |
| `slides.md` | The deck itself — the real state of the talk. |
| `styles/index.css` | The visual language. Read the header comment. |

## Speaker notes lead with the spoken script

Each slide's note is ordered:

1. The `~M:SS` timing cue on the first line.
2. **Jim's draft script** — the actual spoken words, prose, no heading.
3. `# Supporting Notes` — the structured cues, pull-quotes, and guardrails behind it.

The presenter pane shows the top of a note first, so whatever leads is what gets read
while talking. Spoken words go first (D-69, amending D-57).

When adding or editing a slide, write the spoken words first and put structured cues
under `# Supporting Notes`. Cue notation inside that section is unchanged: `**[n]**` a
click beat · `-` a cue said in your own words · `>` a line said close to verbatim ·
`**BOLD LEAD:**` a guardrail · `→` a transition.

**`SCRIPT.md` is reference only.** It is not rehearsed or spoken from. Do not sync it
phrase-by-phrase against `slides.md` — the wording in `slides.md` always wins. Update
`SCRIPT.md` only when the underlying reasoning changes.

## Write to developers

The room is mixed technical and management, but the non-engineers were largely developers
once or work closely with them (D-74). Technical specifics — `@Transactional`, idempotency,
a compiler's guarantees — need no translation or apology, and diluting them for
accessibility usually makes the deck worse. This is not license for the abstract
theory-speak banned in D-07: *"retry meets idempotency"* is fine, *"causal independence of
validation"* is not.

## Never say a trap number on stage

Callbacks name the idea or the story, never the number (D-75) — *"that's the
solving-the-wrong-problem issue again"*, not *"that's Trap 2"*; *"the same question we asked
about those forty-seven passing tests"*, not *"same rule as Trap 1"*. The audience has no
numbered index in front of them and cannot dereference a pointer mid-talk. Numbers belong
in the speaker notes, where they aid navigation.

## American English throughout

Slides, speaker notes, tracking files, CSS comments, and commit messages: *humor*,
*organization*, *gray*, *defense*, *behavior*, *centered*, *labeled*. The speaker is
American and so is the room.

Watch the `-ise`/`-ize` family, but leave words that are always `-ise` alone (*surprise*,
*supervise*, *compromise*, *advertise*, *exercise*, *promise*, *revise*). CSS keywords
like `grayscale` are already American — do not "correct" them.

## Editing and verifying

- Use the Slidev MCP tools for structural slide edits rather than splicing `---`
  separators by hand.
- Verify with `npm run build`, and check reveal states in the browser at
  `http://localhost:3030/12?clicks=1` rather than assuming them.
- For notes at the lectern use `http://localhost:3030/notes`, not `/presenter/`.
- Record decisions in `DECISIONS.md` when they settle; keep `RESTART.md` thin.
