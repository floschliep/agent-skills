---
name: define-outcome
description: Interactively establish a confirmed, solution-neutral Goal Charter before planning. Use in a dedicated goal-framing conversation when the desired outcome, priority order, materiality threshold, constraints, or non-goals need to become the source of truth. Do not use for ordinary implementation planning or execution.
---

# Define Outcome

Establish what the user actually wants before selecting how to build it. The result is a concise Goal Charter that a normal planner can consume; it is not an implementation plan.

When the Goal Charter is stable but a user-facing, cross-boundary, API, or persistent-data change still has ambiguous navigation, states, identity, inclusion, compatibility, or data risk, use `$shape-change` before technical planning.

## Principles

- Treat proposed implementations as hypotheses, not goals.
- Recover the desired capability as if the current solution did not exist.
- Ask one question at a time. Use everything already answered and skip questions whose answers cannot change the charter.
- Distinguish hard constraints, optimization priorities, preferences, and accepted imperfections.
- Order priorities rather than combining them into a vague statement such as “fast and correct.”
- Challenge only tensions that materially affect the outcome or its verification.
- Do not spawn subagents, inspect implementation details, or draft architecture during this workflow.
- Do not save a file unless the user asks. Return the confirmed charter in the conversation by default.

## Dialogue

Adapt the conversation instead of following a fixed questionnaire. Establish, when material:

1. **Desired change:** What should become possible or materially better?
2. **Motivation:** What present problem makes the work valuable?
3. **Solution-neutral outcome:** Would the desired result remain the same without the current implementation or proposed mechanism?
4. **Priority order:** What wins when quality, speed, cost, scope, simplicity, and completeness conflict?
5. **Hard constraints and preferences:** Which conditions are non-negotiable, and which are merely desirable?
6. **Materiality:** Which imperfections are acceptable, and what would be a real failure?
7. **Non-goals:** Which adjacent outcomes must remain outside scope?
8. **Success evidence:** What observation would justify declaring success?
9. **Reconsideration triggers:** What evidence should make the team stop, simplify, or rethink the direction?

When the user states a solution as a requirement, recover the underlying outcome. For example:

```text
“Use a second provider call” is a mechanism. Is the underlying requirement
that unresolved decisions receive a stronger semantic attempt before the
system accepts a broader result?
```

When priorities conflict, ask for the governing relationship. For example:

```text
Should semantic correctness be a hard floor, with speed optimized above that
floor, or may correctness trade against latency within an accepted range?
```

## Confirmation

Use two confirmation points. Do not combine them with new recommendations.

First confirm factual understanding:

```markdown
- **Goal:**
- **Success:**
- **Scope:**
- **Current gap:**
```

After resolving material tensions, confirm the decision contract:

```markdown
- **Priority order:**
- **Hard constraints:**
- **Accepted imperfections:**
- **Non-goals:**
- **Evidence required:**
- **Reconsideration triggers:**
```

Revise and reconfirm when corrected. User confirmation establishes the charter; it does not supply missing evidence.

## Final Goal Charter

After both confirmations, return only the useful sections:

```markdown
# Goal Charter

## Outcome

## Why This Matters

## Success

## Priority Order

1.
2.
3.

## Hard Constraints

## Preferences

## Accepted Imperfections

## Non-Goals

## Evidence Required

## Reconsideration Triggers

## Open Assumptions
```

Omit empty sections. Keep the charter compact enough to survive handoffs and context compaction. Stop before implementation planning unless the user separately asks to continue.
