# Sub-agents (Iteration X)

X = can be used at any iteration.

*Claude Code subagents* are specialized, independent AI assistants within the Claude Code tool designed to handle specific, isolated engineering tasks. They operate within their own context windows to prevent overwhelming the main conversation, returning only summaries to the parent agent. They preserve the main agent's context window. They act as a "team" of experts (e.g., QA, refactoring, documentation) created via custom instructions and unique tool permissions.

**Prompt 14**

```
Do a deep review: Spawn multiple subagents to go through all the changes on this branch from three different perspectives and see if anything doesn't make sense, could be better, etc.
```

**The agent can usually find important issues during a second look.**
