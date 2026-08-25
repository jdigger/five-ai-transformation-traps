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

### Q-01 🟡 The talk is over budget: 49:15 planned against a 45–47 min target
The speaker-note tally sums to **49:15** across 29 timed slides, and note-time is
systematically optimistic — a live room, a laugh, a clarifying question, and it's 55.

**The sub-question is settled: this is a target, not a hard cap (D-47).** ~10 minutes of
slack exist. That halves the cut and changes where it comes from.

| Block | Budget |
|---|---|
| Opening (cover → spine question) | ~4:00 |
| Trap 1 | ~7:00 |
| Trap 2 | ~13:30 |
| Trap 3 | ~7:30 |
| Trap 4 | ~9:30 |
| Trap 5 | ~6:30 |
| Close | ~4:00 |

**Current plan — cut ~3 minutes, all of it from Trap 3.** Not because the clock demands
it, but because Trap 3 is a junk drawer (R-01): four slides whose *notes* argue four
things where one spine belongs. Everything else is now judged on quality alone.

**No longer on the cut list** (D-47 released them): the Sowell callback, the
"ask it to attack your framing" prompt slide, and Trap 4's capacity/2× pair. If any of
them goes, it goes because it isn't earning its place — not to buy minutes.

**Do not cut:** the Trap 1 refund loop, the Trap 2 architecture reveal, the Trap 5
ladder. Those are the three slides the talk is built on.

**Blocked on rehearsal.** Every number in the table above is a guess made while writing
(R-09). The speaker is clocking opening → end of Trap 2 before the Trap 3 pass sizes its
cut. If ~28 minutes turns out to be 35, this plan is too gentle even with the slack.

**Q-08 and Q-09 no longer compete with the trim** (D-47) — both are affordable. They
still have to earn their place in Trap 3, and that is decided during the pass.

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

### Q-05 🟡 Venue and logistics are still largely unknown
The **projector question is handled**: the venue is unknown, so the deck now assumes the
worst and dims to 30% instead of 16% (D-46). That closes the part of this that was
blocking a build decision.

Still unresolved, and each one changes something:

- **Room size / screen size** → type sizes. The deck has never been checked at distance.
- **Recorded?** → changes how hard the invented-numbers disclaimer (D-48, R-06) and any
  first-person story (Q-03) have to be flagged, because they outlive the room.
- **Lectern with a confidence monitor?** → whether Slidev presenter view with notes is
  usable, which the entire notes strategy (D-05) assumes. If there's no monitor, the
  notes strategy needs a fallback and that is a real rebuild.
- **Meetup name and date on the cover slide** → the cover currently carries only
  "Jim Moore".

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

### R-04 🟡 Someone will say the refund requirement is just a bad requirement
Expected objection: *"a human would make the same mistake"* or *"that's a spec problem, not
an AI problem."* Both are half right and the notes carry the answer: yes — what changed is
the **speed and the volume of convincing-looking evidence**. Implementation, tests, and a
green build in twenty minutes, every artifact saying "verified."

**Untested.** Watch whether it survives a live challenge.

### R-05 ⚪ The Trap 2 grey-out is mitigated but still unverified on real hardware
Raised from 16% to 30% (D-46) and verified in the browser at slide 9, click 4 — the
chain recedes without disappearing. That is insurance taken blind, not a test.

**Action:** if a tech check is possible, look at slide 9 click 4 on the actual screen. If
the ghost still washes out, go to ~45% rather than redesigning the slide. If the room
turns out to be dark with a good screen, 30% is slightly safe and could go back toward
20% for a harder gut-punch — but only with the hardware in front of you.

### R-06 🟡 Invented numbers may be quoted back as real
Now settled policy, not an open trade-off: the numbers stay invented and the speaker says
so out loud (D-48). That makes this risk **load-bearing** — the disclaimer is the only
thing standing between this talk and a manufactured statistic.

**Two failure modes to watch in rehearsal:**
1. It gets dropped under time pressure. Then the talk has manufactured a statistic, which
   is precisely the Trap 1 failure it warns about. Ironic and bad.
2. It arrives *late* — after the audience has had a beat to believe the numbers. The
   disclaimer has to land in the same breath as the metrics, not after them.

If the talk is recorded (Q-05), both get worse, because the numbers outlive the room and
the disclaimer may not travel with the clip.

### R-10 🟡 Trap 2's two examples now sit in the same domain
Both the approval chain (D-44) and the greenfield agent question (D-22) are customer-service
problems, back to back. Risk: they read as the same joke told twice.

They are genuinely different kinds of hidden decision — the first is a question that assumed
a **policy**, the second is a question that assumed a **solution** — and that distinction is
what makes the pair worth more than either alone. But it is currently only implicit.

**Action:** make the speaker notes name the difference explicitly at the transition, and
watch for it in rehearsal. If the room does not feel the second one as a new idea, move the
greenfield example out of customer service rather than cutting it.

**Update 2026-08-25:** unresolved and now worse — Trap 2 holds *three* customer-service
scenarios, and slide 12 restates slide 9's approval point outright. See R-16.

### R-12 🔴 Trap 2 is the actual junk drawer: six slides, four unrelated examples
Found 2026-08-25 by reading the whole deck end to end.

Trap 2 runs slides 9–15 at ~13:30 — nearly double any other trap — and carries four
distinct ideas:

| Slides | Example | Really about |
|---|---|---|
| 9 | Refund approval / escalation chain | a question that assumed a **policy** |
| 10–12 | Greenfield "how should we build our AI agent" | a question that assumed a **solution** |
| 13 | Ask it to attack your framing | the Monday technique |
| 14 | Infer vs Enforce | *a different topic* |
| 15 | Prompt injection | *Trap 5's question* (see R-13) |

Slides 9 and 11–12 are the trap. 13 is its payoff. **14 and 15 are passengers**, and both
notes betray it — slide 14's has to argue the connection ("this is the same question…
applied to a choice we make constantly"), and slide 15's states outright: *"here's why
this is a Trap 2 slide and not a security slide."* When a note has to argue that a slide
belongs, it usually doesn't.

**Recommendation:** the deck's cut, when it comes, should come from Trap 2, not Trap 3.
Do not act on this before deciding R-13, which may remove slide 15 for a better reason.

### R-13 🔴 The prompt-injection slide spoils Trap 5, fifteen minutes early
Slide 15's payload is *"the reframe is: what can it DO if it IS tricked?"* — and its note
then says, out loud, *"that question — what can it do when it's wrong — is where we're
going to end up at the end of this talk."*

That is slide 26's title, verbatim, and slide 26 is Trap 5's central question. The deck
currently announces its own ending during Trap 2. Whatever force *"What can it do when
it's wrong?"* has when it finally arrives, it has already been spent.

**Options:**
1. **Move the slide into Trap 5**, where its question is native. It becomes the concrete
   case that motivates the ladder instead of pre-empting it. Costs Trap 5 ~2:00 and gains
   Trap 2 the same — and R-12 says Trap 2 is where the minutes should come from.
2. **Cut it.** The security engineer's objection (R-08) is then answered from the Q&A
   block rather than the deck. Cheapest, and loses a genuinely good slide.
3. **Keep it in Trap 2 and strip the forward reference**, ending on the trust-boundary
   point alone. Keeps the sprawl (R-12) and wastes the best thing on the slide.

**Recommendation: option 1.** It fixes R-12 and R-13 with one move and costs no material.

**Also:** at its tallest click state the slide sits ~26px off the bottom of the frame.
If it stays anywhere, it needs tightening.

### R-14 🟡 "Nobody wrote it down" is now the mechanism in BOTH Trap 1 and Trap 2
Introduced into Trap 2 by D-50 and it is the strongest thing in that trap — but Trap 1
already had it: *"they never refund the setup fee — everybody in billing knows that,
nobody ever wrote it down."*

Two consecutive traps now diagnose the same root cause, which is exactly the R-02 blur.

**The distinction is real and needs saying, not assuming:**
- **Trap 1** — an undocumented **rule** made the *answer* wrong. The check couldn't catch it.
- **Trap 2** — an undocumented **rationale** made the *question* unchallengeable. The
  answer was right.

Rule vs rationale is crisp and one sentence carries it. **Recommendation:** make Trap 2's
note name the contrast explicitly at the reveal ("in Trap 1 the missing thing was a rule;
here it's the reason"), and leave Trap 1 alone.

### R-15 🟡 Trap 5's ladder quietly contradicts Trap 2 — or could become its payoff
Slide 25's top rung is **"Issue the refund"** — autonomously, by an AI. Trap 2 spent 3:30
establishing that refunds at this company move through a layered human escalation chain.
As written, the two never acknowledge each other.

**This is an opportunity, not just a defect.** If it is the same company, Trap 5's top rung
is the control that Trap 2 quietly deleted, now handed to an AI. That is a genuine
narrative callback across three traps, and it costs one sentence.

**Careful:** D-14 refuses to explain the *trap progression* to the audience. This is not
that — it is a concrete callback inside the example domain, not a meta-explanation of
structure. But it must stay one sentence or it becomes the thing D-14 forbids.

### R-16 🟡 Trap 2 makes the approval point twice, and R-10 is now worse
Slide 12's option list includes *"maybe the 18 minutes is four minutes of work and fourteen
minutes of waiting for a second approval, in which case the answer isn't software at all."*

That is slide 9's example, restated, three slides later — and it lands as a throwaway
option in a list rather than as the thing the room just spent three and a half minutes on.

Trap 2 now has **three** customer-service scenarios (refund approvals, the service agent,
the customer's email), which is R-10 unresolved and compounded.

**Recommendation:** cut the approval clause from slide 12's list and replace it with a
non-approval, non-customer-service option, so the greenfield example reads as a genuinely
new kind of hidden decision (a question that assumed a *solution*, not a *policy*).

### R-17 ⚪ An unexploited handoff from Trap 2 into Trap 4
Slide 9's click 5 now ends on *"the ticket says CAPACITY."* Trap 4 is titled *Faster
Doesn't Mean You Should Do More* and is entirely about capacity and where it goes.

Nothing connects them. One transition sentence would make Trap 4 arrive as something the
deck already earned rather than a new subject.

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

**Action — accepted and assigned 2026-08-25.** The speaker is clocking opening → end of
Trap 2 out loud before the Trap 3 pass sizes its cut. Q-01's cut stays provisional until
that number lands. If 28 minutes turns out to be 35, the plan in Q-01 is far too gentle
even with D-47's slack.

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
| Q-01's sub-question: is 45–50 a hard cap or a target? | D-47 — a target, ~10 min slack; the cut halves to ~3 min, all from Trap 3 | 2026-08-25 |
| Q-02 — are Trap 4's metrics real? | D-48 — no real data; keep them invented and say so out loud | 2026-08-25 |
| R-05's build decision: is 16% opacity safe on unknown hardware? | D-46 — no; raised to 30% | 2026-08-25 |
| R-11 — the refund chain is notorious, not hidden, which inverts Trap 2's reveal | D-49 — the reveal moves to the deleted escalation chain; $12 becomes a spoken second beat | 2026-08-25 |
