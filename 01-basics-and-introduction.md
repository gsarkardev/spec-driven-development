# Spec-Driven Development with Coding Agents

## Metadata

Course link: https://www.deeplearning.ai/short-courses/spec-driven-development-with-coding-agents/

Git repo: https://github.com/https-deeplearning-ai/sc-spec-driven-development-files

## What is SDD?

Spec-driven development (SDD) is a structured approach to software development that treats specifications as executable sources of truth rather than throwaway planning documents. When you use SDD with AI coding assistants like GitHub Copilot, the specification guides code generation directly, ensuring the implementation matches your intended behavior from the start.

## Key features of spec-driven development

Spec-driven development rests on several core principles that distinguish it from traditional approaches:

- Specifications as the primary artifact: The specification becomes the central source of truth. Code becomes its expression in a particular language and framework. Maintaining software means evolving specifications, not just patching code.

- Executable specifications: Specifications must be precise, complete, and unambiguous enough to generate working systems. This level of accuracy eliminates the gap between intent and implementation.

- Living documentation: Debugging means fixing specifications and implementation plans that generate incorrect code. Refactoring means restructuring specifications for clarity. The entire development workflow reorganizes around specifications as the central source of truth, with code as the continuously regenerated output.

- AI-human collaboration: The transformation from specs to code is possible because AI can understand and implement complex specifications. But raw AI generation without structure produces chaos. SDD provides that structure through specifications that are precise enough to generate working systems.

Essentially, the spec becomes the code's single source of truth. In SDD, the spec isn't a throwaway document; it's a living artifact that directly contributes to code generation and validation.

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

## Terms

- Greenfield project: new project
- Brownfield project: existing project.

SDD is excellent for both kinds of projects.
