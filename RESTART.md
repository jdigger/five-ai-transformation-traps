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

1. **`DECISIONS.md`** — every settled decision and *why*, including a rejection list.
   Treat these as settled. Challenge one only with a concrete reason from construction or
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

**Bias to cutting.** The talk is over budget (`OPEN-QUESTIONS.md` Q-01). Adding anything
means naming what it displaces.

## Maintenance — this is part of the work, not paperwork

Update the tracking files **in the same session** as the change, before reporting done.

**`DECISIONS.md`** — append-only.
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

## Running and verifying

```bash
npm run dev
```

Then open `http://localhost:3030`. Useful URL forms while building:
`http://localhost:3030/9?clicks=4` jumps to slide 9 with four reveals fired —
**always check reveal states this way rather than assuming**, and screenshot the slide.
Presenter view with notes is at `http://localhost:3030/presenter/`.

**Two traps in the tooling itself, both of which have already cost time:**

- **Slidev counts *registered* `v-click` elements, not the highest index you wrote.** A
  slide whose beats are 1, 3, 4, 5 — because beat 2 is only a `:class="{ x: $clicks >= 2 }"`
  binding with no `v-click` element — caps at four clicks, and the last reveal silently
  never fires. `clicks:` in the slide frontmatter does **not** rescue this. Keep click
  indices contiguous and back every beat with a real `v-click` element; drive purely
  visual changes off `$clicks >= n` *in addition to*, never *instead of*, a real element.
- **HMR does not always pick up structural edits.** If a slide renders at its base state
  when you asked for clicks, reload the page before concluding the markup is wrong.

Content is vertically centred and will silently overflow a 450px-tall frame before it
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
