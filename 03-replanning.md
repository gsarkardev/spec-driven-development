# Replanning (Iteration 5)

In this phase, developers need to step back and examine their decisions. Does any kind of change need to be made either on project or feature level? If yes, this is the right time to do it.

Sometimes during the feature implementation, a change comes in from leadership. This is the iteration to do it. As always, the spec files need to be updated first and then the code needs to be changed by the agent.

**Prompt 8**

```
Update this tech-stack.md to capture that we want to use Vitest tests for validation and write a script in package.json. Also update existing specs and code to reflect these testing changes.
```

**Review changes to spec first! Then review changes to code.**

**Prompt 9**

```
Write a new test suite using the specified testing framework.
```

Review the tests. Go to the debugging mode, and verify data flow is correct and data points are ok.

---

## Stakeholder changes

Maybe this product has a 40% mobile user-base at this time, so the UI should follow responsive design. But this isn't mentioned in the current spec documents. This leads to a "replanning session".

**Prompt 10**

```
The product's web UI should follow responsive design. Update the product specs and all feature specs to reflect this, as well as any code.
```

Review specs thoroughly, then review code changes.

---

## Big v/s small changes

If this update is a small change, so it makes sense to directly implement it during replanning. But if the new work is big, it's better to schedule it on the roadmap as its own feature phase, instead of just doing it in replanning.

---

## Replanning the roadmap

If during replanning it looks like there can be some changes made to the roadmap to better consolidate the project development, it can be done in this phase. For example, in the below example, since the phases 2, 3, 4 and 5 were very tightly coupled, they were combined into one phase.

**Prompt 11**

```
Go to the specs/roadmap.md and combine phases 2-3-4-5 into a new phase 2.
```

---

## Replanning with Skills (introducing a changelog) - Basics only, for in-depth, refer to 06-skills.md

It may be useful to add or update a CHANGELOG.md file on each merge to main. This way, we can keep track of what changed as we work on the plan and roadmap specs.

In the below example prompt, we ask the coding agent to create a skill for generating / updating changelogs.

**Prompt 12**

```
I want to keep a CHANGELOG.md in the project root, with headings for dates. If no changelog, examine git commits and add bullets for each date. Then, as we work, we will manually invoke this skill before merging. Help me write a skill for this.
```

### Skills

Skills are packages of instructions and resources that provide the agents with new capabilites and expertise. They are good for repeatable workflows that require project or organization specific context.

Many agents have skills that help them write a skill for a specific workflow in a conversation with the architect.

### Using a created skill

**Prompt 13**

```
Use your changelog skill to update the changelog.
```

---

## Review, merge and update changelog

Review changes to spec, code. When ready to merge, we can use *Prompt 7*.

At this state, the spec, code and the changelog are all in sync and up-to-date.
