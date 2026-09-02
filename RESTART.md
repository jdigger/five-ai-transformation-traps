# Restart Prompt

**Paste everything below the line into a fresh session to resume work on this talk.**

The three tracking files are the source of truth. This prompt is deliberately thin — it
tells you *how to work*, not *what has been decided*. Keep it that way, or the files drift.

---

I'm building a one-hour Slidev presentation for a local Agile/software/technology meetup:

# The Five Biggest AI Transformation Traps: Do This, Not That

You are taking over active development. This has been through substantial brainstorming,
red-teaming, and one full implementation pass. **Do not restart the conceptual work.**

## Read these first, in this order

1. **`DECISIONS.md`** — start with **"The talk as it currently stands"** at the top; it
   gives you the whole shape in a page. Then the settled decisions and *why*, including a
   rejection list. Treat these as settled. Challenge one only with a concrete reason from construction or
   rehearsal, and if it changes, record the change (see *Maintenance* below).
2. **`OPEN-QUESTIONS.md`** — what's genuinely in flux: open questions with recommendations,
   a risk watch list, and items only a rehearsal can settle.
3. **`slides.md`** — the current implementation. This is the real state of the talk.
4. **`styles/index.css`** — the deck's visual language. Read the header comment.

Do not re-derive anything those files already answer.

## Your job

Turn the current thinking into an excellent *live* presentation: Slidev implementation,
narrative, visual design, diagrams, progressive reveals, examples, speaker notes,
transitions, timing, and eventually rehearsal and refinement.

Continue to red-team the material while building it. If something that sounded good
conceptually does not work when presented, say so and change it.

## Working method

**Speaker notes are lectern cues, not prose (D-57).** `slides.md` notes are scannable
delivery cues for a live room; `SCRIPT.md` holds the long-form prose. Notation: `~M:SS`
first line · `**[n]**` a click beat · `-` a cue said in your own words · `>` an engineered
line said close to verbatim · `**BOLD LEAD:**` a guardrail · `→` a transition.
**Every cue must be a list item, heading, or blockquote** — adjacent bare lines collapse
into a paragraph when rendered and silently rebuild the script.

**American English throughout.** Slides, speaker notes, tracking files, and CSS comments:
*humor*, *organization*, *gray*, *defense*, *behavior*, *centered*. The speaker is American
and so is the room.

**Keep three layers separate.** What appears on screen · what the speaker says · what the
speaker understands but never explains. Never solve complexity by putting more words on a
slide.

**Red-team from these positions**, and check any significant addition against them:

| Position | The challenge |
|---|---|
| AI maximalist | "You're preserving humans because you're uncomfortable with AI." |
| CTO / executive | "This is engineers rationalizing their salaries." |
| Working developer | "So AI writes everything *and* I have to understand everything?" |
| Agile skeptic | "You rediscovered Agile." |
| Senior architect | "You can't experimentally answer every architecture question." |
| Security engineer | "Authorization doesn't solve prompt injection." |
| Future-model advocate | "This all assumes today's AI stays unreliable." |
| Organizational expert | "Evidence doesn't decide; organizational power does." |
| Small-business owner | "I need to survive 18 months, not build a talent pipeline." |

`DECISIONS.md` records how each of these is answered. If your change breaks one of those
answers, the change is wrong.

**The meta-rule.** Continually ask: *are we solving the right problem?* Do not let a
sophisticated presentation become evidence that its own framing was correct — that would
reproduce the exact failure the talk warns about. But equally, do not continuously
redesign concepts that are already doing their job. Presentation reality drives changes
now, not further theorizing.

**Coherency before cutting (D-51).** The current phase is getting the examples and the
narrative move through the deck right. Trimming is mechanical; perfecting what is said is
not. Recompute and report the timing tally after every content change, but do **not** let
a number over budget block or shrink the work — the cut happens once, near the end,
against a stable deck. Q-01 is not a gate.

## Maintenance — this is part of the work, not paperwork

Update the tracking files **in the same session** as the change, before reporting done.

**`DECISIONS.md`** — append-only, **plus one maintained section**.
- The file opens with **"The talk as it currently stands"** — a derived summary of the
  argument's shape: the frame, the engine under all five traps, the trap table, the
  standing commitments, and what must not be flattened. Fifty-odd independent entries are
  right for provenance and useless for seeing the talk. **Update that section in the same
  session as any decision that changes the argument**, and keep it derived — if it ever
  disagrees with an entry, the summary is what's wrong.
- Everything below it is append-only.
- A new decision gets the next `D-nn`, with **Decided** (absolute date), **Status**, the
  decision, **Why**, and what was **Rejected** if anything.
- Never edit a decision to say something different. Mark the old one
  `Status: Superseded by D-nn` and write a new entry with a `Supersedes:` pointer. The
  discarded reasoning is the valuable part.
- If you reject an approach during construction, add it to the **rejected** table at the
  bottom so nobody proposes it again.

**`OPEN-QUESTIONS.md`**
- New uncertainty → new `Q-nn` (needs a decision) or `R-nn` (risk to watch), with a status
  marker and a current recommendation, so future work can proceed under a stated assumption
  instead of blocking.
- Resolved → write the `D-nn` in `DECISIONS.md`, delete the `Q`/`R`, and add a row to
  *Recently resolved* pointing at it.
- Keep the Q-01 timing table current whenever slide content changes materially.

**`RESTART.md`** (this file) — only when the *process* changes. It must not accumulate
decisions or open questions; those belong in the other two files.

## Editing: use the Slidev MCP server

A Slidev MCP server is configured for this repo. Codex loads it from
`.codex/config.toml`; restart Codex and open a new task after first cloning or adding the
configuration. Claude can register the same server with
`claude mcp add slidev -- npx --no-install slidev mcp slides.md`. Prefer it over
hand-editing `slides.md` for anything structural:

| Tool | Use it for |
|---|---|
| `slidev-get-info` | deck overview: entry file, title, slide count |
| `slidev-list-slides` | number → title → layout for every slide |
| `slidev-get-slide` | one slide's frontmatter, content and speaker note, separately |
| `slidev-update-slide` | change content / note / frontmatter without touching the rest |
| `slidev-insert-slide` · `remove-slide` · `move-slide` | add, cut, reorder |

**Why it matters here.** Slides are separated by `---`, which is also the frontmatter
delimiter, so text-splicing a slide out of this file silently eats separators and merges
two slides — that has already happened once. And slide *numbers* are what the browser
needs for verification, but nothing in the file tells you them; `slidev-list-slides` does.
The cutting pass in Q-01 in particular should go through `remove-slide` / `move-slide`.

**What it does not do:** it cannot tell you whether a slide *renders* correctly, fits the
frame, or whether its reveals fire. That still needs the browser loop below. Structural
edits through the MCP, visual verification through screenshots.

## Running and verifying

```bash
npm run dev
```

Then open `http://localhost:3030`. Useful URL forms while building:
`http://localhost:3030/11?clicks=2` jumps to slide 11 with two reveals fired —
**always check reveal states this way rather than assuming**, and screenshot the slide.
**For notes, use `http://localhost:3030/notes`, not `/presenter/`** — presenter view
gives notes a small corner; `/notes` is full-width with a click-progress bar and font-size
controls, and stays in sync (D-57). `/presenter/` is still right for checking slide + next
+ timer together.

**Five traps in the tooling itself, all of which have already cost time:**

- **Slidev counts *registered* `v-click` elements, not the highest index you wrote.** A
  slide whose beats are 1, 3, 4, 5 — because beat 2 is only a `:class="{ x: $clicks >= 2 }"`
  binding with no `v-click` element — caps at four clicks, and the last reveal silently
  never fires. `clicks:` in the slide frontmatter does **not** rescue this. Keep click
  indices contiguous and back every beat with a real `v-click` element; drive purely
  visual changes off `$clicks >= n` *in addition to*, never *instead of*, a real element.
- **And the mirror of it: `clicks:` in frontmatter declaring MORE clicks than there are
  elements creates dead presses** — the speaker clicks forward, nothing happens, they
  click again. Do not add `clicks:` to frontmatter at all (D-52); let Slidev auto-count.
  This bit four slides including the Trap 5 authority ladder, where rhythm carries the
  whole reveal.
- **A hidden `v-click` element still occupies layout.** One left in normal flow squeezed
  the Trap 2 chain and wrapped a node onto two lines at *every* click state — including
  the base state, which is the one you are least likely to re-screenshot. Position reveal
  annotations absolutely, and check a changed slide's **base** state as well as its
  tallest.
- **HMR does not reliably pick up speaker-note edits at all.** The `/notes` and
  `/presenter` views will happily serve stale notes through a hard reload. Restart the dev
  server after editing notes, or you will verify the previous version and believe it.
- **HMR does not always pick up structural edits.** If a slide renders at its base state
  when you asked for clicks, reload the page before concluding the markup is wrong.

Content is vertically centered and will silently overflow a 450px-tall frame before it
clips. Screenshot the **tallest** click state of any slide you change, not just the first.

```bash
npm run build
```

Confirms the deck compiles. Run it before committing.

**Recompute the timing budget** after any content change:

```bash
grep -oE '^~[0-9]+:[0-9]{2}' slides.md | sed 's/~//' | awk -F: '{t+=$1*60+$2} END {printf "%d:%02d over %d slides\n", t/60, t%60, NR}'
```

Each slide's notes open with a `~M:SS` marker. Target is 45–47 minutes of planned content,
leaving room for 10–15 minutes of discussion.

## Where to pick up

Start from `OPEN-QUESTIONS.md`. Anything marked 🔴 is blocking further building.

If nothing there is actionable without input from me, say so and ask — don't invent an
answer to a question that is mine to make. Questions about what I actually experienced,
what my organization actually measured, and what the venue is really like cannot be
guessed, and guessing them produces exactly the confident-and-wrong artifact this talk is
about.
