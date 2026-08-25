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
**Decided** pre-2026-08-23 · **Status** Active

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
bless it, *then* reveal "Why are these two services?" and grey the whole diagram out.

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
good answer."* Then the whole thing greys out under:

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
- Trap 2 — the architecture greys to 16% as "Why are these two services?" lands beneath it
- Trap 4 — `−8% idea to production` gets its **own** beat after the other three metrics,
  rendered neutral (not teal), because it is the punchline, not a win
- Trap 5 — the authority ladder escalates in color, one rung per click

### D-43 · `colorSchema: light`, Inter + JetBrains Mono
**Decided** 2026-08-23 · **Status** Active

Light is forced so there is exactly one design to maintain and one thing to test on an
unknown projector.

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
| Outbox/Kafka architecture as Trap 2's on-screen example | Outside the experience of much of a mixed audience; the reveal only works if the room can be impressed by the answer first (D-44) |
