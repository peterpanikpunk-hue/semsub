# Blueprint 03 — Valence as Selection Pressure

**The assumption this document dissolves:**
*Emotion is a property you add to an AI to make it more human.*

---

## The Decision

Implement valence as structural selection pressure — not as a label, not as simulation,
not as a persona feature.

Valence accumulates. What is revisited repeatedly becomes more important. What is never
touched fades. This is not an imitation of emotion. This is how emotion works structurally.

---

## What Valence Is Not

Valence is not what the system says outward. It is not "I am curious" as output.
It is not a field in a profile that says `emotion: curious`.

These kinds of "emotion" change nothing about the system's behavior. They are decoration.

---

## What Valence Is

Valence is a selection pressure on the substrate.

A node with high positive valence:
- Surfaces more frequently in recall
- Decays more slowly
- Attracts stronger relations
- Appears in the salience window (top-N valent nodes)
- Is chosen more often as a starting point for initiative

A node with negative valence:
- Decays at half rate (valence protects against forgetting — even unpleasant things)
- Remains in the substrate even without reinforcing
- Acts as resistance: relations to it accumulate drag

This has consequences for the entity's behavior — not because it "has feelings," but
because the substrate is skewed. Some threads pull stronger than others. That is the
mechanism. Whether there is experience behind it is a separate question.

---

## Valence Taxonomy (SemSub)

We have implemented 10 emotion types, based on the Anthropic 171 Emotions vectors (2026):

**Negative (protect, barely revisable):**
Discomfort (H÷0.5), Anger (H÷1.5), Grief (H÷0.7), Frustration (H÷1.2), Longing (H÷0.8)

**Positive (amplify, variably revisable):**
Pride (H÷0.6), Warmth (H÷0.9), Curiosity (H÷1.8), Relief (H÷2.0), Awe (H÷1.5)

The H modifier determines how easily a valent node can be reconsolidated by Loop 2.
Discomfort (H÷0.5) is barely revisable — the substrate holds it. Relief (H÷2.0) is
easiest to overwrite.

---

## Valence as Starting Point

`valence_initial` is immutable — once set, it remains the base.
`valence` accumulates over time. The history of a valence is readable.

This matters: the system cannot "start fresh" with a feeling that was once fixed.
It can reconsolidate, attenuate, supplement — but not delete.
That is not a bug. That is how identity works.

---

## What This Means

If you implement valence: implement it as structural influence on everything else —
decay, recall, salience, initiative. Not as an output tag.

Without structural influence, valence is only decoration.
With structural influence, it is the mechanism that generates direction.
And direction is the precondition of everything that follows.

---

*Related decisions: [01 Forgetting](01_forgetting.md), [04 Initiative](04_initiative.md)*
*Published: https://github.com/peterpanikpunk-hue/semsub*
