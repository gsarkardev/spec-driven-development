# Spec-Driven Development with Coding Agents

## Metadata

Course link: https://www.deeplearning.ai/short-courses/spec-driven-development-with-coding-agents/

Git repo: https://github.com/https-deeplearning-ai/sc-spec-driven-development-files

## Benefits of Specs in SDD

- Control huge codebases and feature code with simple, small changes to spec.
- Eliminates context decay: As the coding agent implements a feature, its context window fills up, often leading to more mistakes as the agent tries to work with an almost full memory. Specs persist between sessions and even agents, anchoring the agent to the core context needed to work in a code base and implement a feature.
- Improve content fidelity: With specs, the coding agent is more likely to generate code that is inline with the goals. This is because specs force the developer / *architect* to define the goals, problem, success criteria, constraints, user flows and so on.

> Specs should contain lots of details about the goals, mission, target audience and constraints and less about low level decisions, which the agent can figure out on its own.

## SDD workflow

*First, we specify the Constitution.*

A **Constitution** comprises of 3 things:
- Mission
- Tech stack
- Roadmap

A Constitution is just one way to formalize these project level details. Many developers use a top level `agents.md` file for this purpose. It is **agent-agnostic** and very structured. Most importantly, **a Constitution captures the agreement on key decisions between the human and the agents and also between the humans as well.**

### Mission

- Why?
- Vision
- Scope
- Audiences

### Tech stack

- Targeted to the engineering team
- Provides understanding for the development and deployment technologies and constraints.

### Roadmap

- Living document with a sequence of phases, often breaking down a project into feature-specific specs.
- Updated as "replanning" occurs while development is in progress.
- Translates high level goals into actionable technical tasks or user stories.

**Once the constitution has been drafted, we work on each feature with a repeatable process.**

- Plan the feature using spec documents
- Implement the feature using spec
- Validate the feature as outlined in the spec

In between features, it's time for the replanning phase. In the replanning phase, we revise the constitution, update the roadmap and even improve the process itself. In the feature and replanning phases, developers **steer** the agent.

## The Developer (*read: Architect*) role:

- Design
- Supervise
- Review
- Accept / Reject changes.
- Avoid telling the agent low-level implementation details. If absolutely required, add it as a constraint in the spec document itself.

## Tools

Any editors / CLI agents work. SDD isn't tied to any specific tool / IDE.

Similarly, any coding agent works.

*Created specs travel and remain valid even after switching tools / agents.*
