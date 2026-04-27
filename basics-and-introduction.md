# Spec-Driven Development with Coding Agents

> Course link: https://www.deeplearning.ai/short-courses/spec-driven-development-with-coding-agents/

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


