---
theme: default
title: "The Five Biggest AI Transformation Traps: Do This, Not That"
info: |
  A practical talk about making better engineering and business decisions
  as AI changes what is easy, fast, and worth our attention.
---

# The Five Biggest AI Transformation Traps

## Do This, Not That

Jim Moore

<!--
~0:30

This isn't a talk about today's best model, coding assistant, agent framework,
or prompt technique.

It's about mistakes we're making as AI changes how we build systems
and run technology organizations.
-->

---

# "There are no solutions.<br>There are only trade-offs."

— Thomas Sowell

<!--
~2:00

This is the lens for the entire talk.

Engineering has always been trade-offs:

- consistency vs availability
- flexibility vs control
- speed vs certainty
- build vs buy
- simplicity vs generality

There is no architecture with only advantages.

AI doesn't change that.

But it IS changing the trade-offs we've spent our careers learning how to make.

And it's changing them fast.
-->

---

# AI is making hard things easy.

<div class="text-2xl mt-12">

Code.  
Designs.  
Explanations.  
Alternatives.  
Analysis.  
Experiments.  
Critiques.

</div>

<!--
~2:00

Things that used to take hours or days can now take minutes.

That's fantastic.

And the point is NOT that "cheap" or "easy" means bad.

If something becomes dramatically easier, we SHOULD take advantage of it.

But it also means decisions that made perfect sense five years ago may deserve
another look.

The interesting question isn't simply:

"How much can AI do?"

It's:

"What did AI just make dramatically easier — and what should we do differently
because of that?"

Transition:

One of the first things it made incredibly easy is getting a really good answer.
-->

---

# Trap #1

# A Great Answer Doesn't Mean You're Right

<!--
~0:30

Let this land.

Everyone here knows AI can hallucinate.

That's actually the boring version of this problem.
-->

---

# "How should these two services<br>maintain consistency?"

<div class="mt-12 text-xl opacity-80">

Transactional outbox  
→ Kafka  
→ idempotent consumer  
→ retries  
→ reconciliation

</div>

<!--
~2:30

AI can give you an excellent architecture here.

Maybe it explains failure modes correctly.

Maybe the implementation is excellent.

Maybe all the tests pass.

But there are TWO ways we can still be wrong.

First: is any of this actually correct?

Don't confuse an articulate explanation with evidence.

Plausibility is useful. It isn't proof.

This is where the generated-code example fits:

Requirement misunderstood
→ AI implementation
→ AI tests based on same misunderstanding
→ everything green

The problem isn't "AI wrote the tests."

The problem is that the check repeated the mistake.
-->

---

# Could this check catch<br>the original mistake?

<!--
~1:30

That's the useful code-review / architecture-review question.

Not:

"Did AI write this test?"

But:

"If the implementation misunderstood the requirement, could this test fail?"

Schema.
Invariant.
Independent calculation.
Runtime behavior.
Actual customer outcome.

And AI can absolutely help us generate those checks.

We're not trying to keep AI out of validation.

Use AI to challenge your thinking.

Then use evidence to challenge both of you.

Don't overdo this.

A throwaway prototype doesn't need a regulatory validation regime.

How sure do we need to be?
How bad is it if we're wrong?

Transition:

But suppose we DO check it.

Suppose that Kafka architecture really is excellent.

We can still have a much bigger problem.
-->

---

# Trap #2

# AI Can Solve the Wrong Problem<br>Really Well

<!--
~0:30

This is an escalation from #1.

The answer isn't merely plausible.

Let's assume it's RIGHT.
-->

---

# How should these two services<br>maintain consistency?

<div class="mt-10">

```text
 Service A
    │
 Outbox
    │
    ▼
  Kafka
    │
    ▼
 Service B
```

</div>

<!--
~1:30

Let's say this is a genuinely good design.

Now ask the question that can make the entire diagram disappear.
-->

---

# Why are these two services?

<!--
~2:00

CAP didn't change.

If there is a network partition, the underlying trade-off remains.

But did we have to put a distributed boundary HERE?

Maybe absolutely yes.

Independent scaling.
Ownership.
Failure isolation.
Deployment.

Fine.

But maybe the boundary isn't earning its complexity.

The sophisticated answer didn't establish the premise.

This isn't a legacy-system problem either.
-->

---

# "How should we build our<br>AI customer-service agent?"

<br>

# What did that question already decide?

<!--
~2:00

This is the greenfield version.

We already decided:

"agent"

before discussing the actual problem.

Maybe the actual business problem is:

"Customer requests take 18 minutes to resolve. We need that under five."

Now we can consider:

- AI assistance
- classification + deterministic workflow
- process redesign
- full autonomous agent
- combinations

And maybe the agent wins.

Great.

The point isn't "less AI."

The point is that it WON instead of being assumed.

This is a Monday-morning use of AI:

Ask it:

"What assumptions did I bake into that question?"

"What am I treating as a constraint that is actually a choice?"

"Reframe the problem without assuming my proposed solution."

AI is very good at helping attack the framing too.

Transition:

And that leads to something more personal.

If AI can answer questions, explain unfamiliar systems, generate code,
and challenge architectures this quickly...

what does that do to how WE learn?
-->

---

# Trap #3

# Are You Understanding Faster—

# or Avoiding Understanding?

<!--
~0:30

Give this room.

This is deliberately uncomfortable.

I've caught myself doing the second one.

AI can take:

"I don't understand this"

to:

"working code"

without necessarily passing through:

"now I understand this."
-->

---

# Cognitive offloading is a feature.

<div class="mt-14 text-2xl">

Machine code → Compiler → Framework → Database → Cloud → AI

</div>

<!--
~2:00

Don't turn this into "you must understand everything."

Engineering IS cognitive offloading.

I don't want my team implementing B-trees.

I don't inspect every instruction javac produces.

I don't implement TCP before calling an API.

Abstractions let us work at higher levels.

AI is another enormous step in that direction.

The problem is the quiet transition from:

"I don't need to do this myself"

to:

"I don't need to understand this."
-->

---

# When you **don't know**:

## "Help me understand this."

<br>

# When you **think you know**:

## "Challenge my understanding."

<!--
~2:30

This applies to juniors AND seniors.

Junior learning Spring transactions:

"Show me how this works and why."

Then:

"What does the proxy have to do with it?"

"Would self-invocation change this?"

"How can I prove what's happening in MY application?"

AI can dramatically reduce the time from:

"I don't understand"

to:

"I have a testable mental model."

That's real immediate value.

But senior people get another enormous capability.

"I've built systems like this for 20 years."

Great.

Tell AI:

"Here's my architecture. Tell me why I'm wrong."

"What's the strongest argument for the design I rejected?"

"What assumption am I treating as obvious?"

"What could we test instead of debating?"

Experience is incredibly valuable pattern recognition.

It can also make us very good at recognizing a problem we've seen before
when this one isn't actually the same.
-->

---

# How can we find out?

<div class="mt-14 text-2xl">

Question → Try → Evidence → Learn → Repeat

</div>

<!--
~2:00

THIS is the Agile center of the talk.

None of this is new Agile theory.

We've spent decades saying:

We don't know everything.
Build feedback loops.
Working systems give us evidence.
Learn and adapt.

AI makes that argument stronger.

Because another implementation is cheap.

Another prototype is cheap.

Another architecture is cheap.

Another critique is cheap.

So when reality can answer the question cheaply:

stop arguing and ask reality.

Important qualification:

Not every architecture question can be prototyped.

You can't run a two-hour experiment proving what maintaining six services
across four teams for eight years will feel like.

Test what reality can cheaply answer.

Use judgment for what it can't.

Also: AI makes BAD questions and irrelevant critiques cheap too.

The scarce resource increasingly becomes:

"Which questions are actually worth our attention?"

Transition:

So suppose this works.

AI really does make us dramatically faster.

Now what?
-->

---

# Trap #4

# Faster Doesn't Mean<br>You Should Do More

<!--
~0:30

Immediately qualify this verbally:

"Sometimes more is EXACTLY what you should do."

Otherwise this sounds anti-productivity.
-->

---

# AI gave you capacity.

# It didn't tell you how to spend it.

<!--
~2:00

Suppose implementation capacity increases 50%.

The automatic response is:

Great — 50% more stories.
50% more PRs.
50% more features.

Why?

Maybe that's exactly where the business gets the most value.

But perhaps we can now afford three prototypes before committing.

Maybe review was already overloaded.

Maybe integration is the problem.

Maybe customers don't need more features.

Maybe we can finally fix the operational issue we've ignored for two years.

Maybe we genuinely need fewer people to produce the same business outcome.

Don't dodge that last one.
-->

---

# "If developers are 2× as productive,<br>why do we need this many developers?"

<!--
~2:30

Put the scary question directly on the screen.

This is a legitimate management question.

Don't answer:

"Because somebody has to check the AI."

That's weak and probably increasingly wrong.

Engineer → manager:

"Implementation got dramatically faster. But we're seeing the additional work
accumulate in review. Let's measure that rather than just generating more."

Manager → VP:

"We're not assuming current staffing is automatically right. But code production
isn't the outcome we're staffed to produce. Let's see what work actually
disappeared, where work moved, and what happened to delivery."

And if the answer is:

"The same outcomes genuinely require substantially less engineering labor now."

That's real.

The purpose isn't preserving jobs.

It's understanding the system.
-->

---

# What got faster?

<div class="mt-10 text-xl">

Idea → Design → **Code** → Review → Integrate → Deploy → Customer

</div>

<br>

# Where did the work go?

<!--
~2:00

Illustrative numbers spoken or progressively revealed:

Coding time ↓60%
PR production ↑80%
Review waiting ↑110%
Idea-to-production ↓8%

So how much more productive are we?

There isn't enough information in "coding got 60% faster."

Follow the effect outward.

This is not a Theory of Constraints lecture.

The AI-specific issue is that we can alter intellectual/implementation capacity
enormously and almost overnight.

And the outputs LOOK like completed work.

AI can also help us inspect this system:

PR history.
Tickets.
CI.
Deployments.
Incidents.
Customer feedback.

"Implementation time dropped, but review waiting increased,
particularly around these components."

Great hypothesis.

Now check it.

Transition:

There's one more change.

So far AI has mostly been giving us things.

Answers.
Code.
Designs.

But increasingly, AI doesn't just suggest what should happen.

It can do it.
-->

---

# Trap #5

# [TITLE TBD]

<!--
~0:30

Do NOT force the final title yet.

Build the sequence first.

Concept:

AI action can scale much faster than meaningful oversight.

This is about AUTHORITY, not merely correctness.
-->

---

# Read customer email

<!--
Progressive reveal preferred.
-->

---

# Read customer email

# ↓

# Draft response

---

# Read customer email

# ↓

# Draft response

# ↓

# Send response

---

# Read customer email

# ↓

# Draft response

# ↓

# Send response

# ↓

# Update customer record

---

# Read customer email

# ↓

# Draft response

# ↓

# Send response

# ↓

# Update customer record

# ↓

# Issue refund

<!--
~2:30 total across progressive reveals.

Don't ask:

"Where should the human enter the loop?"

That's not the point.

Ask:

"At what point did the architecture fundamentally change?"

The model may be doing essentially the same inference throughout.

What changed is its AUTHORITY.

An organization may legitimately decide the AI should autonomously do ALL
of these things.

Maybe it's demonstrably better than humans.

Fine.

But the engineering question changes as authority increases.
-->

---

# What can it do<br>when it's wrong?

<!--
~2:00

This is the core Trap 5 question.

Not:

"Can AI be wrong?"

Humans are wrong too.

Future AI may be much better than us.

The question is what authority the system grants and what the consequences are.

How bad is it?

Will we notice?

Can we undo it?

A wrong draft sitting in a queue is different from $50,000 transferred.

And don't gold-plate everything.

If the consequence is trivial and reversible, let the system move.

Controls have costs too.
-->

---

# 10,000 AI decisions

<br>

# 100 meaningful reviews

<br>

# Which 100?

<!--
~1:30

"Keep a human in the loop" doesn't solve this.

A human clicking Approve 2,000 times isn't meaningful supervision.

Oversight doesn't scale automatically because generation/action scales.

This is where you briefly mention:

- enforceable authorization
- least privilege
- automated checks
- sampling
- anomaly detection
- outcome monitoring
- escalation / stop mechanisms

Do NOT put that list on the slide.

And AI itself can do a lot of this oversight.

The point isn't humans supervising machines.

The point is designing accountability that scales with authority.
-->

---

# Five questions for Monday

<!--
~2:00

Closing synthesis.

Ideally reveal these one at a time.
-->

---

# 1.

# What do we actually know?

<!-- Trap 1 -->

---

# 2.

# What did our question already decide?

<!-- Trap 2 -->

---

# 3.

# Am I understanding faster—

# or avoiding understanding?

<!-- Trap 3 -->

---

# 4.

# What got faster—

# and where should that capacity go?

<!-- Trap 4 -->

---

# 5.

# What can it do when it's wrong?

<!-- Trap 5 -->

---

# "There are no solutions.<br>There are only trade-offs."

<!--
~1:30

Return to the opening.

AI didn't give us a world without trade-offs.

It changed them.

Fast.

Things that used to be scarce aren't as scarce anymore.

Implementation.
Knowledge access.
Alternatives.
Experiments.
Critique.

So don't organize your system as though those things still cost what they used to.

But also look for what DIDN'T disappear.

Where did attention move?

Where did the work move?

Where did risk move?

What assumptions stopped being true?

And keep re-evaluating, because these capabilities will keep changing.
-->

---

# The goal isn't maximum AI.

# The goal is better systems.

<!--
Stop.

Don't summarize the entire presentation again.

Q&A.
-->
