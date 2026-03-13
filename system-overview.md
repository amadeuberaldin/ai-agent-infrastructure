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
Development
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

## Public Documentation Scope

This public repository intentionally omits:

- credentials
- internal IPs
- private repository URLs beyond what is already public
- private infrastructure details
- secret runtime configuration

Its role is to communicate the architecture and lessons learned without exposing sensitive operational details.

