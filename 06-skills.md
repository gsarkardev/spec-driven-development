# Using skills for custom workflows

**Refer:** https://agentskills.io/home

> Agent skills are a standardized way to give AI agents new capabilities and expertise. They are a lightweight, open format for extending AI agent capabilities with specialized knowledge and workflows.

At its core, a skill is a folder containing a `SKILL.md` file. This file includes metadata (`name` and `description`, at minimum) and instructions that tell an agent how to perform a specific task. Skills can also bundle scripts, reference materials, templates, and other resources.

```
my-skill/
├── SKILL.md          # Required: metadata + instructions
├── scripts/          # Optional: executable code
├── references/       # Optional: documentation
├── assets/           # Optional: templates, resources
└── ...               # Any additional files or directories
```

It is usually recommended to keep skills outside project folders, on the same level. If projects are in `~/git/todoerv2/`, then skills can be stored in `~/git/agent-skills`.

The important architectural distinction is:

- global skills = reusable workflow protocols
- repo-local specs = project knowledge/state

---

## Iteration 1 (Create the skill)

**Prompt 1**

```markdown
I want to stop repeating my feature-spec workflow prompts.

Use your skill creator to help me create a reusable local skill named:

`feature-spec`

Purpose:
Generate implementation-ready feature specification packages for the next roadmap phase of a software project.

The skill should encode a strict multi-phase workflow for:

* selecting the next roadmap slice
* interviewing for feature requirements
* proposing outlines
* waiting for approval
* generating spec artifacts

The generated skill must:

## Inputs

Read:

* `specs/mission.md`
* `specs/tech-stack.md`
* `specs/roadmap.md`
* any additional specs relevant to the selected roadmap phase

## Workflow

### 1. Select Work

* identify the next incomplete roadmap phase
* choose the smallest meaningful vertical slice
* avoid combining multiple large features
* prioritize:

  * architecture validation
  * low-risk iteration
  * independent testability
  * unblockers

If roadmap ambiguity exists:

* stop and ask for clarification

### 2. Interview Phase

Before writing files:

* MUST use `AskUserQuestion`
* ask grouped questions covering:

  * feature behavior and UX
  * technical constraints and architecture
  * delivery priority and scope boundaries
* ask at least 2 concise questions per category
* ask all questions in a single grouped prompt

### 3. Outline Phase

After interview answers:

* propose:

  * branch name
  * feature directory name
  * spec outlines
  * task group breakdown
* identify:

  * dependencies
  * blockers
  * architecture impacts
  * unresolved decisions
  * validation strategy

Then:

* wait for approval before writing files

### 4. Spec Generation

Only after approval:

Create:

`specs/YYYY-MM-DD-feature-name/`

Generate:

#### `requirements.md`

Include:

* feature goal
* workflows
* scope
* non-goals
* architecture impacts
* API/event/data model changes
* technical decisions
* assumptions
* unresolved questions
* dependencies

#### `plan.md`

Requirements:

* numbered task groups
* independently testable increments
* vertical slices preferred
* minimal refactors
* incremental commit-friendly structure
* identify parallelizable work where relevant

#### `validation.md`

Include:

* acceptance criteria
* manual validation steps
* automated testing expectations
* observability/debugging expectations
* rollback/failure considerations
* merge readiness checklist

## Constraints

* implementation-oriented writing only
* concise bullets
* H2 sections only
* senior engineer audience
* no filler or marketing language
* no speculative redesigns
* avoid generic architecture commentary
* explicitly label:

  * assumptions
  * risks
  * unresolved decisions
  * dependencies
  * out-of-scope items

## Success Criteria

The generated spec package should allow another senior engineer to:

* implement without ambiguity
* validate independently
* estimate effort realistically
* understand architectural intent

The skill should optimize for long-term maintainability of a complex microservice/cloud/reactive system.
```

---

## Iteration 2 (Invoke the skill workflow)

**Prompt 2**

```markdown
Use the `feature-spec` skill for this repository.

Identify the next incomplete roadmap slice and execute the skill workflow exactly as defined.
```

### Targeting / focusing on specific task groups

**Prompt 2.1**

```markdown
Use the `feature-spec` skill for this repository.

Target roadmap item:
`<paste roadmap phase or task here>`

Execute the workflow exactly as defined.
```

---

## Agent replaceability

Specs are not tied to any specific coding agent. Once created, they can be used by any other agent to implement the SDD workflow.

For example, if the above skill was created in Claude, that same skill can be invoked using the same prompt by another agent. The only thing to note is, different agents have different skill directory conventions, and the specs / skills may need to be copied to that specific agent's configured directory.

---

## Further reading

- MCP protocol
- MCP + CLI skills
- Claude Code plugins
- Github spec kit / Fission AI open spec
