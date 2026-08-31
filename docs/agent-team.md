# Agent team

This document describes the custom agent team used to build Mona's Project Pulse dashboard, orchestrated through GitHub Copilot CLI in a Codespace.

## Agents

### Orchestrator
- **Model:** Claude 3.5 Sonnet (copilot)
- **Responsibility:** Coordinates and delegates work to Planner, Coder, and Designer agents. Breaks down complex requests into tasks, manages execution phases (parallel and sequential), ensures file scopes don't overlap, and verifies the integrated result.
- **Definition:** [.github/agents/orchestrator.agent.md](.github/agents/orchestrator.agent.md)

### Planner
- **Model:** Claude 3.5 Sonnet (copilot)
- **Responsibility:** Creates detailed implementation plans by researching the codebase, documentation, dependencies, and edge cases. Produces ordered implementation steps, file assignments, dependency analysis, and identifies work that can run in parallel.
- **Definition:** [.github/agents/planner.agent.md](.github/agents/planner.agent.md)

### Coder
- **Model:** GPT-4o (copilot)
- **Responsibility:** Implements code-oriented tasks, fixes bugs, and writes logic within assigned file scopes. Handles configuration files, launch setup, and ensures code is clear, testable, and follows repository patterns.
- **Definition:** [.github/agents/coder.agent.md](.github/agents/coder.agent.md)

### Designer
- **Model:** Gemini 1.5 Flash (copilot)
- **Responsibility:** Handles UI/UX, accessibility, information architecture, interaction flow, and visual design. Creates a polished dashboard with responsive layout, visual affordances, and clear typography.
- **Definition:** [.github/agents/designer.agent.md](.github/agents/designer.agent.md)

## Coordination approach

The team uses GitHub Copilot CLI in a Codespace to coordinate all work. The Orchestrator delegates tasks to specialized agents, manages file ownership to prevent conflicts, and ensures sequential execution when dependencies exist and parallel execution when safe.
