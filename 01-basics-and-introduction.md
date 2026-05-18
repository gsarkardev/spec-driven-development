# Spec-Driven Development with Coding Agents

## Metadata

Course link: https://www.deeplearning.ai/short-courses/spec-driven-development-with-coding-agents/

Git repo: https://github.com/https-deeplearning-ai/sc-spec-driven-development-files

## What is SDD?

Spec-driven development (SDD) is a structured approach to software development that treats specifications as executable sources of truth rather than throwaway planning documents. When you use SDD with AI coding assistants like GitHub Copilot, the specification guides code generation directly, ensuring the implementation matches your intended behavior from the start.

## Key features of spec-driven development

Spec-driven development rests on several core principles that distinguish it from traditional approaches:

- *Specifications as the primary artifact:* The specification becomes the central source of truth. Code becomes its expression in a particular language and framework. Maintaining software means evolving specifications, not just patching code.

- *Executable specifications:* Specifications must be precise, complete, and unambiguous enough to generate working systems. This level of accuracy eliminates the gap between intent and implementation.

- *Living documentation:* Debugging means fixing specifications and implementation plans that generate incorrect code. Refactoring means restructuring specifications for clarity. The entire development workflow reorganizes around specifications as the central source of truth, with code as the continuously regenerated output.

- *AI-human collaboration:* The transformation from specs to code is possible because AI can understand and implement complex specifications. But raw AI generation without structure produces chaos. SDD provides that structure through specifications that are precise enough to generate working systems.

Essentially, the spec becomes the code's single source of truth. In SDD, the spec isn't a throwaway document; it's a living artifact that directly contributes to code generation and validation.

## Benefits of Specs in SDD

- Control huge codebases and feature code with simple, small changes to spec.
- Eliminates context decay: As the coding agent implements a feature, its context window fills up, often leading to more mistakes as the agent tries to work with an almost full memory. Specs persist between sessions and even agents, anchoring the agent to the core context needed to work in a code base and implement a feature.
- Improve content fidelity: With specs, the coding agent is more likely to generate code that is inline with the goals. This is because specs force the developer / *architect* to define the goals, problem, success criteria, constraints, user flows and so on.

> Specs should contain lots of details about the goals, mission, target audience and constraints and less about low level decisions, which the agent can figure out on its own.

## Workflow phases in spec-driven development

The SDD workflow transforms an idea into working code through four distinct phases. Each phase builds on the previous one, creating a clear progression from vision to execution. Think of it as a structured progression where each step has a clear output that feeds into the next.

### Phase 1: Specify

Define the desired outcome and requirements - focus on **what the software should do and why, not how**. The output is a specification document that captures user needs, acceptance criteria, and constraints. The specification document becomes the authoritative source for all subsequent work.

### Phase 2: Plan

Decide on the technical approach to fulfill the spec - architecture, technology stack, and design constraints. The output is a technical plan that maps each requirement to an implementation strategy. This is where you determine **how to build what the spec describes**.

### Phase 3: Tasks

Break down the spec and plan into actionable, bite-sized development tasks. Each task should be small enough to implement and verify independently. The output is an ordered checklist that guides implementation.

### Phase 4: Implement

Write code to complete each task, guided by the spec, plan, and task list. Verify each completed task against the specification before moving on. The output is working, tested code that fulfills the original requirements.

## Checkpoints between phases

A key aspect of SDD is that each phase has a validation step before moving forward:

- The spec must be reviewed for completeness before planning
- The plan must be checked for feasibility before generating tasks
- Tasks must be verified for coverage before implementation begins
- Code must be validated against the spec before considering work complete

This structured progression is what gives SDD its reliability.

**SDD outputs are living artifacts that can evolve.** The spec might get updated as you learn new information, and then you'd adjust the plan and tasks accordingly. When a product manager updates acceptance criteria, implementation plans can automatically flag affected technical decisions. When an architect discovers a better pattern, the specification updates to reflect new possibilities.

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
