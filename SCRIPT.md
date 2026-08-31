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

Five of them. And a question for each one you can actually use on Monday.
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
~3:00  — the money slide of Trap 1. Do not rush the clicks.

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

RED-TEAM NOTE (if challenged: "a human would make the same mistake"):
Yes — absolutely. A human reading that sentence makes the identical error. What's different is the SPEED and the CONFIDENCE. We got an implementation, a test suite, and a green build in twenty minutes, and every artifact in front of us says "verified." The volume of convincing-looking evidence went up without the amount of actual evidence going up at all.
```


## Slide 6 · Q: Could this check catch the original mistake?

```
~1:30

This is the question I want in your code reviews and your architecture reviews.

Notice what it is NOT. It's not "was a human involved." It's not "did AI write this." Those are proxies, and they're bad ones — a human writing a test from the same misunderstanding is exactly as useless.

The question is about causation. Could this thing have gone red?

If the answer is no — if it is structurally impossible for this check to fail when we've misunderstood the problem — then it isn't a check. It's a restatement.

This is the recurring visual for the whole talk: this teal bar means "here's a question to use on Monday." You'll see it four more times.
```


## Slide 7 · Evidence that didn't come from that sentence

```
~2:00

None of these are exotic. Notice what they have in common: none of them come from anybody's reading of the requirement.

[click 1] The invariant is free and it is not a matter of opinion. You cannot refund more than someone paid. That is not "does this seem reasonable" — that's a line of code that is either true or it isn't.

[click 2] The replay is the strongest one and it is now trivially cheap, which is itself a thing AI changed. Ninety days of real cancellations, run them through the new code, diff against what finance actually paid out. Reality already ran the experiment. We just have to go read the results.

[click 3] And the cheapest one is still a human being. Ten examples, thirty minutes, the person who owns the policy. No framework required.

[click 4] So: use AI to challenge your thinking. Genuinely — ask it to attack your design, generate the tests, find the edge cases. It's good at it.

Then use evidence to challenge both of you.

PROPORTIONALITY — say this out loud, it matters:
Don't do all three for a throwaway prototype. The two questions that set the budget are "how sure do we need to be?" and "how bad is it if we're wrong?" A refund calculator earns the replay. A spike you're deleting Friday does not. Spending ten dollars to verify a ten-cent experiment is also an engineering failure.

TRANSITION:
But now suppose we do all of that. Suppose we check it properly and the answer really is right. We can still have a much bigger problem.
```


## Slide 8 · TRAP 02 intro

```
~0:30

This is an escalation from Trap 1, and it's the one I think about most.

In Trap 1 the answer might be wrong. Here, I want you to assume the answer is
completely, verifiably RIGHT. Excellent, even.

And it doesn't help.
```


## Slide 9 · Refund approval / escalation chain

```
~4:15

Somebody asks AI this. Completely reasonable question — refunds are slow, customers are
annoyed, somebody owns that metric.

Walk the chain first, out loud, and use the organization's OWN words for it: "Three approvals. The agent who takes the call. Their supervisor. Somebody in finance. That's what the wiki says. That's what everybody calls it."

Then read the numbers, flatly, like housekeeping. Do NOT make anything of them yet: "Two thousand refunds a week. Two hundred reach a supervisor. Twenty reach finance."

That is the whole trick of this slide. The evidence is on screen from the first frame, stated in a bored voice, and the room files it as scene-setting.

Everyone here has worked in a company like this.

And AI gives you a genuinely good answer.

[click 1] Route by amount and risk score, so the easy ones move.

Note what just happened, lightly — pay it off at the reveal, don't spend it now: AI just reconstructed a threshold policy out of the two variables it could see in the data. Amount, and risk. It's plausible. It looks like an improvement.

[click 2 — THE DIAGRAM RESTACKS. Stop talking. Let them watch it happen. Then:]
And this one is actually clever. Those three approvals were happening in SEQUENCE — the supervisor can't look at it until the agent is done, finance can't look until the supervisor is done. They don't have to. Run them at the same time.

It's free. It genuinely works. Cycle time drops, maybe a lot.

[DO NOT point at the numbers. They just changed, in front of everybody, and the job right now is to be pleased about the cycle time. If somebody in the room calls it out here — that is the best possible outcome. Say "hold that" and keep going.]

[click 3] Reminders, escalation, an exception queue for the weird ones, a dashboard so nothing sits in an inbox for three days invisibly.

Every one of those is a real improvement. If someone brought me this I would say yes, do it. I would have said yes.

Let's stipulate: this is right. Trap 1 does not apply. We checked it.

[click 4 — everything grays out, and THE ARROWS COME BACK, in orange, running down the stack. Long pause. Let them read it.]

Why were they in that order?

[Wait. Do not fill the silence. Then:]

Because it was never three approvals. It was an escalation chain.

The agent handled the refund. The supervisor saw the ones the agent escalated. Finance saw the ones the supervisor escalated. Each level reviewing the level beneath it — and each level seeing a fraction of what the level beneath it saw.

[NOW point at the numbers. This is the moment the slide exists for:]

Two thousand. Two hundred. Twenty.

That is not three people doing the same job slowly. That is a funnel. The order was the control — and the numbers were the proof, and they have been on this screen since before I said a word.

[point at the three 2,000s]

Look at them now.

It was on the screen the whole time. We were watching the cycle time.

That order wasn't latency. That order was the control, and it was the filter. We deleted both — and the deletion was visible, in the moment, to anyone who was looking at the right number.

[click 5 — the consequence appears. This is the proof, and it is the best beat on the slide. Do not rush it.]

Here's how you find out. Not from the dashboard — the dashboard is green, cycle time is down, that was the metric.

You find out because a week after this ships, the supervisor and the finance team are drowning. Two hundred to two thousand. Twenty to two thousand. A hundred-fold increase in finance's workload, and it shipped as a performance improvement.

And listen to what that complaint sounds like when it arrives: "we don't have enough people." It gets filed as a capacity problem. It gets a headcount request, or a prioritization filter, or — and this is the part that should worry you — somebody suggests using AI to triage the queue.

Nobody in that conversation says the word "control." The governance is gone and the ticket says CAPACITY.

[THE MECHANISM — this is the actual point of Trap 2, land it clearly:]

So why didn't anyone catch it? Not because the AI was bad — and notice, not because the information was missing either. The volumes were right there. AI could have read them.

Because the REASON for that order was never written down.

In Trap 1 the missing thing was a rule — nobody wrote down that the setup fee isn't refundable, so the answer came out wrong. Here the missing thing is a rationale. Every fact you needed was available. What was missing was why anybody had arranged them that way, and without that, the question went unchallenged.

A missing rule makes the answer wrong. A missing rationale makes the question unchallengeable.

It isn't in the code. It isn't in the ticket. It isn't on the wiki — the wiki says "three approvals." It was in the head of whoever set those thresholds, probably after something went wrong, and they left in 2019.

AI cannot ask about a constraint nobody recorded. Neither can a new architect. Neither can a new dev team. Neither could you, on your first week.

That's the trap. It is not an AI problem — AI just made it fast. What we typed, "how do we speed up refund approvals," handed AI a description of a process and asked it to make the description faster. And it did, beautifully.

Nobody typed "the order doesn't mean anything." It just came along.

To be fair: maybe there are excellent reasons to change it. Maybe the thresholds are twenty years stale and the whole chain should go. Segregation of duties is a real control and I am not telling you to delete it, and I am not telling you to keep it. I am telling you that nobody in this story ever made that decision. It got made anyway.

[ONE sentence. Do not expand — it is a different talk:]
And if you're thinking "the supervisor was rubber-stamping it anyway" — probably. Which
means we automated the process on the wiki, not the one people were actually running.

FOR THE ENGINEERS — take the laugh, then generalize. ~45 seconds. This is one of only three planned laughs in the deck (D-54); do not add a fourth here.

Same story, different vocabulary. Somebody asks: how do we keep these two services consistent?

And AI gives you a BEAUTIFUL plan. Kafka. An outbox table. Idempotency keys. Retries with backoff. A dead-letter queue.

[beat]

And a runbook for the dead-letter queue.

[beat — let it land]

And I'll be honest with you: that is a genuinely fun afternoon. I would enjoy building that. Some of you are enjoying it right now, just hearing the list.

[beat]

Nobody asked why these two services need a long-distance relationship.

[Then straight to the principle, no dwelling — the laugh is the delivery mechanism, not the point:]

CAP didn't change. If the boundary is real, every one of those things is real and you need all of it. But the boundary was a design choice somebody made in a meeting, and the excellent answer to "how do we keep these consistent" never once asks why there are two.

THE RULE FOR THIS JOKE (D-54): the target is our own appetite for complexity — mine included. Never a role, never a team. The moment it points at architects or finance or PMs it stops being solidarity and starts being contempt, and the room goes with it.
```


## Slide 10 · The constraint might be exactly right

```
~1:00

That's the whole move. Not "approvals bad." Not "microservices bad." Not "less AI."

A question can quietly contain a decision before the AI ever answers it. And
because the answer is so good, the decision never gets examined — the quality of
the answer becomes evidence that the question was right.

Which, by the way, is exactly the failure mode I'd be reproducing if I built a
very sophisticated talk and treated its sophistication as proof the framing
was correct.

And this is not just a legacy problem. It's worse on greenfield.
```


## Slide 11 · Greenfield: how should we build our agent?

```
~1:30

Here's the greenfield version, and I think it's more dangerous because there's
no legacy system to blame.

Read it. It sounds like the beginning of a design conversation.

It's the end of one.

[click]

We decided "agent" before we said a single word about the problem. Everything
downstream — the framework evaluation, the tool-calling design, the eval
harness, six months of roadmap — is now in service of a noun somebody typed
without noticing.
```


## Slide 12 · The problem underneath

```
~2:00

Same business, same money, different question.

[click 1] And now the option space opens up. AI in the loop with a human.
Classification plus a boring deterministic workflow — which is frequently the
right answer and nobody gets to give a conference talk about it. Or maybe the 18
minutes is four minutes of work and fourteen minutes of the agent hunting through three
systems for the customer's order history — in which case what you needed was one screen,
not an agent.

[Deliberately NOT another approval story. Trap 2 has already spent three and a half
minutes on an approval chain; repeating it here makes the greenfield example read as the
same joke told twice. This one has to be a different KIND of hidden decision — slide 9
was a question that assumed a policy, this is a question that assumed a solution.]

Or a fully autonomous agent.

[click 2] And genuinely — maybe the agent wins. Maybe it's obvious. Great.

The point isn't less AI. The point is that it won on the merits instead of
sneaking in through the phrasing of a question.
```


## Slide 13 · Ask it to attack your framing

```
~1:30

This is a Monday-morning thing, and it's a positive use of AI, not a warning
about it.

Before you ask AI for the design, spend ninety seconds asking it to attack the
question.

[clicks]

I do this now and it is regularly annoying, which is how I know it's working.
Last time it told me that the word "sync" in my question had already committed
me to a direction I hadn't thought about.

[click 4] The tool will not do this on its own. Ask a leading question, get a
led answer. It is extremely agreeable and that is the failure mode.
```


## Slide 14 · Infer vs Enforce

```
~2:00

This is the same question — what did the framing already decide — applied to a choice we make constantly without naming it.

Left: there are things that are cheap to say precisely and cheap to check. You cannot refund more than someone paid. That's an invariant. Write it down, assert it, done. Handing that to a model to judge is strictly worse in every dimension: slower, more expensive, and less reliable.

[click 1] Right: and then there are things that technically have rules, but the rules live in fifteen years of tribal knowledge across four teams, two of which no longer exist. You could write them down. It would take a year and be stale in a month.

That is a legitimately excellent place for inference plus review.

[click 2] Infer what you must, enforce what you can — but do NOT hear that as "enforce everything you possibly can." Enforcement is not free. Every rule you encode is rigidity you carry, false rejections your team works around, and one more thing to maintain. There are systems in this room that are slow because somebody enforced everything they could.

TRANSITION — this is now the last slide of Trap 2, so it carries the handoff:
So that's the answer, and that's the question. Now something more personal. If AI can explain unfamiliar systems, generate the code, and challenge the architecture this fast — what does that do to how WE learn?
```


## Slide 15 · TRAP 03 intro

```
~0:30

Give this room.

This one is deliberately uncomfortable and I'm including it because I have
caught myself doing the second one — recently, and more than once.

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
~2:00

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

TRANSITION:
Alright. Suppose all of this works and we really are dramatically faster. Now what?
```


## Slide 19 · TRAP 04 intro

```
~0:30

QUALIFY THIS IMMEDIATELY AND OUT LOUD:

"And sometimes more is exactly what you should do."

Otherwise this reads as anti-productivity and half the room stops listening.
```


## Slide 20 · AI gave you capacity

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


## Slide 21 · If developers are 2x as productive

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


## Slide 22 · What got faster? (pipeline + metrics)

```
~2:30

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

TRANSITION:
One more change. So far AI has mostly been handing us things. Answers. Code. Designs. Increasingly, it doesn't hand you the thing. It just does it.
```


## Slide 23 · TRAP 05 intro

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


## Slide 24 · Authority ladder

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


## Slide 25 · Prompt injection

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

TRANSITION — straight into the next slide, no pause. The next slide is the answer to the sentence you just said:
The question is what it can do when that happens.
```


## Slide 26 · Q: What can it do when it's wrong?

```
~2:00

Not "can AI be wrong." Everything is wrong sometimes. Humans are wrong. Future models will be much better than today's and this question does not go away — it gets more important, because we'll grant more authority.

Three follow-ups, and they're the ones you already use for everything else:

How bad is it? A wrong draft sitting in a queue is not a wrong wire transfer.

Will we notice? — and this is the one I want to dwell on. Our entire monitoring tradition is built on things that break loudly. Exception, crash, timeout, p99. AI failure doesn't look like that. AI failure looks like: the operation completed successfully, and what it did was wrong. Nothing threw. Every dashboard is green. That's the whole problem.

For AI systems, "nothing threw an exception" is an especially weak definition of success.

Can we undo it? Reversibility buys you more than almost any control does.

AND — do not gold-plate. Controls are not free either. They cost latency, flexibility, engineering time, and customer experience. If the consequence is small and reversible, let the system move. "Yeah, that might break, and we're fine with that" is a legitimate engineering conclusion. Deliberately accepting risk is engineering.

I don't want to replace AI maximalism with governance maximalism.
```


## Slide 27 · 10,000 decisions / which 100?

```
~1:30

Here's the arithmetic nobody does.

[click 1] You will not get more than about a hundred genuinely careful human reviews out of a week. That's a real number about human attention, not a budgeting problem.

[click 2] So: which hundred?

"Keep a human in the loop" is not an answer to that question. A person clicking Approve two thousand times is not supervision — it's a signature, and everyone in this room has been that person.

Oversight does not scale just because action scaled.

BRIEFLY — say these, don't slide them:
There are real mechanisms. Enforceable authorization and least privilege, so the blast radius is bounded whether or not anyone is watching. Automated checks. Sampling. Anomaly detection. Outcome monitoring rather than execution monitoring. Traceability. And a stop button that actually stops things.

And AI can do a lot of this work itself. The point is not humans supervising machines — that framing loses eventually. The point is designing accountability that scales with authority.

If you take one thing from Trap 5: authority and oversight should grow together. Right now we are very good at scaling one of them.
```


## Slide 28 · Five questions for Monday

```
~2:30

That's it. That's the talk.

[reveal one at a time, say each one, brief callback to its trap]

1 — A great answer isn't evidence. What do we actually know?
2 — The question can decide the answer. What did ours already decide?
3 — Offload the work, not the understanding.
4 — Capacity is not a plan.
5 — Authority is the thing that changed, not intelligence.

If one of these makes you stop and ask a better question a month from now, this
was worth your evening.
```


## Slide 29 · Sowell callback

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


## Slide 30 · The goal isn't maximum AI

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
