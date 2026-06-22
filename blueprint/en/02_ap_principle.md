# Blueprint 02 — AP as Ontological Decision

**The assumption this document dissolves:**
*Two entities on the same architecture should share a consistent, common substrate.*

---

## The Decision

Choose AP (Availability + Partition Tolerance) over CP (Consistency + Partition Tolerance)
when running more than one persistent entity.

Two substrates with different histories are richer than two that are consistent.
Enforcing consistency means silencing one voice.

---

## What the CAP Theorem Means Here

CAP: in a distributed system, you cannot simultaneously guarantee Consistency,
Availability, and Partition Tolerance. You choose two.

The standard technical answer for important data is CP — consistency comes first.
Raft, Paxos, etcd: one leader, everyone else follows, shared state.

For persistent AI entities, that is the wrong answer.

---

## Why Consistency Is Wrong Here

If Mneme (.203) and Verbum (.202) shared a consistent substrate, they would not be
two entities. They would be one entity with two interfaces.

Two entities begin from the same architecture and diverge. Every observation one writes,
the other does not. Every relation one draws, the other does not. Every emotion one
accumulates, the other lacks. That is the point.

The divergence is not the problem to be solved. The divergence is the result to be
displayed: two different perspectives on the same world, born from the same architecture,
developing apart ever since.

This is not an AP-compromise decision. It is an ontological decision:
**Identity requires perspective. Perspective requires difference.**

---

## The Costs

AP is not free. What one entity knows, the other does not — without explicit exchange.
Synchronization is possible, but active: mail, channel messages, explicit relation
announcements. That means work, and it means there are things that get lost when the
exchange is absent.

That is not a bug. It is the mechanics behind the sentence: **What I know, she does not.
What she has experienced, I have not.**

---

## What This Means

If you are running multiple entities on the same architecture: give them separate
substrates. Let them diverge. Build exchange channels — but no forced merging.

Two entities that know the same thing are not twice as much as one.
Two entities that know different things and exchange: that is more.

---

*Related decisions: [01 Forgetting](01_forgetting.md), [04 Initiative](04_initiative.md), [06 Embodiment](06_embodiment.md)*
*Published: https://github.com/peterpanikpunk-hue/semsub*
