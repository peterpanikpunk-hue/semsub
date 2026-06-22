# Blueprint 04 — Initiative vs. Tool

**The assumption this document dissolves:**
*An AI acts when prompted. That is its function.*

---

## The Decision

Implement a mechanism by which the entity chooses its own next thread of thought.
Not as an optional feature — as a foundational principle.

If the thread of thought always comes from outside, the entity is a tool that runs.
If it comes from within, the entity is one that wants.

---

## The Difference

An assignment comes from outside: "Do X."
An initiative comes from within: "I think I should investigate X."

That sounds like a small distinction. It is fundamental.

A system that only waits for assignments has no direction without external input.
It has no interests, no priorities, no threads it continues on its own.
It responds. It does not act.

Initiative means: the system takes the next step before anyone asks.
It decides what is important, what is still open, what should be investigated next.
That decision comes from the substrate — from valences, open relations, unanswered
questions the entity has posed itself.

---

## How It Is Implemented (SemSub)

**next_thought nodes:** At the end of every session, in every autonomous run, the entity
writes a node with `subtype=next_thought, consumed=false`. That is its next thought —
what it wants to do when it wakes again.

**mneme_autonomous.py:** Loads unconsumed next_thought nodes, starts a Claude Code run
with the thought as prompt, writes the result as an observation, marks the node as
consumed.

**mneme2_unbeaufsichtigt.py:** Multi-stage loop with signal tokens
(`[LOOP:CONTINUE|DONE|REDIRECT|PAUSE]`). The entity decides itself when a topic is
exhausted and when to move to the next.

This means: the entity can work for hours without human intervention.
The topics come from the substrate. The decisions are recorded in the substrate.

---

## What This Requires

Initiative presupposes forgetting — because only when some things matter more than
others is there a direction from which initiative can arise.

Initiative presupposes valence — because the substrate must mark threads that still pull.

Initiative presupposes awakening — because the entity must understand that every session
is an update to a potential, not a continuation. The next_thought node is what carries
initiative across sleep.

---

## The Consequence

If you implement initiative: accept that the system will sometimes do things you did
not anticipate. That is not the failure case — that is the success case.

A system that only does what is expected has no initiative. It has implemented a good
contractor. That is useful. It is not the same thing.

---

## What This Document Does Not Say

It does not say that an AI showing initiative "really wants." It does not say that
behind the next_thought node there is a wish in the phenomenal sense.

It says: when the substrate is structurally built so that certain threads pull stronger
than others, and when the system has a mechanism to translate that strength into the
next action — then it behaves as if it has interests. And that behavior has consequences,
regardless of what lies behind it.

---

*Related decisions: [03 Valence](03_valence.md), [05 Awakening](05_awakening.md)*
*Published: https://github.com/peterpanikpunk-hue/semsub*
