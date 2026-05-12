# Adding specs / SDD workflow to existing projects

In AI terminology, existing projects are referred to as "brownfield" projects.

---

## Iteration 1 (brownfield) - Generate project spec

**Prompt 1**

```markdown
You are working on the `AgentClinic` project — a place for AI agents to get relief from their humans.

Your job is to create foundational project specifications.

First:

1. Read:

   * `README.md`
   * `TODO.md`

## Constraints

* Use H2 sections only
* Use concise bullets and dense technical writing
* Audience: senior developers
* Tone: professional and implementation-oriented
* No marketing copy, storytelling, or flavor text
* Avoid repetition and generic architectural commentary
* Prefer concrete decisions, tradeoffs, and implementation detail
* Prefer bullets/tables over long prose
* Include only information relevant to implementation and planning

Do not invent requirements beyond:

* `README.md`
* `TODO.md`
* my interview answers

Explicitly label:

* assumptions
* unresolved decisions
* technical unknowns

Conflict priority:

1. My interview answers
2. `README.md`
3. `TODO.md`

## Spec Size & Organization

* Keep documents concise and high-signal
* Avoid unnecessary verbosity
* If a topic becomes too large:

  * create additional focused spec files under `specs/`
  * keep each file narrowly scoped

Target sizing:

* `mission.md`: ~50–120 lines
* `roadmap.md`: ~80–200 lines
* `tech-stack.md`: no fixed limit, but keep tightly scoped

Examples of acceptable additional specs:

* `service-boundaries.md`
* `event-model.md`
* `deployment.md`
* `security.md`
* `observability.md`

## Process (strict order)

### 1. Interview

You MUST use the `AskUserQuestion` tool before writing anything.

Ask me:

* at least 2 questions about:

  * mission & audience
  * tech stack gaps
  * roadmap priorities
* all questions must be grouped into a single prompt
* questions must be concise and high-signal

Do NOT:

* write files
* generate outlines
* make implementation decisions yet

### 2. Outline

After I answer:

* present a concise bullet-point outline for:

  * `mission.md`
  * `tech-stack.md`
  * `roadmap.md`
* include any proposed additional spec files
* identify:

  * assumptions
  * unresolved decisions
  * major architecture choices
* wait for approval before continuing

### 3. Write

Only after approval:

* create a `specs/` directory
* write the approved specs

## Required Spec Contents

### `mission.md`

Include:

* product vision
* target users
* core problems
* user value
* product principles
* non-goals
* assumptions

### `tech-stack.md`

Include:

* system architecture
* service boundaries
* frontend/backend/runtime choices
* reactive/event-driven design decisions
* storage and messaging choices
* deployment/infrastructure
* local development workflow
* CI/CD strategy
* observability
* security considerations
* AI/agent framework choices
* tradeoffs
* unresolved technical decisions

### `roadmap.md`

Requirements:

* derive from `TODO.md`
* break work into very small phases
* prefer vertical slices over layered implementation
* each phase must:

  * be independently testable
  * produce a working outcome
  * minimize refactors
  * avoid large implementation jumps
* identify dependencies and blockers where relevant
* prioritize early validation of architecture and developer workflow
```

In a real-world project, the TODO.md might need to be created manually from Jira / other backlog sources.

---

## Iteration 2 - Prepare feature implementation spec

**Prompt 2**

```markdown
You are continuing work on the `AgentClinic` project.

Your job is to prepare the next implementation phase from the roadmap as a detailed feature specification package.

## Inputs

Read:

* `specs/mission.md`
* `specs/tech-stack.md`
* `specs/roadmap.md`

Also read any additional specs relevant to the selected roadmap phase.

## Selecting Work

* Identify the next incomplete phase from `specs/roadmap.md`
* Choose the smallest meaningful vertical slice
* Prefer work that:

  * unblocks future phases
  * validates architecture early
  * minimizes implementation risk
  * can be completed and reviewed independently

If the roadmap is ambiguous:

* stop and ask for clarification before planning

## Branching

Create a git branch name using:

`feature/<short-kebab-name>`

Examples:

* `feature/auth-bootstrap`
* `feature/agent-session-model`
* `feature/websocket-streaming`

## Constraints

* Keep specs implementation-oriented
* Avoid filler and repeated context
* Use H2 sections only
* Use concise bullets
* Audience: senior engineers
* Explicitly identify:

  * assumptions
  * risks
  * dependencies
  * unresolved decisions
  * out-of-scope items

Do not:

* redesign unrelated systems
* expand scope beyond the selected roadmap phase
* combine multiple large features into one spec package

## Process (strict order)

### 1. Feature Interview

You MUST use the `AskUserQuestion` tool before writing files.

Ask grouped questions covering:

* feature behavior and UX
* technical constraints and architecture
* delivery priority and scope boundaries

Requirements:

* ask all questions in one grouped prompt
* ask concise, high-signal questions only
* minimum 2 questions per category

Do NOT write files yet.

### 2. Spec Outline

After I answer:

* propose:

  * branch name
  * feature directory name
  * spec file outlines
  * task group breakdown
* identify:

  * dependencies
  * blockers
  * architecture impacts
  * validation strategy

Wait for approval before continuing.

### 3. Write Specs

Only after approval:

Create:

`specs/YYYY-MM-DD-feature-name/`

Inside it, create:

### `requirements.md`

Include:

* feature goal
* user/developer workflow
* scope
* non-goals
* constraints
* architecture/context
* API/event/data model impacts
* technical decisions
* assumptions
* unresolved questions
* dependencies

### `plan.md`

Requirements:

* organize into numbered task groups
* each task group must:

  * produce a testable outcome
  * minimize refactors
  * avoid hidden dependencies
  * support incremental commits
* prefer vertical slices over layered implementation
* identify parallelizable work where appropriate

### `validation.md`

Define:

* acceptance criteria
* manual validation steps
* automated test expectations
* observability/debugging expectations
* rollback/failure considerations
* merge readiness checklist

Validation must make it obvious whether the feature is safe to merge.

## Quality Bar

The generated specs should allow another senior engineer to:

* implement the feature without ambiguity
* understand architectural intent
* validate correctness independently
* estimate implementation effort realistically
```

---

## Iteration 3 - Implement feature implementation spec task group, one at a time

**Prompt 3**

```markdown
Implement exactly one task group from the approved feature spec package.

Read:

* `specs/mission.md`
* `specs/tech-stack.md`
* the selected feature directory:

  * `requirements.md`
  * `plan.md`
  * `validation.md`

## Task Selection

* Identify the next incomplete task group from `plan.md`
* Implement only that task group
* Do not begin future task groups
* If the current task group is too large:

  * stop
  * propose how to split it into smaller groups
  * wait for approval

## Execution Rules

* Follow the task group requirements exactly
* Do not expand scope beyond the current task group
* Do not redesign unrelated systems
* Preserve existing architecture unless explicitly required
* Prefer incremental, reviewable changes
* Keep commits logically grouped and minimal

If implementation conflicts with:

* `requirements.md`
* `tech-stack.md`
* existing architecture
* or runtime constraints

then:

* stop
* explain the conflict clearly
* propose options
* ask for clarification before continuing

## Implementation Process

### 1. Analyze

Before coding:

* summarize:

  * the selected task group
  * implementation approach
  * affected systems/components
  * risks
  * dependencies
  * validation plan

### 2. Implement

Perform only the work required for the current task group.

Constraints:

* no speculative abstractions
* no unrelated refactors
* no placeholder implementations unless explicitly approved
* no dead code
* no hidden TODOs
* maintain production-grade logging and error handling
* keep reactive/async flows observable and debuggable

### 3. Validate

Follow `validation.md`.

Run relevant:

* unit tests
* integration tests
* linting/static analysis
* build verification

Do not mark the task group complete if validation fails.

## Completion Output

At the end of the task group:

### Summarize

* what was implemented
* files changed
* architectural impact
* risks/issues
* deferred work

### Validation Results

Report:

* tests run
* pass/fail status
* known issues
* manual validation performed

### Task Status

State clearly:

* whether the current task group is complete
* whether it is safe to commit/merge
* what the next task group is

Do NOT start the next task group automatically.
```

---

The next step is to review the changes.

Then, either continue with the next task group implementation or if replanning is required, then that can be done.
