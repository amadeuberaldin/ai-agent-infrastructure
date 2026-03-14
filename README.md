# AI Agent Infrastructure

This repository documents a sanitized version of a self-hosted multi-stage agent system used to generate, refine, validate, preview, and version website changes.

The real system runs on private infrastructure and private repositories.  
This public repository exists to document the architecture and workflow without exposing secrets, internal credentials, or sensitive deployment details.

---

## Project Goals

- explore modular AI agent orchestration
- build practical self-hosted automation
- generate reviewable website changes
- use Git as a review boundary between agent output and stable code
- improve output quality through planning and refinement stages
- document the architecture in a safe public form

---

## Public / Private Separation

This project is intentionally split into different layers.

### Private repositories

Private code and runtime details are kept outside this repository, including:

- the full orchestrator and worker implementation
- deployment details
- credentials
- API keys
- private repository access configuration

### Public sanitized repository

This repository documents:

- architecture
- workflow
- design decisions
- learning notes
- safe examples of the agent pipeline

---

## High-Level Workflow

The current website-generation workflow follows these stages:

1. research
2. design planner
3. development
4. UI refinement
5. QA validation
6. preview deploy
7. Git preview branch creation
8. human review
9. merge into the stable branch

This makes generated output reviewable before it is accepted into the stable version of the project.

---

## Why the extra stages matter

A major improvement in the system came from splitting generation into multiple quality-focused steps.

### Design planner

The design planner generates a structured visual plan before code is written.

It helps define:

- visual theme
- page sections
- UI direction
- emphasis areas
- interface notes

### UI refiner

The UI refiner improves the first generated version by focusing on:

- spacing
- hierarchy
- typography
- cards
- buttons
- overall polish

This made the generated pages significantly more professional.

---

## Git-Based Review Model

One important design decision is the use of a Git branch per job.

Pattern:

- `agent/<task-slug>-<job-id>`

Examples:

- `agent/homepage-1234abcd`
- `agent/minecraft-section-a1b2c3d4`
- `agent/fix-navbar-98ef7612`

This keeps each agent-generated change isolated and easier to review.

---

## Preview Strategy

Before a change is accepted, the system deploys a preview version on the self-hosted environment.

Conceptually:

- agents generate files
- QA validates the output
- preview deploy publishes a temporary version
- Git records the result in an isolated branch
- a human decides whether the branch should be merged

---

## Reliability Improvements

Recent iterations added stronger controls to improve trustworthiness:

- preserving the correct site owner identity
- avoiding invented metrics
- avoiding invented clients
- avoiding fabricated work history
- enforcing backend consistency

---

## Repository Roles

In the current architecture there are distinct repositories for different purposes:

- private agent system repository
- website repository
- public sanitized documentation repository

This separation reduces risk and improves clarity.

---

## Status

This project is already past the purely conceptual stage.

The documented workflow has been successfully exercised in practice with:

- per-job preview generation
- staged design planning
- UI refinement
- staged validation
- branch creation per job
- automated Git operations
- human-controlled review before merge

