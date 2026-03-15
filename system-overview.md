# System Overview

This project documents a modular agent workflow that turns a user request into a reviewable website change.

---

## High-Level Flow

User request
↓
Orchestrator
↓
Research
↓
Context builder
↓
Design planner
↓
Development
↓
UI refinement
↓
QA
↓
Preview deploy
↓
Git preview branch
↓
Human review
↓
Stable branch merge

---

## Design Principles

- modular stages
- explicit handoff between steps
- preview before approval
- Git as a review boundary
- separation between public and private repositories
- sanitized public documentation

---

## Why context injection was added

A single prompt was not enough to consistently preserve site identity, editorial tone, and philosophical direction.

The architecture improved after adding a context stage before design and code generation.

That stage allows the workflow to preserve:

- who the site represents
- how the homepage should behave
- what kinds of claims must be avoided
- what belongs on the homepage versus internal pages

---

## Why planning and refinement were added

A single-step “generate the page” flow was not enough to consistently produce high-quality design.

The architecture improved after adding:

- a design planning stage before code generation
- a UI refinement stage after code generation

This produced stronger layouts and more polished results.

---

## Why Git is part of the architecture

Git is not just storage in this design.

It acts as a control point.

The system does not directly overwrite the stable version of the project.  
Instead, it creates an isolated branch for each job and lets a human decide what should be accepted.

That gives:

- traceability
- easier rollback
- safer experimentation
- cleaner history
- better learning value

---

## Branch Strategy

Pattern:

- `main` = stable branch
- `agent/<slug>-<jobid>` = generated review branch

This keeps each generated change independent.

---

## Preview Role

Preview deployment exists to answer one important question before merge:

“Does this generated change actually behave the way we expect?”

That preview-first design is one of the most important features of the system.

---

## Homepage vs Internal Pages

One important architectural lesson was that not all pages should behave the same way.

The homepage can be treated as:

- a manifesto
- a point of view
- an introduction to the mindset behind the work

Internal pages can then carry the detailed technical content.

This separation improves clarity and identity.

---

## Trustworthiness Constraints

One of the important architectural lessons was that visually strong output is not enough.

The workflow also needs constraints that preserve:

- correct identity
- factual honesty
- backend consistency
- technical guardrails
- editorial coherence

---

## Public Documentation Scope

This public repository intentionally omits:

- credentials
- internal IPs
- private infrastructure details
- private runtime configuration
- private repository access details

Its role is to communicate the architecture and lessons learned without exposing sensitive operational details.

