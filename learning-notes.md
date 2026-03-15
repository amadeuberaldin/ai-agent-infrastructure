# Learning Notes

This file contains sanitized notes from the evolution of the agent pipeline.

## Key lessons so far

- staged pipelines are easier to debug than monolithic agent flows
- a Git branch per job gives much better review control
- preview deployment before merge is extremely valuable
- human review remains important even when generation is automated
- separating public documentation from private runtime code is worth the effort

## Quality lessons

A major improvement came from splitting generation into several different quality-focused stages:

- context before planning
- planning before coding
- refinement after coding

This produced stronger visual results and more coherent content than single-step generation.

## Context lessons

Long prompts alone are not enough to preserve identity and philosophy consistently.

A persistent context layer improved generation quality by making it easier to preserve:

- correct owner identity
- editorial direction
- homepage philosophy
- content boundaries
- integrity constraints

## Git-specific observations

Using Git as a review boundary improved the system significantly.

Instead of allowing generated output to go directly into the stable branch, the system now:

- creates a branch per job
- stores the generated result there
- lets a human review the change
- only later merges into the stable branch

This reduced the risk of accidental breakage.

## Content trust lessons

Generated pages may look visually convincing while still being factually wrong.

That led to stronger rules around:

- preserving the correct owner identity
- avoiding fabricated metrics
- avoiding invented clients
- avoiding fake professional history
- keeping backend constraints explicit
- injecting persistent context before generation

## Editorial lessons

A homepage does not always need to behave like a project catalog.

In this system, the homepage became more effective when treated as:

- a manifesto
- an editorial introduction
- a philosophical starting point

Project details can then live in internal pages.

## Operational observations

The preview step made remote testing easier and more practical.

The job pipeline became more useful once it could:

- generate output
- expose a preview
- register the result in Git
- preserve stable code until human approval

## Future improvements

Potential next steps include:

- richer QA
- automated smoke checks for preview
- pull request creation
- stronger page-type awareness
- structured generation for internal content pages

