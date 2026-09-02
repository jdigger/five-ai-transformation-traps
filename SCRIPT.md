# Script — long-form

**This is not what shows on the lectern screen.** The speaker notes in `slides.md` are
scannable cues for live delivery; this file is the long-form prose they were distilled
from — the full arguments, the qualifications in their complete form, and the red-team
answers written out.

**What it is for**
- Estimating timing (the `~M:SS` markers are authoritative in `slides.md`, not here)
- Preparing — read this in the days before, not at the lectern
- The source material for any shared rollup (Q-06)

**Drift.** This file is the *argument of record*, not a word-for-word mirror. Update it
when the reasoning changes, not when a phrase is retuned. If the two disagree about what
the talk is *arguing*, this file is wrong and should be fixed.

---


## Slide 1 · Cover

```
~0:30

This isn't a talk about today's best model, coding assistant, agent framework,
or prompt technique. All of that will be wrong by the time you get home.

It's about mistakes I'm watching us make — mistakes I've made — as AI changes
how we build systems and how we run technology organizations.

Five of them. In each one: a tempting default to stop, a better use of AI,
and one question you can actually use on Monday.
```


## Slide 2 · Sowell quote

```
~1:30

This is the lens for the whole talk. It's not a decorative quote.

Everything we do is trade-offs:

- consistency vs availability
- flexibility vs control
- speed vs certainty
- build vs buy
- generality vs simplicity

There has never been an architecture with only advantages.

AI does not change that. AI is not a solution either.

What AI IS doing is moving the trade-offs — the ones we spent our careers
learning how to make. Fast.

Which means a decision that was obviously correct five years ago might deserve
another look, because the thing underneath it changed.
```


## Slide 3 · AI is making hard things easy

```
~2:00

Things that took hours or days can take minutes. That is genuinely fantastic.

And I want to be clear up front: the point is NOT that easy means bad, or that cheap means low quality. If something got dramatically easier, we should take advantage of it. Sometimes the correct answer at the end of one of these traps is "use much more AI, much more aggressively."

[click — cluster]

Look at that list. Notice it isn't just implementation. Critique got cheap.
Alternatives got cheap. Analysis got cheap. Explanation got cheap.

[click — kicker]

This is the question underneath all five traps.

Not "how much can AI do?" — that's a demo question.

"What just got dramatically easier, and what should we do differently
because of that?"

TRANSITION:
One of the very first things it made easy was getting a really good answer.
```


## Slide 4 · TRAP 01 intro

```
~0:30

Let this sit for a second.

Everybody in this room already knows AI can hallucinate. That's the boring
version of this problem, and honestly it's the version we're getting better at
catching, because obvious nonsense is obvious.

I'm interested in the other one. The sophisticated, well-reasoned, completely
coherent answer that raises our confidence in something we never actually
established.
```


## Slide 5 · Refund requirement loop

```
~3:30  — the money slide of Trap 1. Do not rush the clicks.

Read the requirement out loud. "Customers who cancel mid-cycle get a prorated refund." Ask the room: does anybody see a problem with that sentence?

They won't. It's a perfectly normal requirement. That's the point.

[click 1] AI writes the implementation. Let's say it's good code.
[click 2] AI writes the tests. Let's say they're good tests — edge cases, boundary conditions, the day-one and day-thirty cases.
[click 3] Green. All the way green.

Now. What do we actually know at this moment?

We know the implementation matches the tests. We do not know anything at all about whether either of them matches what the business meant.

[click 4] Because both of them came out of the same reading of that sentence.

The problem here is NOT "AI wrote the tests." I want AI writing tests. It is very good at it and I am not going back.

The problem is that the check repeated the mistake.

[click 5] Finance meant unused whole days, not fractional days. And they never refund the setup fee — everybody in billing knows that, nobody ever wrote it down.

So we shipped a refund calculator that overpays. Quietly. Correctly, according to every test we have.

Somebody in here is thinking: a human would have made exactly the same mistake.

Yes. Absolutely. A human reading that sentence makes the identical error. That is not the interesting part.

But one human makes it once. A second human, reading it separately, probably makes a different mistake — which is the entire reason code review has ever worked. The second person was never valuable because they were guaranteed to be smarter. They were valuable because they were independent.

Point at the 47 passing tests:

"You didn't get forty-seven checks. You got one check, forty-seven times."

The mistake and the thing that was supposed to catch it are no longer independent events. The amount of convincing-looking evidence went up while its independence went to zero, and every artifact still says "verified."

Independence used to arrive as a by-product of friction — different people, different days, the time the work took. Now we have to build it on purpose.
```


## Slide 6 · Evidence that didn't come from that sentence

```
~2:00

None of these are exotic. Notice what they have in common: none of them come from the implementation's reading of this requirement.

[click 1] Suppose the ledger already carries a separately established refundable balance. Checking that the refund does not exceed that balance is a cheap boolean comparison once the rule exists.

But do not hear "obvious" or "nobody had to interpret it." People still had to decide what counts as refundable, and that rule can still be wrong. The independence comes from provenance: the implementation came from this sentence; the ledger constraint came from somewhere else. It does not prove the whole policy is right. It gives one independently sourced fact a chance to contradict the implementation.

[click 2] The replay is the strongest one and it is now trivially cheap, which is itself a thing AI changed. Ninety days of real cancellations, run them through the new code, diff against what finance actually paid out. A quick script or appropriately controlled tool access can do work that once required a specialist and a long queue. Access controls still apply; ease of access is not permission. Reality already ran the experiment. We just have to go read the results.

[click 3] And the cheapest one is still a human being. Ten examples, thirty minutes, the person who owns the policy. No framework required.

[click 4] So: use AI to challenge your thinking. Genuinely — ask it to attack your design, generate the tests, find the edge cases. It's good at it.

Then use evidence to challenge both of you.

A fresh context matters. "Write the implementation, now write the tests" in one session is maximum contamination. Generating tests from the requirement in a new context, before the implementation exists, restores some independence for roughly the same effort.

None of this is new. Pairing, test-first, and an on-site customer were all ways XP manufactured independence. AI makes that machinery cheaper at the same moment it makes the independence more necessary.

PROPORTIONALITY — say this out loud, it matters:
Don't do all three for a throwaway prototype. The two questions that set the budget are "how sure do we need to be?" and "how bad is it if we're wrong?" A refund calculator earns the replay. A spike you're deleting Friday does not. Spending ten dollars to verify a ten-cent experiment is also an engineering failure.

All of these techniques differ, but they force the same question.
```


## Slide 7 · Q: What do we actually know?

```
~1:30

Pause. This is the conclusion of Trap 1.

What do we actually know?

The operational version for a code review or architecture review is: could this check catch the original mistake? Is there any path where it goes red?

Notice what it is NOT. It's not "was a human involved." It's not "did AI write this." Those are proxies, and they're bad ones — a human writing a test from the same misunderstanding is exactly as useless.

If it is structurally impossible for this check to fail when we've misunderstood the problem, then it isn't a check. It's a restatement.

This is the recurring visual for the whole talk: this teal bar means "here's a question to use on Monday." Every trap will now end here.

TRANSITION:
Now suppose the answer really is right. We can still have a much bigger problem.
```


## Slide 8 · TRAP 02 intro

```
~0:30

Let's stay in the same customer-service world as the refund example, but move
one step outward: from one refund decision to the support queue around the
product.

In Trap 1 the answer might be wrong. Here, assume the answer is completely,
verifiably RIGHT. Excellent, even.

The system does exactly what we asked. That is what makes the trap possible.
```


## Slide 9 · The business goal

```
~1:30

The refund may be straightforward with our spiffy new service, but getting help
is not.

Sales are up. That's good. Support volume is up too. That's less good.

The same team of representatives is handling more incidents than it can absorb.
People get overwhelmed. Each incident starts taking longer, which grows the
queue, which makes the overload worse. The problem begins feeding itself.

Support management has the obvious answer: we need more people.

And this is where somebody says: “What if technology could swoop in and rescue
us?”

[Deliver that line with the lightly theatrical robot-superhero tone. Do not say
“robot superhero” or “cue the robot superhero.” The joke is our recurring hope
for technological rescue, not the support team or the seriousness of the
problem.]

[click]

That is a serious business goal: get the customer a correct resolution in under
five minutes, any time of day.

Do not say AI until the next slide. The problem statement must stand without it;
AI should enter as a credible answer rather than a premise hidden inside the
question.
```


## Slide 10 · The system we built

```
~2:00

So we build the system people are hoping AI can become.

It reads what the customer wrote, pulls the account and order context, applies
the policy, takes the action it is allowed to take, and explains what happened.
If it is genuinely uncertain, it escalates.

And it works. Correct answers. Personalized. Available around the clock. Trap 1
does not apply here.

[click 1]

The wait drops from eighteen hours to under five minutes.

[click 2]

If someone brought me that result, I would say yes.

Do not foreshadow a hidden model failure. Let this feel like a win, because it
is one.
```


## Slide 11 · One week of support

```
~2:00

At the end of the week the number says: eight hundred tickets resolved. The
support metric is green.

[click 1]

But the system also clusters what it saw. Three hundred and forty-four of those
customers were describing the same checkout failure.

[Pause. Give the room time to reclassify what it is seeing.]

[click 2]

We thought we had 344 support cases.

We had one product problem, reported 344 times.

[Long pause.]

The system found the cluster. Do not make the AI implausibly blind; a good
support system should detect repeated language and shared context. The turn is
that the work looked like hundreds of independent conversations because we
named the queue “support.”
```


## Slide 12 · The framing decided whether it was the job

```
~1:30

And yes: a good system should notice that pattern. This one did.

But we had chartered it as a support-automation project. We funded it, measured
it, and assigned ownership around one job: resolve support contacts quickly.

So the trend appeared in a report. Support celebrated the wait-time
improvement. The checkout defect stayed in somebody else's backlog.

The AI found the evidence. The framing decided what counted as the job.

The question had already decided that the product was fixed, and support was
where the problem lived.

This is not mainly a capacity or metric trap. We mistook a stream of evidence
about the product for a queue of independent work to complete. The support
system is still valuable; the question is whether resolving each contact also
makes the recurring reason for contact impossible to ignore.
```


## Slide 13 · Ask it to attack your framing

```
~1:00

This is a Monday-morning thing, and it's a positive use of AI, not a warning
about it.

Before you ask AI for the design, spend ninety seconds asking it to attack the
question.

[Apply the prompts directly to the support story: What did “resolve support
tickets” already assume? What if the current product is not a fixed constraint?
Reframe the goal so repeated contact becomes evidence to remove the cause, not
merely work to complete.]

[clicks]

The value is the friction. If every answer confirms the framing, you have not
challenged it yet.

[click 4] The tool will not do this on its own. Ask a leading question, get a
led answer. It is extremely agreeable and that is the failure mode.

All three prompts are ways of forcing one question.
```


## Slide 14 · Q: What did our question already decide?

```
~0:30

Pause. This is the conclusion of Trap 2.

What did our question already decide?

The support system may be exactly right. The five-minute target may be right.
The trap was letting “support queue” decide that 344 reports were 344 pieces of
support work instead of one product problem.

Make the framing win the argument instead of letting it skip the argument.

TRANSITION:
Now something more personal. If AI can explain unfamiliar systems, generate the code, and challenge the architecture this fast — what does that do to how WE learn?
```


## Slide 15 · TRAP 03 intro

```
~0:30

Give this room.

This one is deliberately uncomfortable because both behaviors can produce
working code. Only one keeps your judgment calibrated.

AI can take you from "I don't understand this" to "working code" without ever
passing through "now I understand this."
```


## Slide 16 · Cognitive offloading is a feature

```
~2:00

Before I make anybody feel bad, let me kill the obvious wrong version of this.

I am not saying you must understand everything AI produces. That's nonsense and it would destroy the entire value of abstraction.

Engineering IS cognitive offloading. I don't want my team implementing B-trees. I don't read the bytecode javac emits. I have not implemented a TCP stack and I would like to keep it that way. Every one of those arrows is somebody deciding to stop understanding a layer, and every one of them was correct.

AI is another enormous step along that line and I'm in favor of it.

[click]

The danger is this one quiet slide from a true statement to a different statement. Nobody announces it. It just happens on a Tuesday.

And here's the honest version of what you need: you don't need to understand everything under an abstraction. You need enough to recognize where the seams are — and which ones matter.

Transaction boundary meets service boundary. Retry meets idempotency. Cache meets stale data. Generated code meets an undocumented convention. "Executed successfully" meets "did the wrong thing."

That's what you keep.
```


## Slide 17 · Help me / Challenge me

```
~2:30

Two modes. Both are enormous, and the split is not what people assume.

[left] When you're in unfamiliar territory, AI collapses the distance between "I have no idea what's happening" and "I have a testable mental model." Not "I have an answer" — a mental model I can go check. That is a real, immediate, economic gain and it applies to a new grad learning Spring transactions and to me landing in a Rust codebase.

[click 1 — right] But this second one is the underrated one, and it's most valuable to the most experienced people in this room.

Experience is compressed pattern recognition. It is the most valuable thing you have. It is also exactly the mechanism by which you decide this problem is the same as the one you solved in 2014, and stop looking.

Now you can hand your design to something that will argue with you at 11pm for free and never gets tired or political about it.

[click 2] So it isn't a seniority thing. It's a familiarity thing, and most of us are in both states in the same week.

ON JUNIORS — say some version of this:
Some traditional junior work really is getting less valuable. Boilerplate, routine implementation, simple debugging. I'm not going to pretend otherwise and I'm not going to argue we should preserve obsolete work because that's how my generation learned.

But there's a difference between juniors producing junior artifacts and engineers developing judgment. The second one still has to happen, and the path "ask, generate, tests pass, merge" does not produce it.

ON SENIORS — the uncomfortable half:
And I'm not going to give you the comforting version where AI writes the code and seniors provide the judgment. AI is going to participate in judgment too. It already reviews, critiques, designs, and analyzes evidence.

What I'd say instead: offload implementation effort without disconnecting from implementation evidence. The moment you stop touching real code, real incidents, real production, your judgment stops being calibrated — and we already know what that role looks like. We called it the ivory tower architect and we didn't like it.
```


## Slide 18 · How can we find out?

```
~2:15

This is the Agile center of the talk, and I want to name something directly.

Somebody here is thinking "you've rediscovered Agile." Yes. Correct. Guilty.

We've spent twenty-five years saying: we don't know everything up front, build feedback loops, working systems produce evidence, learn and adapt.

Here's the thing — AI makes that argument STRONGER, not weaker. Every objection to running the experiment used to be about cost. Another implementation is expensive. Another prototype is expensive. Another architecture is expensive. Another serious critique is expensive.

They're not, anymore.

[click]

So when reality can answer the question cheaply — stop arguing and go ask reality. The two-hour spike beats the two-hour meeting, and now it's a twenty-minute spike.

THE QUALIFICATION — do not skip this, a senior architect will nail you on it:
Not every question is experimentally answerable. You cannot run a prototype that tells you what maintaining six services across four teams for eight years will feel like. That is a judgment call and it stays a judgment call.

Test what reality can cheaply answer. Use judgment for what it can't. And know which one you're doing.

ALSO WORTH SAYING:
AI made bad questions cheap too. And irrelevant critiques. And prototypes nobody needed. More alternatives is not automatically better. The scarce thing now is deciding which questions deserve your attention at all.

The loop only works if I stay connected to its evidence.
```


## Slide 19 · Q: Am I understanding faster — or avoiding understanding?

```
~0:30

Pause. This is the conclusion of Trap 3.

Am I understanding faster — or avoiding understanding?

This is not "did I write the code myself?" It is whether I can still test my mental model against what the system actually does.

TRANSITION:
Suppose all of this works and we really are dramatically faster. Now what?
```


## Slide 20 · TRAP 04 intro

```
~0:30

QUALIFY THIS IMMEDIATELY AND OUT LOUD:

"And sometimes more is exactly what you should do."

Otherwise this reads as anti-productivity and half the room stops listening.
```


## Slide 21 · AI gave you capacity

```
~2:00

Say implementation capacity goes up fifty percent. The automatic response is fifty percent more stories, fifty percent more PRs, fifty percent more features.

And maybe! Maybe that's exactly where the value is.

But look at the other options, because nobody put them on the table:

- We can afford three prototypes before we commit to one.
- Review was already the bottleneck and we just made it worse.
- Integration is the actual problem.
- Customers do not want more features, they want the three we have to work.
- We can finally fix the operational thing we've been ignoring for two years.
- Or: the same business outcome now genuinely needs fewer people.

I'm not going to dodge that last one.
```


## Slide 22 · If developers are 2x as productive

```
~2:30

Put it on the screen. Somebody in your org is already saying it in a meeting you weren't invited to.

This is a legitimate question. It is not hostile. If I'm a CFO and engineering is my largest line item and my engineers are telling me they're twice as fast, I would be negligent not to ask.

DO NOT ANSWER: "because somebody has to check the AI."
It's weak, it's defensive, and it's increasingly going to be false. Don't build your career on it.

Here's what a credible conversation sounds like.

Engineer to manager:
"Implementation got dramatically faster. What we're actually seeing is the extra work piling up in review — cycle time barely moved. Let me measure that before we just generate more."

Manager to VP:
"We're not assuming current staffing is automatically correct. But code production isn't the outcome we're staffed to produce. Let's look at what work actually disappeared, where work moved, and what happened to delivery."

And if the evidence says the same outcome genuinely takes substantially less engineering labor — that's real, and I'd rather find out from the data than from a spreadsheet somebody else built.

I'm not going to stand here and promise you everyone moves up the value chain. Historical transformations don't work that neatly. Some skills are going to become less scarce. Some roles will shrink. I don't know which ones, and neither does anyone selling you a certainty about it.

What I do know is that being wrong about where the work went is bad for everybody in the argument.
```


## Slide 23 · What got faster? (pipeline + metrics)

```
~2:00

Here's the pipeline. AI hit one box in it, hard.

[click 1] These numbers are illustrative — I made them up, say so — but the SHAPE of them is what I keep seeing.

Coding time down sixty percent. Real. Measurable. Everyone's happy.
PRs up eighty percent.
Time waiting for review, up a hundred and ten percent.
Idea to production: down eight percent.

[click 2] So — how much more productive are we?

There is not enough information in "coding got sixty percent faster" to answer that. The constraint moved and we celebrated the wrong number.

This is NOT a Theory of Constraints lecture — you all know constraints move. The AI-specific part is the speed and the disguise. We can change implementation capacity enormously, almost overnight, and the outputs LOOK like finished intellectual work. Two hundred PRs of plausible code is not two hundred PRs of progress, but it photographs identically.

THE POSITIVE USE — don't skip it:
AI is genuinely good at finding this. Point it at your tickets, PR history, CI runs, deploys, incidents, support tickets. Ask it where the time actually went.

You'll get back something like: "implementation time dropped, but review wait increased, concentrated in changes touching these three components."

That is a hypothesis, not a finding. Now go check it with telemetry. Same rule as Trap 1 — could that check catch the mistake?

Before we decide what to do with the new capacity, name the decision.
```


## Slide 24 · Q: What got faster — and where should that capacity go?

```
~0:30

Pause. This is the conclusion of Trap 4.

What got faster — and where should that capacity go?

Those are two separate questions. "Coding got faster" does not answer either one for the whole organization.

TRANSITION:
So far AI has mostly been handing us things: answers, code, designs. Increasingly, it doesn't hand you the thing. It just does it.
```


## Slide 25 · TRAP 05 intro

```
~0:30

TITLE STILL PROVISIONAL — candidates:
  - When AI Gets It Wrong, What Is It Allowed To Do?   [current]
  - AI Can Scale Faster Than Your Ability To Supervise It
  - Who Gave The AI Permission To Do That?

Current pick is the least clever and the most useful — it states the actual
question, and it sets up the closing question verbatim.

The concept: this is about AUTHORITY, not correctness.
```


## Slide 26 · Authority ladder

```
~2:30 across the reveals. Go slowly. Let each one land.

Same product. Same model. Same prompt, more or less.

[click through them one at a time, reading each aloud]

Now — don't ask "where should the human enter the loop." That's the governance answer and it's the wrong question.

Ask: at what point did the architecture fundamentally change?

Because the model is doing roughly the same inference the whole way down. Same capability, same error rate, same everything.

What changed is AUTHORITY.

And an organization may legitimately decide the AI should autonomously do every single one of these. Maybe it's measurably better than the humans doing it now — faster, more consistent, fewer bad days. That's a real possibility and I'm not going to argue against it from human dignity.

I'm not making an argument about intelligence at all. I'm making one about consequences.

TRANSITION:
And before we ask what it should be allowed to do — one more thing about that first rung.
```


## Slide 27 · Prompt injection

```
~2:00 — keep this tight. This is NOT a security tutorial, and the room will try to make it one.

Point back at the ladder still fresh in their heads: "Rung one was — read the customer's email."

That whole ladder was about what the AI is allowed to DO. This is the other half: who gets to talk to it.

SQL injection taught us something structural: you don't defend by getting better at spotting malicious strings. You separate the instruction channel from the data channel — parameterized queries — so the data physically cannot become code.

Prompt injection has a related trust-boundary problem. It is NOT the same vulnerability, and I want to be careful here.

[click 1] Because there's no equivalent separation available. The email is supposed to be data. But interpreting instructions written in English is precisely what the model does. That is not a bug we are going to parameterize away.

[click 2] And notice what the obvious question does.

"How do we stop the model from being tricked" has already decided that the defense lives inside the model — which is the one place we cannot fully enforce it.

That's Trap 2. Turning up again, at the worst possible moment, in a security review.

BE HONEST IF ASKED — and someone here will ask (this is the security engineer's slide):
Authorization does not solve prompt injection. There are real mitigations and people are making real progress on them. What authorization does is decide how much a successful injection is WORTH. That's a blast-radius argument, not a fix. A prompt is not a security boundary.

Do not get drawn further in. If it keeps going: "grab me afterwards, I'd enjoy that conversation and it's a different talk."

[NOW PUT THE TWO HALVES TOGETHER. This is Trap 5 in one sentence — slow down:]

Rung one is an input we do not control.

Rung five is issuing a refund.

So the question was never whether it can be tricked. Something, someday, will trick it.

TRANSITION — straight into the scale problem, no pause:
And that authority can now act much faster than careful human oversight.
```


## Slide 28 · 10,000 decisions / which 100?

```
~1:30

Here's the arithmetic nobody does.

[click 1] Ten thousand and one hundred are deliberately round. The point is the orders-of-magnitude gap: genuinely careful human review will cover only a small fraction of the decisions AI can produce.

[click 2] So: which hundred?

"Keep a human in the loop" is not an answer to that question. A person clicking Approve two thousand times is not supervision — it's a signature. Many of us know what that feels like.

Oversight does not scale just because action scaled.

BRIEFLY — say these, don't slide them:
There are real mechanisms. Enforceable authorization and least privilege, so the blast radius is bounded whether or not anyone is watching. Automated checks. Sampling. Anomaly detection. Outcome monitoring rather than execution monitoring. Traceability. And a stop button that actually stops things.

And AI can do a lot of this work itself. The point is not humans supervising machines — that framing loses eventually. The point is designing accountability that scales with authority.

If you take one thing from Trap 5: authority and oversight should grow together. Right now we are very good at scaling one of them.

Oversight cannot scale by asking people to stare at more decisions. So end on the authority question.
```


## Slide 29 · Q: What can it do when it's wrong?

```
~2:00

Pause. This is the conclusion of Trap 5.

What can it do when it's wrong?

Not "can AI be wrong." Everything is wrong sometimes. Humans are wrong. Future models will be much better than today's and this question does not go away — it gets more important, because we'll grant more authority.

Three follow-ups, and they're the ones you already use for everything else:

How bad is it? A wrong draft sitting in a queue is not a wrong wire transfer.

Will we notice? — and this is the one I want to dwell on. Our entire monitoring tradition is built on things that break loudly. Exception, crash, timeout, p99. AI failure doesn't look like that. AI failure looks like: the operation completed successfully, and what it did was wrong. Nothing threw. Every dashboard is green. That's the whole problem.

For AI systems, "nothing threw an exception" is an especially weak definition of success.

Can we undo it? Reversibility buys you more than almost any control does.

AND — do not gold-plate. Controls are not free either. They cost latency, flexibility, engineering time, and customer experience. If the consequence is small and reversible, let the system move. "Yeah, that might break, and we're fine with that" is a legitimate engineering conclusion. Deliberately accepting risk is engineering.

I don't want to replace AI maximalism with governance maximalism.

TRANSITION:
Five traps. Five questions.
```


## Slide 30 · Five questions for Monday

```
~2:30

That's it. That's the talk.

The traps were the "not that." These five questions are the "do this."

[reveal one at a time, say each one, brief callback to its trap]

1 — What do we actually know?
2 — What did our question already decide?
3 — Am I understanding faster — or avoiding understanding?
4 — What got faster — and where should that capacity go?
5 — What can it do when it's wrong?

If one of these makes you stop and ask a better question a month from now, this
was worth your evening.
```


## Slide 31 · Sowell callback

```
~1:30

Back to where we started.

AI did not give us a world without trade-offs. It moved them, and it moved them faster than any shift I've worked through — and I've been through the internet, distributed systems, Agile, cloud, DevOps, microservices, and a couple of reorganizations I'd rather not relive.

Here's the lesson I actually carry from those: people were profoundly correct that the internet would change everything, and profoundly wrong about exactly how. I'd assume the same is true of everything I've said tonight.

Things that were scarce aren't anymore. Implementation. Knowledge access. Alternatives. Experiments. Critique.

So stop organizing your systems and your teams as if those things still cost what they used to.

But go look for what didn't disappear. Where did the attention go? Where did the work go? Where did the risk go? Which assumption quietly stopped being true?

And keep doing it, because this is going to move again next year.
```


## Slide 32 · The goal isn't maximum AI

```
Stop here.

Do NOT re-summarize. Do not add a thank-you slide with your Twitter handle.

Say the line, pause, then: "I'd love to argue about any of this."

Q&A — 10-15 minutes.

LIKELY QUESTIONS / PREPARED ANSWERS:

Q: "Doesn't this all assume today's AI stays unreliable?"
   No. Every question in the talk gets MORE important with better models,
   because we'll grant more authority. "What can it do when it's wrong" is not a
   question about capability.

Q: "Isn't this just engineers protecting their jobs?"
   Trap 4 explicitly says the same outcome may genuinely need fewer people, and
   that we should go measure it. I'd rather find that out honestly.

Q: "So AI writes everything AND I have to understand everything?"
   No — offload aggressively. Keep understanding where the seams are and where
   the consequences are. Those are much smaller sets than "everything."

Q: "Authorization doesn't solve prompt injection."
   Correct, and I said so. It bounds what a successful injection is worth.

Q: "Evidence doesn't decide — organizational power does."
   Fair. Evidence should arbitrate factual claims. Decisions also involve
   objectives, risk appetite, and commitments. But seniority shouldn't make a
   factual claim unfalsifiable — and a junior with AI can still be
   spectacularly wrong.

Q: "I'm a small business, I need to survive 18 months, not build a talent
    pipeline."
   Completely legitimate. Then Trap 4 is your trap: figure out what actually
   got faster in YOUR pipeline before you staff to it.
```

---

## Background · Trap 1's core argument (D-58, 2026-08-25)

The Slide 5 and Slide 7 sections above carry the live version of this argument. This section preserves the deeper reasoning behind those stage choices.

**"A human would make the same mistake" is not an objection to be parried. It is the
argument.**

Trap 1 is not "AI is unreliable." Everyone in the room already discounts that claim, and
they are right to — obvious nonsense is obvious and we are getting better at catching it.
Trap 1 is that **the shape of your evidence changed.**

A human reading an ambiguous requirement makes an error. So does AI. Identical error,
identical cause. What differs:

1. **One human makes the mistake once.** A second human, reading the same sentence
   independently, most likely makes a *different* mistake. The non-overlap of two people's
   misreadings is the whole reason code review, pair programming, and a separate QA
   function have ever produced value. It was never that the second person was smarter — it
   was that they were *independent*.

2. **Implementation and tests generated from one reading make the same mistake, with
   certainty.** Not probably. The error propagates into the artifact whose entire job was
   to catch it. Forty-seven tests derived from one misunderstanding are not forty-seven
   checks. They are one check, run forty-seven times, reported as forty-seven successes.

3. **Therefore the count of evidence rose while the effective sample size stayed at one** —
   and every artifact still displays the surface features of verification. Green build.
   Coverage number. Passing count. Those signals were calibrated in a world where producing
   them was expensive, and the expense was doing epistemic work nobody had named.

**The qualitative claim, stated carefully.** Speed did not simply produce more of the same
kind of evidence. It removed the *accidental mechanism* that used to produce independent
evidence. Friction — different people, different days, the hours it took — was generating
independence as a free by-product. Remove the friction and the by-product disappears with
it, silently, because nobody ever wrote down that it was there.

**Independence used to be free. Now it has to be engineered.**

This is what makes Slide 7 coherent rather than a list of good practices. Each item is a
different *source* of independence, deliberately purchased:

- **The invariant** — independent because the claim is narrower than the requirement.
  `refundAmount <= amountPaid` needs no interpretation, so no interpretation can taint it.
- **The replay** — independent because it is history. Ninety days of real cancellations
  were produced by a system that never read our sentence and had no opportunity to inherit
  our misreading.
- **The policy owner** — independent because it is a different reader, and specifically the
  reader whose understanding is definitionally correct.
- **Fresh context** — the cheapest partial fix, and TDD's ordering discipline applied to an
  AI workflow: generating tests from the requirement in a new context, before the
  implementation exists, restores *some* independence for the same effort.

**A rhyme worth noticing and not naming on stage.** Trap 1 and Trap 2 both turn on a
control that was invisible and got optimized away — *duration* in Trap 1, *order* in Trap
2. In both, nobody decided to remove it; it was never written down as a control in the
first place. Let the room feel the echo. Naming it would pull Trap 1 toward framing, which
is Trap 2's territory, and re-blur the two traps (R-02).

---

## Addendum · XP as independence machinery, and the human/technical seam (D-59, 2026-08-25)

**XP already solved this, and then we couldn't afford it.**

Everything Trap 1 now argues about independence (see the D-58 addendum) was built into
Extreme Programming as explicit machinery, installed along the entire path from requirement
to production:

- **Pair programming** — two readers with different priors on the same problem, continuously.
- **Test-driven development** — a check authored *before* the implementation exists, and
  therefore structurally incapable of being derived from it.
- **On-site customer** — the person who owns the meaning, available to be asked. This is the
  "show ten of them to the person who wrote the policy" item on Trap 1's evidence slide,
  thirty years early.
- **Collective code ownership and continuous integration** — verification by people who did
  not write the thing, continuously rather than at a gate.

None of it was novel epistemics. It was a deliberate, expensive attempt to buy independence
that teams were otherwise not getting.

**And expense is why it didn't stick.** Pairing costs two salaries against one keyboard.
TDD costs visible time up front against invisible time saved later. An on-site customer
costs a stakeholder's calendar indefinitely. Under cost pressure these are the first things
cut, and they were cut nearly everywhere — usually while keeping the standups.

**What changed is the price on both sides of the trade.** AI cut the cost of the machinery:
generating a test suite, producing a critique, arguing an alternative, exploring an
unfamiliar system. Simultaneously it removed the *accidental* independence that made
skipping the machinery survivable — the independence we were getting for free from friction,
from different people, from elapsed time. So the practices got cheaper and the need for them
got sharper in the same movement.

**The limit that must never be dropped: AI pairing is weaker independence than human
pairing.** A human pair brings different priors, different scar tissue, different
misreadings — the non-overlap is the entire product. An AI in your session inherits your
framing, your vocabulary, and the assumptions embedded in how you asked. It is the same
correlated-error problem that Trap 1 is about, presented in a form that feels like help.
This does not make it worthless — it is excellent for attention, momentum, and unfamiliar
ground, and the fresh-context technique recovers part of the independence. It makes it a
*partial* substitute that must not be mistaken for the real thing.

**Audience caution.** This is the most flattering thing the deck could possibly say to an
Agile meetup, and flattery is a failure mode. The honest version keeps both edges: XP was
abandoned for real reasons, and its AI-powered successor is weaker than the original in the
specific dimension that mattered most.

---

**The talk's actual subject.**

Every trap is a technical system meeting a human system that nobody wrote down:

| Trap | Technical side | Human system it hit |
|---|---|---|
| 1 | implementation + generated tests | what finance actually meant |
| 2 | an approval workflow optimization | why the approvals were in that order |
| 3 | offloaded cognition | how judgment actually forms |
| 4 | pipeline throughput | what an organization is staffed to produce |
| 5 | autonomous action | who is allowed to decide |

Sowell is a systems thinker about human systems — incentives, institutions, second-order
consequences, the costs nobody counted. The audience are systems thinkers about technical
systems. The quote bookends the talk not as decoration but because **the distinction between
the two is a convenience of our job titles, not a property of the systems.** The parts we
wrote down are the technical system. The parts we didn't are still running, still enforcing
constraints, and still absorbing the consequences when a technical change arrives faster
than they can adapt.

That is why every trap resolves to a question rather than a practice, and why none of the
five questions are about AI.
