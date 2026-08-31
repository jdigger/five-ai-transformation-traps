# Decisions

Settled decisions for **The Five Biggest AI Transformation Traps: Do This, Not That**,
and the reasoning behind them.

**Purpose:** stop a future session (human or agent) from re-litigating what is already
settled, and — more importantly — record what was *rejected* and why, so discarded ideas
stay discarded.

**How to use this file**
- Entries are append-only. Never delete a decision; mark it `Superseded` and add the
  replacement as a new entry with a `Supersedes:` pointer.
- A decision belongs here once it is settled. Anything still in motion lives in
  [OPEN-QUESTIONS.md](./OPEN-QUESTIONS.md).
- `pre-2026-08-23` means the decision came out of brainstorming and red-teaming that
  happened before the current build phase.

---

## A. Audience, format, objective

### D-01 · Audience is mixed technical + management
**Decided** pre-2026-08-23 · **Status** Active · **Refined by D-54** (the mix tilts geeks)

Engineers, architects, Agile practitioners, engineering managers, technology leaders,
business/technology managers. At a local Agile meetup.

**Why:** the traps only work if they cash out in both a code review *and* a staffing
conversation. Writing for engineers alone would gut Trap 4.

### D-02 · 45–50 min presentation, 10–15 min discussion
**Decided** pre-2026-08-23 · **Status** Active · **See** Q-01 (currently over budget)

### D-03 · Success criterion is a better question a month later
**Decided** pre-2026-08-23 · **Status** Active

> A month later, someone encounters an AI-related decision at work and one of these
> mental models causes them to stop, ask a better question, and make a better trade-off.

**Why:** this is the test every slide has to pass. It is why the deck ends on five
questions rather than five summaries, and why we keep cutting frameworks — a framework
you have to memorize fails this test.

### D-04 · Agile is integral, not decoration
**Decided** pre-2026-08-23 · **Status** Active

The Agile content is load-bearing in Trap 3 (question → try → evidence → learn) and
Trap 4 (where did the work go). It is not terminology pasted onto a generic AI talk.

**Why:** it is an Agile meetup, and the room will detect a generic AI talk instantly.

### D-05 · Slides are sparse; the rigor lives in the speaker's head and the notes
**Decided** pre-2026-08-23 · **Status** Active

Three distinct layers, deliberately kept separate:
1. what appears on screen
2. what the speaker says
3. what the speaker understands but never explains

**Why:** the sophistication should make the simple questions *defensible*, not make the
audience memorize the sophistication. Do not solve complexity by adding words to slides.

---

## B. Tone and language

### D-06 · Whiteboard voice, not conference voice
**Decided** pre-2026-08-23 · **Status** Active

Sounds like: an architecture review, a code review, a retrospective, a developer talking
to their manager, a manager talking to a VP.

**Rejected:** academic AI conference, economics lecture, governance framework, AI-safety
evangelism, AI skepticism, job preservation, "humans are better", "five reasons AI is
dangerous".

### D-07 · Banned audience-facing vocabulary
**Decided** pre-2026-08-23 · **Status** Active

Never on a slide or in the spoken track: *causal independence of validation*,
*epistemic status*, *verification economics*, *economically appropriate evidence*.
Also avoid overusing *prices* and *economics* — "cost" in ordinary engineering usage is
fine.

**Use instead:** Could this test actually catch the mistake? · How sure do we need to be?
· How bad is it if we're wrong? · Will we notice? · Can we undo it? · What got faster? ·
Where did the work go? · What did my question already decide?

**Why:** the theory can exist underneath. The audience-facing language must be direct.
The audience should leave with better questions, not more AI terminology.

### D-08 · Respect that this is existential for real people, without lying to them
**Decided** pre-2026-08-23 · **Status** Active

**Rejected:** "don't worry, you'll move up the value chain." We don't know that.
Historical transformations don't work that neatly. Some skills will become less scarce;
some roles will shrink.

**Why:** the room contains people who are genuinely frightened. False comfort loses them
and is also just wrong. The deck says plainly that we don't know, and that being wrong
about where the work went is bad for everyone in the argument.

---

## C. Philosophical spine

### D-09 · Sowell trade-offs quote opens and closes the talk
**Decided** pre-2026-08-23 · **Status** Active

> "There are no solutions. There are only trade-offs." — Thomas Sowell

**Why:** it is the worldview underneath the whole deck, not a decorative epigraph. AI
does not eliminate trade-offs; it moves them. That framing is what keeps every trap from
becoming a warning.

### D-10 · "Easier does not mean free" — but never pessimism
**Decided** pre-2026-08-23 · **Status** Active

Sometimes the correct conclusion is *use much more AI, much more aggressively*. The goal
is to re-optimize, not to preserve old systems.

**Why:** guards against the deck curdling into "everything has a downside."

### D-11 · "Cheap candidates" is NOT the theory of everything
**Decided** pre-2026-08-23 · **Status** Active

The earlier master thesis — *AI collapsed the cost of producing candidates; establishing
whether a candidate is right is falling more slowly* — is still useful speaker
understanding, but is deliberately **not** the organizing frame.

**Why:** "candidate" gets stretched until it means everything. The broader durable idea
is simply: *AI makes many things that used to require substantial human effort
dramatically easier — so what should we do differently?*

### D-12 · Scarcity/attention is speaker understanding, not a taught framework
**Decided** pre-2026-08-23 · **Status** Active

*When something stops being scarce, stop organizing the system as though it still is.*
AI makes bad questions and irrelevant critiques cheap too. Deliberately kept off the
slides; surfaces once, spoken, in Trap 3 notes.

### D-13 · Evidence arbitrates factual claims — not seniority, not the AI
**Decided** pre-2026-08-23 · **Status** Active · Used carefully

Evidence itself requires judgment: what was measured, was the experiment representative,
what was omitted, what generalizes. Expertise still matters enormously.

**Rejected:** "evidence eliminates hierarchy." Modern science created new and deeper
hierarchies. A junior with AI can still be spectacularly wrong. Do not romanticize
flattened hierarchy.

---

## D. Structure

### D-14 · The five traps are a progression, never explained as one
**Decided** pre-2026-08-23 · **Status** Active

1. challenge the answer
2. challenge the framing/question
3. challenge our own understanding/use of AI
4. challenge what we do with the capacity AI creates
5. challenge how authority scales into real-world consequences

**Why:** it makes the narrative feel inevitable rather than like a listicle. Explaining
the taxonomy out loud would turn it into one more thing to memorize — see D-03.

### D-15 · Every trap must leave the audience wanting to use AI *better*
**Decided** pre-2026-08-23 · **Status** Active

Each trap carries an explicit positive use: generate tests and critiques (T1), attack
your own framing (T2), tutor and challenge (T3), analyze delivery evidence (T4), automate
consequential work and assist oversight (T5).

**Why:** the answer to bad AI architecture is better system design and better use of AI,
not less AI.

### D-16 · Closing is five questions mapped to the five traps
**Decided** pre-2026-08-23 · **Status** Active

1. What do we actually know?
2. What did our question already decide?
3. Am I understanding faster — or avoiding understanding?
4. What got faster — and where should that capacity go?
5. What can it do when it's wrong?

Then the Sowell callback, then: *The goal isn't maximum AI. The goal is better systems.*
**Stop there.** No re-summary, no thank-you slide.

### D-17 · Hard cap on frameworks
**Decided** pre-2026-08-23 · **Status** Active

Do **not** add, unless construction exposes a genuine hole: constraint taxonomy, risk
matrix, seams framework, cognitive-offloading model, AI maturity model, new Agile
methodology, governance framework, another list of principles.

**Parked to speaker understanding only:** Goal / Hypothesis / Invariant / Implementation;
persistent intent & validation. Useful for thinking, would turn the talk into requirements
management.

---

## E. Per-trap decisions

### D-18 · Trap 1 title: "A Great Answer Doesn't Mean You're Right"
**Decided** pre-2026-08-23 · **Status** Active

**Why:** jarring, and it skips past the boring version. Everyone already knows AI
hallucinates. The interesting failure is a sophisticated, compelling answer that raises
confidence in something never established.

### D-19 · Trap 1 owns the refund-requirement example
**Decided** 2026-08-23 · **Status** Active

On screen: *"Customers who cancel mid-cycle get a prorated refund."* → AI implementation →
AI tests → `47 passing · 0 failing` → both came from the same reading of that sentence →
finance meant unused *whole days*, and the setup fee is never refundable.

**Why:** Trap 1 previously had **no** on-screen example of its own point — it borrowed the
services/Kafka architecture, which is Trap 2's. That is the "traps collapsing together"
failure mode happening literally on screen. The refund domain also threads forward into
D-24 (`refundAmount <= amountPaid`) and Trap 5 ("issue the refund"), giving the deck one
concrete world instead of three.

**The problem is not "AI wrote the tests."** The problem is that the check repeated the
mistake. Keep saying this out loud — the anti-AI misreading is one click away.

### D-20 · Trap 2 title: "AI Can Solve the Wrong Problem Really Well"
**Decided** pre-2026-08-23 · **Status** Active

**Supersedes:** "Starting with AI instead of the problem."

**Why:** "start with the problem" is true and banal, and the room has heard it a hundred
times. The real insight is that *a question can quietly contain important decisions before
the AI ever answers it.* Get to "What did my question already decide?" fast.

### D-21 · Trap 2 owns the services/Kafka architecture, and it must be genuinely good
**Decided** pre-2026-08-23, re-sited 2026-08-23 · **Status** Superseded by D-44 on 2026-08-25

Build the outbox → Kafka → idempotent consumer design up over five clicks, explicitly
bless it, *then* reveal "Why are these two services?" and gray the whole diagram out.

**Why:** the rhetorical force depends on the audience nodding along first. Also state
plainly: CAP didn't change; the boundary may be completely justified (independent
scaling, ownership, deployment, failure isolation) — **it should win the argument, not
skip it.**

### D-44 · Trap 2's on-screen example is the refund approval chain, not the architecture
**Decided** 2026-08-25 · **Status** Active · **Supersedes** D-21

On screen: *"How do we speed up refund approvals?"* over the chain
`Refund request → Agent → Supervisor → Finance → Refunded`. AI's answer builds up —
route by amount and risk score, run the three approvals **in parallel rather than in
sequence**, reminders at four hours, escalation at twenty-four, an exception queue, a
dashboard. It is explicitly blessed on screen: *"Cycle time genuinely drops. This is a
good answer."* Then the whole thing grays out under:

> **Why does a $12 refund need three approvals?**

**Why the swap.** The slide's mechanic requires the audience to be *genuinely impressed
by the answer before the reveal.* Transactional outbox, Kafka and idempotent consumers
are outside the working experience of much of a mixed audience (D-01) — managers and
business technologists watch jargon go past, cannot be impressed, and the reveal lands on
nothing. Legibility is not a nicety here; it is a precondition for the trap to function.

**Why this example specifically:**
- Everyone in the room has personally suffered an approval chain. No setup required.
- The AI answer is legibly *good* — "run them in parallel instead of in sequence" is a
  real, non-obvious improvement that engineers respect and managers immediately grasp.
- The hidden premise is a **policy** silently treated as a constraint, which is a cleaner
  instance of D-20 than an architecture boundary is.
- The dollar amount is withheld until the reveal. The question never mentioned amounts and
  neither did the answer — that *is* the trap, precisely.
- It threads the deck's single domain: the refund from Trap 1 (D-19), the approvals here,
  and "issue the refund" at the top of Trap 5's authority ladder (D-33). One story, three
  different ways to be wrong.

**Keep the architecture version as exactly one spoken sentence** for the engineers,
immediately after the reveal — the two services that didn't have to be two services, CAP
didn't change, the boundary was a design choice. It is in the speaker notes and must not
grow back into a slide.

**Say out loud that the approvals may be justified** — fraud, auditors, segregation of
duties are real controls. The point is that the policy should *win* the argument, and that
nobody has re-run it since it was written.

### D-45 · The approval diagram must *perform* the change, and the reveal names who
**Note:** the *reveal* half of this decision is **superseded by D-49**. The restack on
click 2 stands unchanged; what click 4 exposes has moved from "which approvers are
unnecessary" to "the order was the control."
**Decided** 2026-08-25 · **Status** Active · **Extends** D-44

Two things the first version of this slide got wrong:

**1. The picture has to show why parallel is faster.** Originally the chain sat still while
a bullet *claimed* "run the three approvals in parallel." On click 2 the three approvers
now physically restack from a sequential row into a parallel fork/join between the request
and the refund. The audience sees the change rather than being told about it.

This one is on principle, not polish: a bullet asserting an improvement is exactly the
"sophisticated answer that never established the premise" the talk is about. The slide
should not commit its own Trap 1.

**2. The reveal has to say *which* approvals.** "Why three approvals" is vague on its own.
At the reveal, Supervisor and Finance turn orange while Agent stays neutral — because at
twelve dollars those two are not a control, they are reviewing a decision that was always
entirely inside the agent's authority. The optimization made two unnecessary approvals
faster, in parallel, with a dashboard.

Also: the three approvers are labeled `THREE APPROVALS` on screen and named out loud —
"the agent who takes the call, their supervisor, somebody in finance." Without that the
chain reads as a pipeline rather than as three separate people saying yes.

**The blessing line is spoken, not shown.** *"Cycle time genuinely drops, this is a good
answer"* was on the slide and is now in the speaker's mouth — it belongs there (D-05), and
removing it bought the vertical space the parallel stack needed.

### D-22 · Trap 2 also carries the greenfield version
**Decided** pre-2026-08-23 · **Status** Active

*"How should we build our AI customer-service agent?"* already decided **agent**. Reframe
to the business problem (18 minutes → under five), fan out the real option space, then:
maybe the agent still wins — now it *won* instead of being assumed.

**Why:** prevents Trap 2 from reading as a legacy-systems or anti-microservices complaint.

### D-23 · Inference vs enforcement lives inside Trap 2, one slide
**Decided** pre-2026-08-23, implemented 2026-08-23 · **Status** Active

`refundAmount <= amountPaid` is cheap to state and cheap to check — never ask a model
whether it "seems reasonable." *"Does this PR fit the conventions of a 15-year-old
codebase?"* involves hundreds of real conventions nobody wrote down; inference plus
inspection is a good trade.

*Infer what you must. Enforce what you can.* — **not** an absolute. Enforcement costs
rigidity, false rejections, maintenance, slower experimentation.

**Why one slide:** it is a genuine trade-off worth naming, and it is exactly the kind of
thing that would metastasize into a framework (D-17) if given room.

### D-24 · Prompt injection lives inside Trap 2, one slide, as a *framing* problem
**Decided** pre-2026-08-23, implemented 2026-08-23 · **Status** Active

The payoff is: *"How do we stop it being tricked?" already put the defense inside the
model* — the one place we can't fully enforce it. Reframe to: **what can it do if it IS
tricked?** Which hands off to Trap 5.

**Constraints, all deliberate:**
- SQL injection is an *analogy* about trust boundaries, **not** the same vulnerability.
- Do **not** claim injection is unsolved in every sense, or that there are no mitigations.
- Do **not** imply authorization "solves" prompt injection. It bounds what a successful
  injection is *worth* — a blast-radius argument.
- *A prompt is not a security boundary.*
- Do not let this become a security tutorial.

### D-25 · Trap 3 title: "Are You Understanding Faster — or Avoiding Understanding?"
**Decided** pre-2026-08-23 · **Status** Active

**Why:** deliberately uncomfortable, and the speaker admits to doing the second one.

### D-26 · Trap 3 must not become "engineers must understand everything"
**Decided** pre-2026-08-23 · **Status** Active

Cognitive offloading is a *feature* — machine code → compiler → framework → cloud → AI.
The danger is the quiet slide from "I don't need to do this myself" to "I don't need to
understand this."

The honest requirement: *you need enough understanding to recognize where the seams are —
and which ones matter.* "Seams" is speaker vocabulary; it must never become a slide
taxonomy (D-17).

### D-27 · Trap 3's spine is familiarity, not seniority
**Decided** pre-2026-08-23 · **Status** Active

When unfamiliar: **"Help me understand this."** When you think you know:
**"Challenge my understanding."** Most people are in both states in the same week.

**Why:** the junior/senior framing is wrong and also flatters the room. The second mode is
the underrated one and is most valuable to the *most* experienced people, because
experience is compressed pattern recognition — which is exactly the mechanism that
decides "I've seen this before" and stops looking.

### D-28 · Trap 3 on juniors and seniors — no comforting version of either
**Decided** pre-2026-08-23 · **Status** Active

- Some traditional junior work genuinely is getting less valuable. Do not preserve
  obsolete work because previous generations learned through it. Distinguish *juniors
  producing junior artifacts* from *engineers developing judgment*.
- **Rejected:** "AI writes code; seniors provide judgment." AI will increasingly
  participate in judgment too.
- Instead: *offload implementation effort without disconnecting from implementation
  evidence.* Detached seniors recreate the ivory-tower architect.

### D-29 · Trap 3's Agile loop, with its qualification attached
**Decided** pre-2026-08-23 · **Status** Active

*When reality can answer the question cheaply, stop arguing and ask reality.*
Immediately followed by: *test what reality can cheaply answer; use judgment for what it
can't.* You cannot prototype what maintaining six services across four teams for eight
years feels like.

**Also:** if someone says "you rediscovered Agile" — say yes, out loud, from the stage.
AI makes the original Agile argument *stronger*, because every objection to running the
experiment used to be about cost.

### D-30 · Trap 4 title: "Faster Doesn't Mean You Should Do More"
**Decided** pre-2026-08-23 · **Status** Active

**Must be verbally qualified the instant it appears:** *"And sometimes more is exactly
what you should do."* Otherwise it reads as anti-productivity and half the room leaves.

### D-31 · Trap 4 puts the frightening management question on screen verbatim
**Decided** pre-2026-08-23 · **Status** Active

> "If developers are 2× as productive, why do we need this many developers?"

**Rejected answer:** "Because somebody has to check the AI." Weak, defensive, and
increasingly false.

**Instead:** model two credible conversations (engineer→manager, manager→VP) that ask to
*measure* what disappeared and where work moved. And if the evidence says the same
outcome genuinely needs substantially less engineering labor — say that that is real.
The purpose is not preserving jobs; it is understanding the system.

### D-32 · Trap 4 is constraint relocation, not Theory of Constraints
**Decided** pre-2026-08-23 · **Status** Active

Idea → Design → **Code** → Review → Integrate → Deploy → Customer. The AI-specific
intensifier: capacity can change enormously and almost overnight, and the outputs *look
like completed intellectual work.*

### D-33 · Trap 5 is about authority, not correctness
**Decided** pre-2026-08-23 · **Status** Active

Read email → draft → send → update record → issue refund. Same model, same inference,
same error rate. What changed is **authority**.

Do **not** ask "where should the human enter the loop" — that is the governance answer and
the wrong question. Ask: *at what point did the architecture fundamentally change?*

Do **not** base any of it on human intellectual superiority. An organization may
legitimately decide AI should autonomously do all of these.

### D-34 · Trap 5's core question and its three follow-ups
**Decided** pre-2026-08-23 · **Status** Active

**What can it do when it's wrong?** → How bad is it? · Will we notice? · Can we undo it?

*For AI systems, "nothing threw an exception" is an especially weak definition of
success.* Traditional monitoring catches loud failure; AI failure looks like the
operation completing successfully and doing the wrong thing.

### D-35 · Oversight does not scale automatically — 10,000 / 100 / which 100?
**Decided** pre-2026-08-23 · **Status** Active

"Keep a human in the loop" is not an answer. A human clicking Approve 2,000 times is a
signature, not supervision.

Mechanisms (enforceable authorization, least privilege, automated checks, sampling,
anomaly detection, outcome monitoring, traceability, escalation, stop mechanisms) are
**spoken, never listed on a slide** (D-17). AI can perform much of this oversight itself —
the point is not humans supervising machines, it is designing accountability that scales
with authority.

### D-36 · Controls have trade-offs too — a qualification, never a sixth trap
**Decided** pre-2026-08-23 · **Status** Active

Controls cost attention, latency, flexibility, engineering effort, operational
complexity, customer experience. *"Yeah, that might break. We're okay with that"* is a
legitimate engineering conclusion. Do not spend $10 proving a 10-cent experiment correct.

**Why:** do not replace AI maximalism with governance maximalism.

### D-37 · Trap 5 title (provisional): "When AI Gets It Wrong, What Is It Allowed To Do?"
**Decided** 2026-08-23 · **Status** Provisional · **See** Q-04

**Why this one:** least clever of the candidates, states the actual question, and sets up
closing question #5 verbatim.

**Other candidates:** *AI Can Scale Faster Than Your Ability to Supervise It* · *What
Happens When AI Stops Asking Permission?* · *Who Gave the AI Permission to Do That?*

---

## F. Visual and implementation decisions

### D-38 · Slidev, `apple-basic` theme, plus deck-specific CSS
**Decided** pre-2026-08-23 (theme), 2026-08-23 (CSS) · **Status** Active

The theme alone was not enough — it renders everything as small top-left text, which
destroys a deck built on large provocative statements. `styles/index.css` supplies the
actual visual language.

### D-39 · Two semantic colors, never decorative
**Decided** 2026-08-23 · **Status** Active

- **Orange `--trap` `#c2410c`** — the mistake, the thing that bites you
- **Teal `--good` `#0e7490`** — the better question, the evidence

If a color appears without carrying one of those meanings, remove it. Two-column
comparison slides (infer/enforce, help/challenge) deliberately use **neutral** headings,
because both columns are valid choices — not a right and a wrong one.

### D-40 · Recurring slide surfaces so the room learns the vocabulary
**Decided** 2026-08-23 · **Status** Active

- `cover-slide`, `pull-quote` — dark, open and close
- `trap-slide` — dark ground, orange rule, `### TRAP 0N` eyebrow. A hard act break
- `q-slide` — teal left rule. **Always** means "here is a question for Monday"
- `statement-slide` — one big line, nothing else
- `canvas-slide` — the content is a diagram, not a headline
- `fact-slide` — big numbers

**Why:** by Trap 2 the audience recognizes the teal bar without being told. The five
closing questions then land as a callback rather than a summary.

### D-41 · Diagrams are CSS boxes and rules — no clip art, no ASCII
**Decided** 2026-08-23 · **Status** Active

**Rejected:** robots, glowing brains, circuit boards, neon gradients, stock-photo
futurism. Also rejected: ASCII diagrams in `<pre>` — they read as terminal output and
don't animate with reveals.

### D-42 · Progressive reveal via `v-click`, not duplicated slides
**Decided** 2026-08-23 · **Status** Active

**Supersedes:** the customer-service ladder as five near-identical slides, and the five
closing questions as five slides. Both are now single slides with click reveals.

**Why:** duplicated slides break navigation, presenter view, and the timing tally.
Hidden clicks keep their layout space, so nothing shifts as reveals land.

Reveals that are load-bearing and must not be flattened:
- Trap 1 — the green build flips from teal to **orange** on the final reveal
- Trap 2 — the architecture grays out as "Why are these two services?" lands beneath it
  (the figure is now 30%, not 16% — D-46)
- Trap 4 — `−8% idea to production` gets its **own** beat after the other three metrics,
  rendered neutral (not teal), because it is the punchline, not a win
- Trap 5 — the authority ladder escalates in color, one rung per click

### D-43 · `colorSchema: light`, Inter + JetBrains Mono
**Decided** 2026-08-23 · **Status** Active

Light is forced so there is exactly one design to maintain and one thing to test on an
unknown projector.

---


### D-46 · The Trap 2 gray-out dims to 30%, not 16%
**Decided** 2026-08-25 · **Status** Active
**Supersedes:** the `16%` figure recorded in D-42's load-bearing-reveals list.

`.dimmable.dimmed` is now `opacity: 0.30` (plus `grayscale(1)`), up from `0.16`.

**Why:** the venue is unknown (Q-05), so the deck must assume the worst — a projector in
a lit room. The reveal only works if the audience can still see the *ghost* of the
architecture they just approved sitting underneath the question. At 16% on washed-out
hardware it vanishes, and a vanished diagram reads as a slide malfunction rather than a
gut-punch (R-05). Verified in the browser at slide 9, click 4: the chain and the three
bullets recede without disappearing, and Supervisor + Finance still pop orange against
them.

**Rejected:** redesigning the slide for high-contrast hardware. A one-value change buys
the insurance; the design is right.

### D-47 · 45–50 minutes is a target with roughly 10 minutes of slack, not a hard cap
**Decided** 2026-08-25 · **Status** Active

The organizers have not imposed a hard stop. Running to ~55 is survivable.

**Why it matters:** it halves the cut. Q-01's recommendation assumed a hard cap and
listed ~6 minutes across four cuts. Against a soft target the cut is **~3 minutes, taken
entirely from Trap 3** — and taken because Trap 3 is a junk drawer (R-01), not because
the clock demands it. The Sowell callback, the attack-your-framing prompt slide, and
Trap 4's capacity/2× pair are **no longer on the cut list** and should be judged on
quality alone.

**Consequence for Q-08 and Q-09:** both now fit without displacing anything. Q-08's one
spoken sentence on the *"Could this check catch the original mistake?"* slide and Q-09's
single naming of steel-man/red-team in Trap 3 are affordable. They still have to earn
their place, but they no longer compete with the trim.

**Still true:** note-time is systematically optimistic, and no number has been rehearsed
(R-09). The slack is insurance against that, not budget to spend.

### D-48 · Trap 4's metrics stay invented, and the speaker says so out loud
**Decided** 2026-08-25 · **Status** Active

No real organizational data exists. `−60% coding time · +80% PRs · +110% review wait ·
−8% idea to production` remain as written, with the spoken disclaimer intact.

**Why:** the *shape* of the claim is the point — three metrics improve, the one that
matters doesn't. Inventing numbers while announcing you invented them is honest.
Quietly presenting invented numbers as observed would be the exact Trap 1 failure this
talk warns about.

**This makes R-06 load-bearing.** The disclaimer is now the only thing standing between
this talk and a manufactured statistic being quoted back as real. It must not be dropped
under time pressure, and it must arrive in the same breath as the numbers — not after
the audience has had a beat to believe them.

**Rejected:** sourcing public industry figures instead. They would carry the same
citation burden, invite a fight about methodology, and cost minutes on a detour away
from the argument.

### D-49 · Trap 2's reveal is the deleted escalation chain, not the $12 policy
**Decided** 2026-08-25 · **Status** Active
**Supersedes:** the reveal half of D-45 (orange on Supervisor + Finance; the on-screen
question *"Why does a $12 refund need three approvals?"*).
**Resolves:** R-11.

Click 4 now asks **"Why were they in that order?"** Everything dims to 30% except the
three approvers, and the two sequence arrows — deleted by the parallel restack on click
2 — **come back, in orange, running down the stack.** No approver turns orange.

**Why the old reveal failed.** A *sequential* three-approval chain for a $12 refund is
not a hidden assumption; it is the most complained-about thing in the building. Agents
feel it on every call. It would surface within weeks of rollout, not years. So the room's
honest reaction to *"why does a $12 refund need three approvals?"* is **"we know"** — and
Trap 2 requires the assumed decision to be genuinely unexamined. The old note's line
*"Nobody had thought of that"* could not survive the objection.

**Why the new reveal works.** In sequence, the supervisor reviews *the agent's decision*
and finance reviews *the supervisor's*. The order is not latency — the order **is** the
control. It encodes escalation. Parallelising silently deletes it: three independent
opinions on the raw request, nobody reviewing anybody. The diagram looks equivalent; the
governance is not. **Nobody complains, because nobody can see it** — which is exactly the
invisibility Trap 2 needs.

It also promotes the click-2 restack from a clever win to **the crime itself**, performed
on screen while the room nods along. That reveal was already built and verified.

**The $12 question survives as a spoken second beat**, and its notoriety becomes the
point: one question the organization has asked a thousand times and never had authority
to act on, one nobody has ever asked. The typed prompt — *"how do we speed up refund
approvals"* — invited neither.

**The R-02 tension, handled deliberately.** Losing escalation semantics is the answer
being *wrong*, which sounds like Trap 1. The Trap 2 reading is carried by the **question**:
"speed up approvals" treats a review hierarchy as three units of latency. Approvals-as-queue
is the hidden decision, and nobody typed it. This must be said explicitly or the two traps
re-blur.

**Rejected:** a fifth click for the escalation loss (Trap 2 is already the longest block);
swapping the example out entirely (any replacement inherits the same challenge, and
D-44/D-45's build is verified); making rubber-stamping its own beat — it is one spoken
sentence, flagged in the note as a different talk.

**Cost:** the slide's note goes ~2:45 → ~3:15. Affordable under D-47.


### D-50 · The chain is an escalation chain, and the reveal pays off in workload
**Decided** 2026-08-25 · **Status** Active
**Extends:** D-49. **Fixes:** a contradiction present since D-44.

Three linked changes to slide 9, all raised by the speaker during construction.

**1 · The chain is an escalation chain, not three mandatory sign-offs.**
The agent handles the refund; the supervisor sees what the agent escalates; finance sees
what the supervisor escalates. Each level reviews the level beneath it **and sees a
fraction of what it saw**.

This had been straddled. D-49's reveal used escalation semantics ("each level reviewing
the level beneath it") while the diagram's `THREE APPROVALS` label said mandatory
sign-off. Committing to escalation is strictly better: the label becomes **load-bearing
irony** — it is the organization's own wrong summary of its own process, and it is what
got typed into the prompt. AI optimized the *description*, not the process.

**2 · A fifth click: the workload consequence.**
An annotation appears right of the chain — *A WEEK LATER · Supervisor and Finance are
drowning.* Deleting an escalation chain removes the **filter** as well as the control:
those two used to see the exceptions, now they see every refund.

This is the proof, and it is what makes the deleted control detectable at all. The
crucial beat is how the complaint arrives: *"we don't have enough people."* It gets filed
as a **capacity problem** — answered with headcount, a triage filter, or somebody
suggesting AI triage the queue. Nobody says the word "control." The dashboard stays green,
because cycle time was the metric.

**Reverses D-49's rejection of a fifth click.** New information: the consequence is the
strongest beat on the deck's best slide and cannot be carried by speech alone.

**3 · The `$12` beat is cut entirely.**
It was self-contradicting: click 1 (*"route by amount and risk score"*) already sends a
$12 refund straight through, so the slide's own first suggestion answered the question the
reveal was saving. Under escalation semantics it is doubly dead — a $12 refund never left
the agent in the first place. Cutting it also disposes of R-11's notorious-vs-hidden
problem completely rather than managing it.

**What click 1 now means.** AI reconstructing a threshold policy from the two variables
visible in the data — amount and risk. Plausible, and a guess at a policy whose reasons
were never recorded. Set up lightly at click 1, paid off at the reveal.

**The mechanism, now stated explicitly — this is Trap 2's actual point.**
The reason for the order was never written down. Not in the code, not in the ticket, not
on the wiki (the wiki says "three approvals"). It was in the head of whoever set the
thresholds, probably after something went wrong, and they left. **AI cannot ask about a
constraint nobody recorded — and neither can a new architect, a new dev team, or you in
your first week.** This generalizes the trap beyond AI, which also blunts the
"engineers rationalizing their salaries" objection: AI did not create this failure, it
made it fast.

**Cost:** ~3:15 → ~3:30; deck at 50:00. Affordable under D-47, and the $12 cut pays part
of it back.

**Rejected:** turning Supervisor and Finance orange at click 5 — the arrows already carry
orange and a second focus makes the frame busy; the annotation points at them instead.

**Build note:** `.load-note` is absolutely positioned. In normal flow its hidden state
still reserved width and wrapped "Refund request" onto two lines at *every* click state —
a variant of the reveal-verification rule in `RESTART.md`: a hidden element can damage
the slide you are not looking at.


### D-51 · Coherency of the examples comes before the timing trim
**Decided** 2026-08-25 · **Status** Active

The working order is now: get the examples and the narrative move through the deck right,
*then* cut to time. Trimming is mechanical; perfecting what is said is not.

**Why:** the last two sessions found two example-level defects that no amount of trimming
would have surfaced — the notorious-vs-hidden inversion (D-49) and the `$12` beat being
self-contradicted by click 1 (D-50). Both were found by reasoning about the example, not
the clock. Cutting first would have preserved the defects in a shorter deck.

**Consequence:** Q-01 stops being a gate. The timing tally is still recomputed after every
content change and still reported, but a number over budget no longer blocks work. The
cut happens once, near the end, against a stable deck.

**This supersedes the "Bias to cutting" instruction in `RESTART.md`** for the current
phase, and `RESTART.md` has been updated to say so.

### D-52 · No slide declares `clicks:` in frontmatter unless it exceeds its `v-click` count
**Decided** 2026-08-25 · **Status** Active

Removed `clicks:` from slides 15, 23, 25 and 27. Slidev auto-counts registered `v-click`
elements, which is always the correct number when every beat is backed by an element.

**The bug this fixes — the mirror of the trap already in `RESTART.md`.** That trap is
*too few* registered elements silently capping a slide. This is the opposite: `clicks:`
declaring *more* clicks than there are elements creates **dead presses** at the end of a
slide. Live, that is the speaker pressing forward, nothing happening, and pressing again.
Found on four slides, including the **Trap 5 authority ladder** — one of the three slides
the talk is built on, and the one that most depends on rhythm.

| Slide | Declared | Real beats | Dead |
|---|---|---|---|
| 15 · prompt injection | 4 | 2 | 2 |
| 23 · pipeline metrics | 4 | 3 | 1 |
| 25 · authority ladder | 5 | 4 | 1 |
| 27 · 10,000 decisions | 3 | 2 | 1 |

**Why removal rather than correction:** a corrected number drifts the moment a beat is
added or removed, and the mismatch is invisible in the source. Absence cannot drift.

**Kept:** slides 5 and 28, where the declared count matches the element count exactly.
Neither is load-bearing; they can go too if they ever disagree.


### D-53 · The escalation must be VISIBLE before the reveal — volumes on the diagram
**Decided** 2026-08-25 · **Status** Active
**Extends:** D-49, D-50.

Each approver carries a weekly volume: **Agent 2,000 · Supervisor 200 · Finance 20** in
sequence. On the click-2 restack **all three become 2,000**, in neutral gray, unremarked.
They turn orange at click 4 with the returning arrows.

**The defect this fixes — and it was the real reason the slide felt unclear.** The diagram
drew a *pipeline*: every request flowing through all three boxes. That is exactly what
"three approvals" means. Then at click 4 the speaker asserted it had been an escalation
chain all along. **The audience could not verify that from anything they had seen** — they
had to accept that the picture meant something other than what it drew.

Compare Trap 1, which works because you *watch* green flip to orange. Nothing is asserted
there. Trap 2 was asking the room to take the reveal on trust, and trust is precisely what
this talk is about not extending.

**With volumes on screen the slide inverts:** the catastrophe happens visibly, at click 2,
in the same instant the room is being told the optimization is clever. The evidence is
present from the first frame, delivered in a bored voice as scene-setting, and ignored.

That yields the line the slide had been missing:

> It was on the screen the whole time. We were watching the cycle time.

**Deliberate risk accepted:** an alert audience member may catch it at click 2, before the
reveal. That is the **best** outcome, not a failure — the note tells the speaker to say
"hold that" and continue. A reveal that some of the room beats you to is stronger than one
nobody could have seen coming, and it protects D-44's requirement that the room be
impressed before it is caught.

**Also strengthens the mechanism.** It is now explicit that the *information* was never
missing — the volumes were readable, and AI could have read them. What was missing was the
**rationale**. This lets Trap 1 and Trap 2 be distinguished in one line, resolving R-14:

> A missing rule makes the answer wrong. A missing rationale makes the question
> unchallengeable.

**Numbers are deliberately round** (2,000 / 200 / 20) so they read as structural
illustration, not measurement. This is not the R-06 / D-48 situation: nobody will quote a
diagram's decimal funnel as industry data.

**Build note:** the volume labels widened every box, which reintroduced the base-state
wrap on "Refund request" and then overran the frame entirely. Fixed with `flex: none`,
`white-space: nowrap`, and smaller type inside `.chain`. Caught by the base-state check
added to `RESTART.md` in the previous commit — on its first use.


### D-54 · The room tilts geeks, and the humor register is in-group and slightly blue
**Decided** 2026-08-25 · **Status** Active
**Refines:** D-01. Does **not** supersede it — the room is still mixed, just weighted.

**Audience.** Speaker's read of the actual room: still mixed (D-01 stands — Trap 4 needs
the management half), but **weighted toward engineers**. Content pitched at the technical
half will mostly land; content requiring management context still needs its scaffolding.

**Register.** Mildly risqué, in-group technical humor — *"nerdgasm"*, *"hot and bothered"*
about an architecture, *"long-distance relationship"* for a service boundary — is
**extremely effective at drawing both the laugh and the memory** with this room. It is
also easy to overuse, and the speaker has flagged that himself.

**The working rule that makes it safe — the target is always our own appetite for
complexity, never a person or a group.** *"We get hot and bothered about an outbox
pattern"* is solidarity: the speaker is inside the joke and so is the room. The same
energy aimed at a role — architects, PMs, the finance team — becomes contempt and costs
the room instantly. Every laugh in this deck should be self-implicating, which is already
the deck's established voice (*"I would have said yes"*, *"I have caught myself doing the
second one"*).

**Budget: three laughs, not a set.** The design intent is a principal engineer at a
whiteboard (see `styles/index.css`), not a comedy set. Current plan:
1. **Trap 2** — the Kafka buffet, *after* the refund reveal has done the work. Deferred
   until the R-12/R-13 restructure so Trap 2's minutes get allocated once.
2. **Trap 4** — wants one badly; it is the most likely hostile-question moment (R-07) and
   a laugh defuses a room better than an argument does.
3. Reserve. Do not spend it just because a spot exists.

**Trap 5's ladder stays cold** — deliberately unfunny. The escalation is doing the work
and a laugh would release exactly the tension the slide is building.

**This does NOT reopen D-44.** D-44 rejected the Kafka/outbox architecture as Trap 2's
on-screen example partly on mixed-audience grounds, which this weakens — but the refund
escalation chain has since become far stronger on its own merits (D-49, D-50, D-53). It
now wins on quality, not on accessibility. Kafka returns as the *laugh*, not the example.

**Raises the stakes on Q-05 (is it recorded?).** A register that works in a room among
peers travels differently as a clip. If the talk is recorded, this needs a second look —
not necessarily a change, but a deliberate decision rather than a default.


### D-55 · The prompt-injection slide moves into Trap 5, between the ladder and its question
**Decided** 2026-08-25 · **Status** Active
**Resolves:** R-13. **Partially resolves:** R-12, R-16.

Slide order is now `23 TRAP 05 · 24 ladder · 25 prompt injection · 26 "What can it do when
it's wrong?"`. Trap 2 drops to six slides / 12:45; Trap 5 rises to five / 8:30.

**Why it had to leave Trap 2.** Its payload was *"the reframe is: what can it DO if it IS
tricked?"* — slide 26's title, verbatim — and its note then said out loud that this is
where the talk ends up. **The deck announced its own ending fifteen minutes early**, and
whatever force Trap 5's central question had on arrival was already spent.

**Why Trap 5 is where it belongs, not merely where it does least harm.** The ladder's
first rung is *"Read the customer's email."* Prompt injection is what happens when that
email is hostile. The two slides now compose into one argument the deck could not make
before:

> Rung one is an input we do not control. Rung five is issuing a refund.

That is Trap 5 in a sentence, and it exists only because of the adjacency. The slide is no
longer a passenger arguing for its seat — it is the reason the ladder is dangerous.

**The Trap 2 callback survives and improves.** *"How do we stop it being tricked"* still
put the defense inside the model, and the note still names that as a framing failure — but
now as **Trap 2 turning up again in a security review**, which is reinforcement rather
than a spoiler, because Trap 2 already happened.

**Also in this pass:**
- **Slide 14 (infer/enforce) inherits the handoff into Trap 3**, which the injection slide
  used to carry, and slide 24 gains a one-line handoff into the injection slide.
- **R-16 fixed.** Slide 12's option list no longer restates slide 9's approval point; the
  18 minutes is now spent hunting three systems for order history. The note explains why:
  slide 9 was a question that assumed a **policy**, slide 12 is a question that assumed a
  **solution**, and repeating an approval story collapses the distinction.
- **The Kafka buffet lands** (D-54), replacing the one-sentence engineers' aside on slide
  9. ~45s, after the reveal has done its work, ending on *"nobody asked why these two
  services need a long-distance relationship."* The self-implication rule is written into
  the note so it cannot drift into contempt.

**Still open from R-12: slide 14 (infer/enforce) remains a passenger.** Its note still has
to argue that it belongs. Deliberately NOT moved in this pass — Trap 5 is now at 8:30 and
adding it would just relocate the junk drawer. Recommendation is to cut it on quality
grounds, not move it; recorded as R-18.

**Cost:** deck 50:00 → 50:45, all of it the Kafka bit. Trap 2 is no longer the longest
block.

---

## G. Rejected — do not reopen without new information

| Idea | Why it was rejected |
|---|---|
| "Cheap candidates" as the master theory | "Candidate" stretches until it means everything (D-11) |
| "Starting with AI instead of the problem" as Trap 2 | True but banal; the room has heard it (D-20) |
| "AI writes code; seniors provide judgment" | Comforting and false — AI participates in judgment (D-28) |
| "Because somebody has to check the AI" | Weak, defensive, increasingly untrue (D-31) |
| "You'll move up the value chain" | We don't know that; transformations aren't that neat (D-08) |
| Arguments from human intellectual superiority | Loses to better models; the argument is about consequences (D-33) |
| Any new framework, taxonomy, matrix or maturity model | The deck already has enough conceptual load (D-17) |
| Academic vocabulary (*epistemic status*, *verification economics*, …) | Wrong room, wrong register (D-07) |
| "Where should the human enter the loop?" as Trap 5's question | It's the governance answer; authority is the real variable (D-33) |
| Explaining the five-trap progression to the audience | Turns a natural narrative into homework (D-14) |
| ASCII diagrams; stock AI imagery | Reads as terminal output / generic AI talk (D-41) |
| Sourcing public industry figures for Trap 4 instead of invented ones | Same citation burden, invites a methodology fight, costs minutes on a detour (D-48) |
| The `$12` question anywhere in Trap 2, on screen or spoken | Self-contradicting: click 1 routes by amount, so the slide already answers it (D-50) |
| "Why does a $12 refund need three approvals?" as Trap 2's on-screen reveal | The room already knows; a sequential chain is notorious, not hidden, so the reveal inverts (D-49) |
| Outbox/Kafka architecture as Trap 2's on-screen example | Outside the experience of much of a mixed audience; the reveal only works if the room can be impressed by the answer first (D-44) |
