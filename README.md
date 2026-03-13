# AI Agent Infrastructure

This repository documents a sanitized version of a self-hosted multi-stage agent system used to generate, validate, preview, and version website changes.

The real system runs on private infrastructure and private repositories.  
This public repository exists to document the architecture and workflow without exposing secrets, internal credentials, or sensitive deployment details.

---

## Project Goals

- explore modular AI agent orchestration
- build practical self-hosted automation
- validate generated changes before promotion
- use Git as a review boundary between agent output and stable code
- document the architecture in a safe public form

---

## Public / Private Separation

This project is intentionally split into different layers:

### Private repositories

Private code and runtime details are kept outside this repository, including:

- the real orchestrator and worker code
- private deployment details
- credentials
- internal runtime configuration
- repository access keys

### Public sanitized repository

This repository documents:

- architecture
- workflow
- design choices
- learning notes
- safe examples of the review pipeline

---

## High-Level Workflow

The system follows a staged pipeline:

1. research
2. development
3. QA validation
4. preview deploy
5. Git preview branch creation
6. human review
7. merge into the stable branch

This makes generated output reviewable before it is accepted into the stable version of the project.

---

## Git-Based Review Model

One important design decision is the use of a Git branch per job.

Example pattern:

- `agent/<task-slug>-<job-id>`

Examples:

- `agent/homepage-1234abcd`
- `agent/minecraft-section-a1b2c3d4`
- `agent/fix-navbar-98ef7612`

This keeps each agent-generated change isolated and easier to review.

---

## Preview Strategy

Before a change is accepted, the system deploys a preview version locally on the self-hosted environment.

That preview can then be tested before merge.

Conceptually:

- agents generate files
- QA validates the output
- preview deploy publishes a temporary version
- Git records the result in an isolated branch
- a human decides whether the branch should be merged

---

## Repository Roles

In the current architecture there are distinct repositories for different purposes:

- private agent system repository
- private or controlled website repository
- public sanitized documentation repository

This separation reduces risk and improves clarity.

---

## Status

This project is already past the purely conceptual stage.

The documented workflow has been successfully exercised in practice with:

- per-job preview generation
- staged validation
- branch creation per job
- automated Git operations
- human-controlled review before merge

