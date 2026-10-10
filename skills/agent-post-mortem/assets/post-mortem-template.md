# Agent Post-Mortem: <!-- concise incident title -->

- **Incident date:** <!-- date or range -->
- **Confirmed scope:** <!-- bounded task, phase, or workstream -->
- **Failure point:** <!-- earliest meaningful divergence -->
- **Confidence:** <!-- confidence and material uncertainty -->

## Incident Identification & Classification

### Executive Summary

<!-- Intended outcome, highest causal layer, impact, and chosen path forward in one short paragraph. -->

### Failure Class

- **Primary failure class:** <!-- outcome, problem framing, strategy, architecture, execution/control, or implementation -->
- **Late trigger or amplifier:** <!-- omit when unnecessary -->

### Blast Radius

- **Impact and external effects:** <!-- affected scope and verified/unknown effects -->
- **Preserved and unaffected:** <!-- reusable work and incident boundary -->
- **Current state:** <!-- failed, contained, reverted, partially recovered, or recovered -->

## Context & Belief State Analysis

### Confirmed Goal and Scope

- **Desired outcome:** <!-- solution-neutral capability the user needed -->
- **Success condition:** <!-- what would have counted as complete -->
- **Observed failure:** <!-- verified symptom or unmet outcome, without causal interpretation -->
- **Incident confirmation:** <!-- outcome, scope, and observed failure the user confirmed or corrected -->
- **Diagnosis confirmation:** <!-- proposed primary failure and direction the user confirmed or corrected after analysis -->

### Context at the Earliest Meaningful Divergence

<!-- State the evidence cutoff and label partial reconstruction. -->

- **Present and used:** <!-- facts reflected in the decision -->
- **Present but missed or contradicted:** <!-- available facts inconsistent with it -->
- **Assumed:** <!-- propositions used without adequate evidence -->
- **Unknown:** <!-- unresolved material facts -->

### Timeline

| Point | State transition or evidence | Why it mattered |
|---|---|---|
| <!-- last known-good state --> |  |  |
| <!-- earliest meaningful divergence --> |  |  |
| <!-- ignored stop signal or amplifier --> |  |  |
| <!-- observable failure or containment --> |  |  |

## Root Cause Diagnostics

### Higher-Layer and Strategy Check

| Layer tested | Verdict | Evidence |
|---|---|---|
| <!-- outcome, framing, and strategy before any lower primary cause --> | <!-- survives, fails, or unresolved --> | <!-- requirements, credible alternatives, and why the current solution class does or does not survive --> |

<!-- When strategy is material, distinguish commodity capability from genuinely domain-specific behavior. Do not treat plausibility, sunk cost, or repository silence as evidence. -->

### Decision Point Identification

- **Highest causal layer:** <!-- outcome, framing, strategy, architecture, controls, or implementation -->
- **Decision fork:** <!-- chosen path and viable alternative -->
- **Why it looked reasonable:** <!-- contemporary reasoning without hindsight -->
- **Counterfactual:** <!-- decision, question, or guardrail that would have changed the path -->
- **Late trigger or amplifier:** <!-- distinguish from root cause; omit when unnecessary -->

### Contributing Factors

| Layer | Finding | Evidence |
|---|---|---|
| <!-- include only causal layers from the diagnostic ladder --> |  |  |

## Action Items & Prevention

### Systemic Fixes

| Failed guardrail | Change | Verification |
|---|---|---|
| <!-- requirements, strategy review, architecture, harness, stop rule, coordination, etc. --> |  |  |

### Next Steps

- **Chosen direction:** <!-- continue, simplify, adopt/replace, reframe/redesign, or stop/defer -->
- **Reuse boundary:** <!-- commodity capability to reuse and domain-specific custom scope; omit when irrelevant -->

1. <!-- first goal-aligned action -->
2. <!-- implementation, replacement, or redesign action -->
3. <!-- authoritative completion check -->

#### Continuation Prompt

```text
OUTCOME
<solution-neutral capability to deliver>

PROBLEM FRAME
<the confirmed problem, without assuming the old implementation>

APPROACH
<continue, simplify, adopt/replace, reframe/redesign, or stop/defer—and why>

REUSE / CUSTOM BOUNDARY
<standard capability to adopt and genuinely domain-specific logic to retain>

CURRENT STATE
<preserved work, invalid assumptions, hazards, and stable checkpoint>

SUCCESS
<externally checkable completion predicate>

DOES NOT COUNT
<relevant near misses, including merely continuing the failed approach>

VERIFICATION AND STOP CONDITIONS
<authoritative checks and conditions requiring reassessment>
```
