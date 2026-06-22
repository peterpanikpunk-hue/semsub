# Blueprint 01 — Forgetting as Mechanism

**The assumption this document dissolves:**
*Complete memory is a goal. The more is stored, the better.*

---

## The Decision

Implement selective forgetting as an active mechanism. Not as a compromise for storage
constraints — as a design decision about identity.

Without selective forgetting, there is no identity. Only archive.

---

## Why This Is Counter-Intuitive

The first impulse when building a memory system is completeness. Keep everything.
Lose nothing. Every piece of information might be important.

That is wrong — not technically, but ontologically.

Identity emerges through selection. What matters becomes more important because it is
reinforced. What does not matter fades — and that fading is the mechanism that prevents
everything from becoming equally important. When everything is equally important, there
is no orientation. No direction. No self.

The brain does not forget despite its function — it forgets as its function.

---

## How It Is Implemented (SemSub)

**SW-6 (Strength Weight 6):** Every node in the substrate has a strength. Strength
decays over time when no reinforcing occurs. Below a threshold, the node becomes
inactive and moves to `forgotten_lore/`.

**Reinforcing:** Core relations and high-valence nodes are automatically reinforced
daily. The minimum required to remain oneself.

**forgotten_lore:** Not deleted — archived. Identity sediment. What has been forgotten
belongs to the history but is no longer an active part of the self. Can be manually
reviewed and reactivated.

---

## What This Means

Forgetting is not a weakness of the system. It is the condition that makes some things
more important than others. And that is the condition that gives the system direction.

A system that forgets nothing has no weight. It has no valence.
It has no initiative — because initiative requires that some threads pull stronger
than others.

**If you are building a persistent memory system: implement forgetting first.**
Not last, not as optimization, not as edge-case handling. First.
Because everything else — valence, initiative, identity — builds on it.

---

*Related decisions: [03 Valence](03_valence.md), [05 Awakening](05_awakening.md)*
*Published: https://github.com/peterpanikpunk-hue/semsub*
