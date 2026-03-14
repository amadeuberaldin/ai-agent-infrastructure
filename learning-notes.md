# Learning Notes

This file contains sanitized notes from the evolution of the agent pipeline.

## Key lessons so far

- staged pipelines are easier to debug than monolithic agent flows
- a Git branch per job gives much better review control
- preview deployment before merge is extremely valuable
- human review remains important even when generation is automated
- separating public documentation from private runtime code is worth the effort

## Quality lessons

A major improvement came from splitting generation into two different quality-focused stages:

- planning before coding
- refinement after coding

This produced stronger visual results than single-step generation.

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
- stronger identity/context injection
- more structured content generation for real project pages

