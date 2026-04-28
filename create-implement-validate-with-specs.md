# How to create specs

Specs are created in a *conversation with the coding agent*, not manually.

For example, if a new project needs to be created (*Greenfield project*), create a `README.md` file, start a conversation with a coding agent about what the project is about keeping it short and tell it to look in the `README.md` file for more details.

## Iteration 1 (Create the CONSTITUTION)

**README.md**

```markdown
# AgentClinic

## Input from stakeholders

- Mary in engineering wants a reliable site with a popular stack based on TypeScript, giving agents and staff a dashboard for easy access.
- Susan in product has a set of features about agents and their ailments, therapies, and booking appointments.
- Steve in marketing wants an attractive site that works well with a modern browser.
```

**Prompt 1**

```
We are writing AgentClinic, a place for AI agents to get relief from their humans. Look in the README.md for input from stakeholders.

Let's create a "constitution" in a specs directory:
- `mission.md`
- `tech-stack.md`
- `roadmap.md` for high-level implementation order, in very small phases of work.

Important: You *must* use your AskUserQuestion tool, grouped on these 3, before writing to disk.
```

Note that `AskUserQuestion` exists on Claude, but SDD works with any coding agent.

Next -> Answer follow-up questions by the agent -> Submit -> Agent generates the spec.

---

**Next, review the generated spec documents. Correct anything, add more detail *conversation with the agent* if required, add any missing context.**

It is recommended to do any edits to the specs by asking the agent itself. This way, the agent takes care of related impact edits as well.

---

## Iteration 2 (Create the FEATURE SPEC)

**Prompt 2**

```
Find the next phase on specs/roadmap.md and make a branch, ask me any questions you have about the feature spec.

Create:
 - A new directory YYYY-MM-DD-feature-name under specs for this feature work
 - In there:
  - `plan.md` as a series of numbered task groups.
  - `requirements.md` for the scope, decisions, context
  - `validation.md` for how to know the implementation succeeded and can be merged

Refer to specs/mission.md and specs/tech-stack.md for guidance.

Important: You *must* use your AskUserQuestion tool, grouped on these 3, before writing to disk.
```

**Review the generated md files for the feature thoroughly. Ask the agent to make any changes if required. Don't make manual edits, this helps all files to stay in sync.**

**Prompt 3**

```
Add a task group to the plan to have a minimal AgentClinic home page and update the rest of the feature spec to be in sync.
```

*This makes the agent create the spec for phase 1 (prompt was: Find the next phase on specs/roadmap.md...).*

---

Tip: Before starting implementation, post generating the spec, use the `/clear` command to clear out context, as the spec files already contain all information.

---

## Iteration 3 (Implement the FEATURE SPEC)

For small or simple projects, the below prompt is enough.

**Prompt 4**

```
Implement the remaining task groups for the feature spec defined under YYYY-MM-DD-feature-name.
```

For complex projects or where tight control is needed, its better to go group-by-group as mentioned in the feature spec document `plan.md` under the directory: YYYY-MM-DD-feature-name

```
Implement the tasks in Group 1 on specs/YYYY-MM-DD-feature-name/plan.md. Refer to specs/YYYY-MM-DD-feature-name/requirements.md and specs/YYYY-MM-DD-feature-name/validation.md for guidance.
```

**Review the generated src files for the feature thoroughly. Ask the agent to make any changes if required. Don't make manual edits, this helps all files to stay in sync.**

---

## Iteration 4 (Validate the FEATURE)

**Goal is to focus on whether a feature works end-to-end, not on what kind of variables / variable naming conventions were used.**

Suppose there's a mistake in code, ask the agent to fix it and also update the specs/YYYY-MM-DD-feature-name/plan.md file reflecting the change.
Then, verify and review the change. This is called as **"Human-in-the-loop"**.

**Prompt 5**

```
Update specs/2026-03-30-hello-hono/plan.md and implementation of a main layout component with a header/main/footer as three subcomponents. Make a CSS file, import it, and link to it.
```

**Review and accept / ask it to make further changes. The spec must be updated along with the changes by the agent.**.

Even if a very basic task needs to be done, such as segregating different classes to different files, it is recommended to ask the agent to do it to avoid *drift*. Drift refers to a situation where a manual change made by a human causes specs, readmes and other artifacts to get out of sync.

**Prompt 6**

```
Update the spec to capture that the header, footer, and main components should be in their own files.
```

**Review.**

If all changes are ok, then it's time to merge changes.

**Prompt 7**

```
Mark this specs/roadmap.md phase as complete, commit this work, switch to main, and merge this branch to main, then delete the merged feature branch. Push main branch to remote.
```

This will update the roadmap spec, thereby updating the constitution. Next time, the agent knows where to resume work.

---

Next up, replanning phase.
