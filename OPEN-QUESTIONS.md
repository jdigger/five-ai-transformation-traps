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

### Q-01 🔴 The talk is over budget: 49:00 planned against a 45–47 min target
The speaker-note tally currently sums to **49:00** across 29 timed slides, and note-time is
systematically optimistic — a live room, a laugh, a clarifying question, and it's 55.

The overrun came from implementing D-23 (infer/enforce) and D-24 (prompt injection), which
were specified but had never been built. Roughly:

| Block | Budget |
|---|---|
| Opening (cover → spine question) | ~4:00 |
| Trap 1 | ~7:00 |
| Trap 2 | ~13:30 |
| Trap 3 | ~7:30 |
| Trap 4 | ~9:30 |
| Trap 5 | ~6:30 |
| Close | ~4:00 |

**Recommendation — cut roughly 6 minutes, in this order:**
1. **Trap 3** (~2:00). It is still the junk drawer (see R-01). The four slides are fine;
   the *notes* argue four things where one spine belongs.
2. **The "ask it to attack your framing" prompt slide** (~1:30). Good Monday material, but
   it largely restates the trap that precedes it.
3. **Trap 4's capacity slide + 2× slide** (~1:30). These overlap; the 2× question can
   absorb the capacity argument.
4. **The Sowell callback** (~1:00). It can be 30 seconds and land harder.

**Do not cut:** the Trap 1 refund loop, the Trap 2 architecture reveal, the Trap 5 ladder.
Those are the three slides the talk is built on.

**Competing demands on the same minutes:** Q-08 wants ~15 seconds in Trap 1 and Q-09 wants
~1 minute in Trap 3 — the trap already marked for the deepest cut. Resolve those two while
doing the Trap 3 pass, not separately.

**Open sub-question:** is 45–50 a hard cap from the organizers, or a target? Changes the
aggressiveness of the cut.

---

### Q-02 🟡 The Trap 4 metrics are invented — is there real data?
`−60% coding time · +80% PRs · +110% review wait · −8% idea to production` are **made up**.
The speaker notes instruct the presenter to say so out loud.

Real numbers from a real organization — even rough, even anonymized — would make Trap 4
dramatically stronger and would blunt the "engineers rationalizing their salaries"
red-team objection better than any argument can.

**Recommendation:** if real data exists, use it and say whose it is. If not, keep the
invented numbers *and keep the disclaimer* — the shape of the claim is the point, and
inventing numbers while announcing you invented them is honest. Quietly presenting
invented numbers as observed would be the exact Trap 1 failure the talk warns about.

---

### Q-03 🟡 The first-person stories are placeholders and need to be true
Several notes currently contain invented anecdotes written as if they were the speaker's:

- Trap 3 intro: *"I have caught myself doing the second one — recently, and more than once."*
- Trap 2 framing slide: *"Last time it told me that the word 'sync' in my question had
  already committed me to a direction I hadn't thought about."*
- Trap 5: *"everyone in this room has been that person"* (clicking Approve)

**These must be replaced with things that actually happened, or removed.** A talk like this
lives on the speaker's real scar tissue, and 30 years of it is the single biggest asset
here that nothing else in the deck can substitute for.

**Highest-value places for a real story:** Trap 1 (a check that couldn't have caught the
mistake), Trap 4 (a constraint that moved and everyone celebrated the wrong number), Trap 5
(authority granted before anyone thought about it).

---

### Q-04 🟡 Trap 5's title is provisional
Currently **"When AI Gets It Wrong, What Is It Allowed To Do?"** (D-37).

Alternatives: *AI Can Scale Faster Than Your Ability to Supervise It* · *What Happens When
AI Stops Asking Permission?* · *Who Gave the AI Permission to Do That?*

**Recommendation:** keep the current one. It is the least clever, states the actual
question, and sets up closing question #5 word-for-word — which makes the callback land.
Decide after a rehearsal of the ladder slide, not from the page.

---

### Q-05 🟡 Venue and logistics are unknown
Unresolved and each one changes the build:

- **Room size / screen size / projector or TV** → type sizes, and whether the 16% greyed-out
  architecture in Trap 2 will actually be visible (R-05)
- **Recorded?** → changes how carefully invented numbers and anecdotes must be flagged
- **Lectern with a confidence monitor?** → whether Slidev presenter view with notes is usable,
  which the entire notes strategy (D-05) assumes
- **Meetup name and date on the cover slide** → currently the cover carries only "Jim Moore"

---

### Q-06 ⚪ Will the slides be shared afterward, and should they stand alone?
They currently **do not** stand alone, deliberately (D-05) — the rigor is in the notes.
Someone reading the deck cold gets provocative fragments and no argument.

**Recommendation:** don't compromise the live deck for this. If sharing is expected,
export a companion document from the speaker notes after the talk is finalized — Slidev can
export with notes. Keep the two artifacts separate rather than thickening the slides.

---

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
oldest objection to TDD ("tests are expensive to write"), which cuts in TDD's favour.

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
(D-01) may not have either. And the deck already says the behaviour in plain language,
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

### R-01 🔴 Trap 3 is still the junk drawer
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

### R-04 🟡 Someone will say the refund requirement is just a bad requirement
Expected objection: *"a human would make the same mistake"* or *"that's a spec problem, not
an AI problem."* Both are half right and the notes carry the answer: yes — what changed is
the **speed and the volume of convincing-looking evidence**. Implementation, tests, and a
green build in twenty minutes, every artifact saying "verified."

**Untested.** Watch whether it survives a live challenge.

### R-05 🟡 The Trap 2 grey-out is unverified on real hardware
The reveal dims the architecture to 16% opacity. On a washed-out projector in a bright room
it may vanish entirely — which kills the effect, because the audience is supposed to still
see the ghost of the design they just approved.

**Action:** test on the actual projector. If it disappears, raise to ~30% rather than
redesigning the slide.

### R-06 🟡 Invented numbers may be quoted back as real
See Q-02. The mitigation is a single spoken sentence; if it gets dropped, the talk has
manufactured a statistic. Ironic and bad.

### R-10 🟡 Trap 2's two examples now sit in the same domain
Both the approval chain (D-44) and the greenfield agent question (D-22) are customer-service
problems, back to back. Risk: they read as the same joke told twice.

They are genuinely different kinds of hidden decision — the first is a question that assumed
a **policy**, the second is a question that assumed a **solution** — and that distinction is
what makes the pair worth more than either alone. But it is currently only implicit.

**Action:** make the speaker notes name the difference explicitly at the transition, and
watch for it in rehearsal. If the room does not feel the second one as a new idea, move the
greenfield example out of customer service rather than cutting it.

### R-07 ⚪ Trap 4 is the most likely source of a hostile question
Putting *"If developers are 2× as productive, why do we need this many developers?"* on
screen invites a manager in the room to press it. The prepared answer refuses the weak
defence and asks to measure instead (D-31) — which is honest but will not satisfy someone
who wants reassurance.

### R-08 ⚪ A security engineer will challenge the prompt-injection slide
Most likely: *"authorization doesn't solve prompt injection."* Correct, and the deck says
so. The answer is the blast-radius framing (D-24). The risk is being drawn into a security
tutorial that costs five minutes the talk does not have.

### R-09 🔴 No timing estimate has ever been rehearsed
Every number in Q-01's table is a guess made while writing. The whole timing model is
unvalidated.

**Action:** rehearse the opening → end of Trap 2 block against a clock before building
further. If 28 minutes turns out to be 35, the cut list in Q-01 is far too gentle.

---

## Only a rehearsal will resolve these

- Whether the Trap 1 refund loop needs six clicks or is too slow
- Whether the Trap 2 grey-out lands as a gut-punch or reads as a slide malfunction
- Whether the Trap 5 ladder earns 2:30 of silence-and-clicking
- Whether the five closing questions land as a callback or a summary (D-16 forbids summary)
- Whether Trap 3's two-column *Help me / Challenge me* slide is self-evident or needs setup
- Where the room actually laughs — which is where the pacing has slack

---

## Recently resolved

| Was | Now | Resolved |
|---|---|---|
| Trap 1 had no example of its own; it borrowed Trap 2's architecture | D-19 — Trap 1 owns the refund-requirement loop | 2026-08-23 |
| Inference vs enforcement specified but never built | D-23 — one slide inside Trap 2 | 2026-08-23 |
| Prompt injection specified but never built | D-24 — one slide, framed as a framing problem | 2026-08-23 |
| Trap 5 title was `[TITLE TBD]` on the slide | D-37 — provisional title set; still open as Q-04 | 2026-08-23 |
| Progressive reveals faked by duplicating slides | D-42 — `v-click` throughout | 2026-08-23 |
| Trap 2's example needed Kafka/outbox knowledge much of the room doesn't have | D-44 — refund approval chain instead; architecture survives as one spoken sentence | 2026-08-25 |
| The approval chain asserted "run in parallel" in a bullet while the diagram sat still | D-45 — the diagram restacks sequential→parallel on click 2 | 2026-08-25 |
| "Why three approvals" didn't say which ones were unnecessary | D-45 — Supervisor and Finance turn orange at the reveal; Agent stays neutral | 2026-08-25 |
| No visual language at all | D-38, D-39, D-40, D-41 | 2026-08-23 |
