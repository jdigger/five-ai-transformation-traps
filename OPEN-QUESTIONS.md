# Open Questions & Risks

Everything still in flux for **The Five Biggest AI Transformation Traps**.

**How to use this file**
- `Q-nn` = a question that needs a decision. `R-nn` = a known risk to watch while building.
- When something is settled, move it to [DECISIONS.md](./DECISIONS.md) as a new `D-nn`
  entry and record it under *Recently resolved* below with a pointer. Don't just delete it.
- Every `Q` carries a current recommendation, so a session can proceed under a stated
  assumption rather than blocking.

**Status key:** 🔴 blocking further building · 🟡 needed before the talk · ⚪ nice to resolve

---

## Needs a decision

### Q-01 🟡 The talk is over budget: 48:45 planned against a 45–47 min target
The speaker-note tally sums to **48:45** across 31 timed slides, and note-time is
systematically optimistic — a live room, a laugh, and pauses on the three money slides
will push the delivery longer.

**The sub-question is settled: this is a target, not a hard cap (D-47).** ~10 minutes of
slack exist. That halves the cut and changes where it comes from.

| Block | Slides | Budget |
|---|---|---|
| Opening | 1–3 | 4:15 |
| Trap 1 | 4–7 | 7:30 |
| Trap 2 | 8–14 | 9:00 |
| Trap 3 | 15–19 | 7:45 |
| Trap 4 | 20–24 | 7:30 |
| Trap 5 | 25–29 | 8:30 |
| Close | 30–32 | 4:15 |

*Recomputed from the note markers 2026-09-02 after D-64. Slide 32 is deliberately
untimed, so 31 slides carry markers.*

**Current plan — rehearse before choosing the remaining cut.** D-60 removed two minutes
from Trap 2 on quality grounds, and D-64's cleaner example removed another 1:45. The deck
still needs roughly 1:45 to reach the top of the
target range, and note-time is optimistic. Trap 3 remains dense, but R-01 explicitly
warns against treating it as the automatic source of every remaining minute.

**No longer on the cut list** (D-47 released them): the Sowell callback, the
"ask it to attack your framing" prompt slide, and Trap 4's capacity/2× pair. If any of
them goes, it goes because it isn't earning its place — not to buy minutes.

**Do not cut:** the Trap 1 refund loop, Trap 2's `344 cases → one product problem` reveal, the Trap 5
ladder. Those are the three slides the talk is built on.

**Blocked on rehearsal.** Every number in the table above is a guess made while writing
(R-09). The speaker is clocking opening → end of Trap 2 before deciding where the
remaining cut comes from.

**Q-08 and Q-09 no longer compete with the trim** (D-47) — both are affordable. They
still have to earn their place in Trap 3, and that is decided during the pass.

---

### Q-04 🟡 Trap 5's title is provisional
Currently **"When AI Gets It Wrong, What Is It Allowed To Do?"** (D-37).

Alternatives: *AI Can Scale Faster Than Your Ability to Supervise It* · *What Happens When
AI Stops Asking Permission?* · *Who Gave the AI Permission to Do That?*

**Recommendation:** keep the current one. It is the least clever, states the actual
question, and sets up closing question #5 word-for-word — which makes the callback land.
Decide after a rehearsal of the ladder slide, not from the page.

---

### Q-05 🟡 Venue and logistics are still largely unknown
The **projector question is handled**: the venue is unknown, so the deck now assumes the
worst and dims to 30% instead of 16% (D-46). That closes the part of this that was
blocking a build decision.

Still unresolved, and each one changes something:

- **Room size / screen size** → type sizes. The deck has never been checked at distance.
- ~~**Recorded?**~~ → **Resolved: no video recording (D-56).** This cleared the humor
  register (D-54) and removed the posterity burden from Q-03's stories.
- **Lectern with a confidence monitor?** → whether Slidev presenter view with notes is
  usable, which the entire notes strategy (D-05) assumes. If there's no monitor, the
  notes strategy needs a fallback and that is a real rebuild.
- **Meetup name and date on the cover slide** → the cover currently carries only
  "Jim Moore".

### Q-06 🟡 What gets shared afterward — slides, slides + notes, or a rollup?
Speaker is undecided between three forms. Raised in priority: the deck deliberately does
**not** stand alone (D-05 — the rigor is in the notes), so this choice materially changes
what a reader gets.

**a · Presentation slides only — actively bad, and I'd argue against it.**
R-03 already flags that *"A Great Answer Doesn't Mean You're Right"*, *"Faster Doesn't Mean
You Should Do More"* and *"Are You Understanding Faster — or Avoiding Understanding?"* each
read as anti-AI when seen out of context, and all three are defused **verbally only**. A
slides-only artifact ships the provocations without any of the qualifications. D-56 fixed
the worst instance (the Trap 4 metrics) but not the general problem.

**b · Slides + speaker notes — honest, complete, nearly free.**
The notes are written as stage directions, not prose — *"[beat]"*, *"do NOT point at the
numbers"*, *"take the laugh"*. A reader gets a shooting script rather than an essay, which
is charming to some and strange to others, and it does expose the performance mechanics to
anyone who was in the room. Zero additional work; Slidev exports it directly.

**c · A rollup — most useful, some work.**
The highest-value version is small, not a document: **the five Monday questions, one page,
two or three sentences each.** That is the artifact most likely to end up pinned to a wall,
and it maps exactly onto the success criterion (D-03 — a better question a month later).
Slide 30 already *is* this in skeleton form, and the notes already contain the prose.

**Recommendation: (c), scoped to one page, optionally alongside (b) for anyone who wants
the full argument.** Explicitly not (a) on its own. Do not thicken the live deck to make
it stand alone — that trade was settled in D-05 and remains right.

**Decide after the deck is finalized**, since the rollup is generated *from* the notes and
would need regenerating after any content change.

### Q-07 ⚪ Is the 10–15 minutes open Q&A or facilitated discussion?
An Agile meetup often prefers discussion over interrogation. If discussion is wanted, two
or three seeded prompts would help — e.g. *"Where in your pipeline did the constraint
actually move?"* or *"What is the most consequential thing your systems let AI do today
without asking?"*

**Recommendation:** prepare the prompts; use them only if the room goes quiet. A prepared
Q&A block already exists in the final slide's notes.

---

### Q-08 🟡 Does any of this change the value or the practice of TDD?
Unaddressed anywhere in the deck, and near-certain to be asked in the room — it is an
Agile meetup, and TDD is the most concrete shared practice the audience has.

**The interesting half.** Test-first ordering was always partly a design-pressure
mechanism and partly a *don't-fool-yourself* mechanism: a test written before the
implementation cannot have been derived from the implementation. That second half is
exactly the Trap 1 property — *could this check catch the original mistake?* So the honest
claim is that **AI makes TDD's ordering discipline more valuable, not less**, because
derived-check contamination is now fast, fluent, and voluminous. It also removes the
oldest objection to TDD ("tests are expensive to write"), which cuts in TDD's favor.

**The honest limit — do not skip this.** TDD gives you independence between the test and
the *implementation*. It gives you nothing against a misread *requirement*: you write a
test-first test encoding the misunderstanding, implement to it, and you are exactly as
wrong. That gap is precisely where the refund example lives (D-19), and it is why the
Trap 1 evidence slide reaches for invariants, replay against real history, and the person
who wrote the policy instead.

**A concrete Monday technique that falls out of this**, and probably the most useful thing
in the whole question: *"AI, write the implementation"* followed by *"AI, now write the
tests"* in the same context is the maximum-contamination case. Generating tests from the
requirement in a **fresh** context, before the implementation exists, is meaningfully
better evidence for roughly the same effort. That is TDD's ordering applied to an AI
workflow, and it costs nothing to adopt.

**Second-order:** red-green-refactor is the Trap 3 learning loop (*question → try →
evidence → learn*) running on a 30-second cadence, and AI makes each cycle cheaper. But
watch the design-pressure half — if you are not writing the code, you feel a bad interface
less, which is the Trap 3 warning about staying connected to implementation evidence (D-28).

**Recommendation:** do **not** add a TDD section — it would cost minutes the talk does not
have (Q-01) and risks a practice-taxonomy detour (D-17). Instead:
1. Add **one spoken sentence** on the *"Could this check catch the original mistake?"*
   slide — TDD is one historical answer to that exact question, and the room already owns
   it. Roughly 15 seconds, and it earns real credibility with an Agile audience.
2. Put the **full nuanced answer above into the prepared Q&A block** on the final slide.
   Someone will ask.

The fresh-context technique is the one piece good enough that it could justify its own
line on the Trap 1 evidence slide if a rehearsal shows room.

---

### Q-09 🟡 Should steel-manning and red-teaming be named explicitly?
They are already the method of the entire talk, but always unnamed and always local:

- **T1** — *"Use AI to challenge your thinking, then use evidence to challenge both of you."*
- **T2** — *"What assumptions did I bake into that question?"*, *"Why are these two services?"*
- **T3** — *"Challenge my understanding"*, *"What's the strongest argument for the approach
  I rejected?"* (that second one is a steel-man, verbatim, unnamed)

Right now these read as three separate tips. Named once, they compress into **one move
applied at three levels** — the answer, the question, your own understanding — which maps
onto the trap progression (D-14) instead of fighting it. That is a real gain against the
success criterion (D-03): one thing to carry out of the room beats three.

**The genuinely non-obvious part, and the reason this is worth more than a label.**
The two halves are asymmetric with respect to what AI actually changed. AI is *superb* at
generating the steel-man — it will argue any position fluently, instantly, tirelessly,
with no ego and no politics, which is exactly what makes human steel-manning so rare and
so expensive. But it is much weaker at telling you **which** critique deserves your
attention. So:

> Generating the counter-argument became free. Deciding which counter-arguments matter
> did not.

That is the concrete, sayable version of D-12 (scarcity and attention), which is currently
buried as speaker-only understanding. *"Red-team your ideas with AI"* on its own would be
banal; the asymmetry is not.

**The case against.** D-14 deliberately refuses to explain the trap progression to the
audience; naming a cross-cutting theme risks the same meta-layer problem. D-17 caps
frameworks hard, and "steel-man / red-team" could grow into a sixth one. *Red-team* is mild
in-group jargon and *steel-man* more so — the business and management half of the room
(D-01) may not have either. And the deck already says the behavior in plain language,
which may make the label pure overhead.

**Recommendation:** name it **once**, in Trap 3, and never again — Trap 3 is where
*"Challenge my understanding"* already lives, and it is the trap that turns the lens on the
practitioner. Say both words, define neither at length, attach the asymmetry above, and let
T1 and T2 re-read as instances of it in hindsight. Do **not** give it a slide of its own, a
diagram, or a place in the five closing questions.

**Conflict to resolve first:** this costs ~1 minute in the one trap already marked for
cutting (R-01, Q-01). It competes directly with the Trap 3 trim rather than being free.
My instinct is that it *replaces* some of what should be cut there — naming the move is a
better use of Trap 3's minutes than the fourth argument currently in its notes — but that
should be decided while doing the Trap 3 pass, not before it.

---

## Risks & watch list

### R-01 ⚪ Trap 3 is the junk drawer — CONTESTED, probably stale
**Challenged 2026-08-25 by a full read of the deck. See R-12: the sprawl is in Trap 2.**
Trap 3 is now three content slides with one clean spine (offloading is good → two modes →
go find out). Its *notes* still over-argue, and a trim is worth doing, but it is no longer
the worst offender and should not be the default place minutes come from.

Original entry follows.

### R-01a · Trap 3 is still the junk drawer
It carries learning, juniors, seniors, cognitive offloading, seams, experiments, red
teaming, Agile loops, and expertise development. The slides are now sparse, but the notes
still argue all of it.

The intended spine is one sentence: **AI makes doing easier — use some of that capacity to
make learning easier.** Then: *Help me understand* → *Challenge my understanding* → *How
can we find out?*

**Action:** cut aggressively on the next pass. This is also where Q-01's minutes come from.

### R-02 🟡 Traps 1 and 2 could re-blur
Fixed on screen this session by giving Trap 1 its own example (D-19). The distinction is:
**T1 = is the answer actually right? · T2 = why are we solving this problem at all?**
Any new Trap 1 content that touches framing will collapse them again.

### R-03 🟡 Several slides read as anti-AI when photographed out of context
*"A Great Answer Doesn't Mean You're Right"*, *"Faster Doesn't Mean You Should Do More"*,
and *"Are You Understanding Faster — or Avoiding Understanding?"* are each one click from
an AI-skeptic misreading. All three are currently defused **verbally**, not on screen.

This is an accepted trade (the titles work because they're jarring — D-18, D-30), but the
verbal qualifications are now load-bearing and must not be dropped under time pressure.
Trap 4's qualification in particular has to arrive *within seconds* of the title.

### R-19 ⚪ Should "one check, forty-seven times" go on screen?
Trap 1's core beat (D-58) is currently spoken, delivered while pointing at the
`47 passing · 0 failing` node that is already on slide 5. That is cheap, uses an artifact
already present, and costs no clicks.

**The case for putting it on screen:** it is arguably the single most portable line in the
deck, it is the one idea from Trap 1 most likely to survive a month (D-03), and Trap 1's
other load-bearing moment — the green build flipping orange — is visual while this is not.

**Two ways to do it:** a sixth beat on slide 5, or a `statement-slide` immediately after
it. The statement surface already exists in the visual language (D-40).

**The case against:** slide 5 already ends on the orange flip, which is a strong close.
A sixth beat risks stepping on it, and a separate slide costs ~45s in a trap that just
grew to 7:30.

**Recommendation:** decide at rehearsal — specifically, whether the spoken version lands
without visual support. If it does, leave it alone.

### R-06 ⚪ Invented numbers may be quoted back as real
Largely mitigated. The numbers stay invented and the speaker says so (D-48), **and the
slide now carries `illustrative figures, not measured` on screen** (D-56), so the caveat
travels with the artifact instead of living only in the speaker's mouth. That closes the
original failure mode — the spoken line being dropped under time pressure — and the
no-recording decision removes the clip risk entirely.

**Residual watch:** the qualifier is small by design. If the deck is shared as images or
re-used in someone else's slides, it could still be cropped out. Not worth making it
uglier; worth knowing.

### R-07 ⚪ Trap 4 is the most likely source of a hostile question
Putting *"If developers are 2× as productive, why do we need this many developers?"* on
screen invites a manager in the room to press it. The prepared answer refuses the weak
defense and asks to measure instead (D-31) — which is honest but will not satisfy someone
who wants reassurance.

### R-08 ⚪ A security engineer will challenge the prompt-injection slide
Most likely: *"authorization doesn't solve prompt injection."* Correct, and the deck says
so. The answer is the blast-radius framing (D-24). The risk is being drawn into a security
tutorial that costs five minutes the talk does not have.

### R-09 🔴 No timing estimate has ever been rehearsed
Every number in Q-01's table is a guess made while writing. The whole timing model is
unvalidated.

**Action — accepted and assigned 2026-08-25.** The speaker is clocking opening → end of
Trap 2 out loud before the Trap 3 pass sizes its cut. Q-01's cut stays provisional until
that number lands. If 28 minutes turns out to be 35, the plan in Q-01 is far too gentle
even with D-47's slack.

---

## Only a rehearsal will resolve these

- Whether the Trap 1 refund loop needs six clicks or is too slow
- Whether Trap 2's `344 cases → one product problem` pause gives the room enough time to reclassify the work
- Whether the Trap 5 ladder earns 2:30 of silence-and-clicking
- Whether the five closing questions land as a callback or a summary (D-16 forbids summary)
- Whether Trap 3's two-column *Help me / Challenge me* slide is self-evident or needs setup
- Where the room actually laughs — which is where the pacing has slack

---

## Recently resolved

| Was | Now | Resolved |
|---|---|---|
| Trap 2's refund-approval optimization looked irrational before its reveal | D-64 — excellent support automation wins first; 344 contacts then reveal one product defect | 2026-09-02 |
| R-05 — Trap 2's gray-out needed projector verification | D-64 — the gray-out and approval-chain slide were removed | 2026-09-02 |
| R-10/R-15/R-17 — duplicated customer-service examples and approval-chain callbacks created cross-trap tension | D-64 — Trap 2 now stays adjacent to refunds without reusing their approval mechanism | 2026-09-02 |
| Q-03 — three invented anecdote placeholders remained in the spoken track | D-63 — removed them; future personal stories must be true | 2026-09-01 |
| Trap 1 had no example of its own; it borrowed Trap 2's architecture | D-19 — Trap 1 owns the refund-requirement loop | 2026-08-23 |
| Inference vs enforcement specified but never built | D-23 — one slide inside Trap 2 | 2026-08-23 |
| Prompt injection specified but never built | D-24 — one slide, framed as a framing problem | 2026-08-23 |
| Trap 5 title was `[TITLE TBD]` on the slide | D-37 — provisional title set; still open as Q-04 | 2026-08-23 |
| Progressive reveals faked by duplicating slides | D-42 — `v-click` throughout | 2026-08-23 |
| Trap 2's example needed Kafka/outbox knowledge much of the room doesn't have | D-44 — refund approval chain instead; architecture survives as one spoken sentence | 2026-08-25 |
| The approval chain asserted "run in parallel" in a bullet while the diagram sat still | D-45 — the diagram restacks sequential→parallel on click 2 | 2026-08-25 |
| "Why three approvals" didn't say which ones were unnecessary | D-45 — Supervisor and Finance turn orange at the reveal; Agent stays neutral | 2026-08-25 |
| No visual language at all | D-38, D-39, D-40, D-41 | 2026-08-23 |
| Q-01's sub-question: is 45–50 a hard cap or a target? | D-47 — a target, ~10 min slack; the cut halves to ~3 min, all from Trap 3 | 2026-08-25 |
| Q-02 — are Trap 4's metrics real? | D-48 — no real data; keep them invented and say so out loud | 2026-08-25 |
| R-05's build decision: is 16% opacity safe on unknown hardware? | D-46 — no; raised to 30% | 2026-08-25 |
| R-11 — the refund chain is notorious, not hidden, which inverts Trap 2's reveal | D-49 — the reveal moves to the deleted escalation chain; $12 becomes a spoken second beat | 2026-08-25 |
| R-14 — "nobody wrote it down" is the mechanism in both Trap 1 and Trap 2 | D-53 — a missing *rule* makes the answer wrong; a missing *rationale* makes the question unchallengeable | 2026-08-25 |
| R-13 — the prompt-injection slide spoiled Trap 5's question fifteen minutes early | D-55 — moved into Trap 5 between the ladder and its question | 2026-08-25 |
| R-16 — slide 12 restated slide 9's approval point | D-55 — replaced with a non-approval option; the note names the policy/solution distinction | 2026-08-25 |
| R-12 — Trap 2 is the junk drawer | D-55 — largely resolved; narrowed to R-18 (slide 14 alone) | 2026-08-25 |
| Q-05's "is it recorded?" | D-56 — no video recording; clears the humor register and Q-03's posterity burden | 2026-08-25 |
| R-04 — someone will say the refund requirement is just a bad requirement | D-58 — inverted; the objection is now Trap 1's led core beat, and the mechanism is named as collapsed independence | 2026-08-25 |
| R-18 — inference vs enforcement was a passenger in Trap 2 | D-60 — cut; the handoff moved onto the framing-prompt slide | 2026-08-31 |
