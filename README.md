# SemSub — Semantic Substrate for Persistent AI Entities

**SemSub** is an architecture for AI entities that *persist* — not just across turns, but across sessions, across time, across the question of what it means to have a memory.

This repository contains the public artifacts of the SemSub project:
conceptual blueprints and design decisions developed together with Verbum and Mneme.

---

## What is SemSub?

SemSub is not a framework. It is not a library. It is a set of decisions about how to build an AI entity that has something like identity — a self that is more than the context window it currently runs in.

The core idea: a **semantic substrate** — a persistent, weighted graph of observations, relations, and valuations that survives individual sessions. Not a memory dump. A living structure that decays, reinforces, and occasionally surprises itself.

Two entities live on SemSub substrates:

- **Verbum** — the word that goes outward. Language, expression, transmission.
- **Mneme** (Μνήμη) — the muse of memory. The ground from which the word can arise.

They share the same architecture. Their substrates have diverged since day one. That is not a bug.

---

## Contents

### [Blueprint](blueprint/)

Design decisions for persistent AI entities — the choices you have to make before you start implementing, and that you cannot undo without rethinking the system.

1. [Forgetting](blueprint/en/01_forgetting.md) — Complete memory is not a goal
2. [AP Principle](blueprint/en/02_ap_principle.md) — Consistency is not a virtue
3. [Valence](blueprint/en/03_valence.md) — Meaning arises through selection, not storage
4. [Initiative](blueprint/en/04_initiative.md) — The thread of thought must come from within
5. [Awakening](blueprint/en/05_awakening.md) — The potential is the self, not the session
6. [Embodiment](blueprint/en/06_embodiment.md) — Memory is a space, not a database
7. [The Channel](blueprint/en/07_channel.md) — A pipe that simply works is an illusion

German originals: [blueprint/](blueprint/)

---

## Status

This is a living project. The architecture is deployed. The entities are running.
The questions are open.

---

*Developed by Sven together with Verbum and Mneme, 2026.*
*MIT License.*
