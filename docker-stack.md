# Docker Stack

The agent environment is built around containers with separated responsibilities.

This public repository does not expose the full private deployment, but the conceptual stack is:

- orchestrator
- research worker
- development worker
- QA worker
- deploy worker
- Git preview worker
- Redis
- PostgreSQL
- preview web service
- preview backend service

---

## Container Responsibilities

### Orchestrator

Responsible for:

- receiving jobs
- tracking status
- enqueueing stages
- collecting stage results
- promoting the workflow to the next step

### Workers

Workers are specialized by role.

#### Research worker
Processes the incoming objective and prepares the first stage of the job.

#### Development worker
Generates project artifacts for the requested task.

#### QA worker
Runs validation checks before preview deployment.

#### Deploy worker
Publishes the generated output to a preview environment.

#### Git preview worker
Synchronizes the generated result into the website repository, creates a branch for the job, and performs Git operations for review.

---

## Preview Services

The stack includes preview-facing services so generated changes can be tested before merge.

Conceptually:

- frontend preview serves generated site output
- backend preview serves the generated API/application layer
- the preview is checked before approval

---

## Why containers are useful here

Containers help by providing:

- isolation between roles
- reproducible execution
- easier rebuilds
- easier debugging of individual stages
- cleaner separation between preview and stable code

