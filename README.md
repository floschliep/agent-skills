# Agent Skills

A collection of agent skills I find useful.

## Overview

### Define Outcome

Use [define-outcome](skills/define-outcome/SKILL.md) to work out what you want to achieve, how you'll judge success, and what's outside the scope before choosing a solution.

> "I want to automate customer support."

### Shape Change

Use [shape-change](skills/shape-change/SKILL.md) for non-technical planning: clarify how a proposed change should work, including the user experience, expected behavior, and edge cases, before deciding how to implement it.

> "We're adding saved searches. What happens when someone edits or deletes one?"

### Fix Bug

Use [fix-bug](skills/fix-bug/SKILL.md) to choose a fix that addresses the cause, accounts for side effects, and verifies the original failing scenario.

> "When changing selection users briefly see the wrong detail screen."

This skill references the `diagnosing-bugs` skill from [mattpocock/skills](https://github.com/mattpocock/skills), which can be helpful for complex diagnosis.

### Check Trajectory

Use [check-trajectory](skills/check-trajectory/SKILL.md) to pause an active task and check whether its goals, approach, and scope still make sense given what you've learned. It's useful in long-running tasks, whether one agent is working alone or coordinating multiple agents.

> "We've tried three fixes and keep expanding the scope. Reassess the approach."

### Agent Post-Mortem

Use [agent-post-mortem](skills/agent-post-mortem/SKILL.md) to examine why an agent task went wrong, including whether it pursued the right problem and approach, and decide what to do next.

> "The agent built a complicated solution that missed the goal. What went wrong?"

### Review Agent Guidance

Use [review-agent-guidance](skills/review-agent-guidance/SKILL.md) to review a completed task for lessons worth keeping in agent guidance, tooling, tests, or documentation.

> "We repeatedly corrected the same mistake. Should we update AGENTS.md or add a check?"

## Other Skill Collections

Other collections of skills I like to use:

- [muratcankoylan/Agent-Skills-for-Context-Engineering](https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering)
- [mattpocock/skills](https://github.com/mattpocock/skills)
