---
name: agent-post-mortem
description: Analyze why an agent task went off course, test whether it was solving the right problem in the right way, and define a better path forward.
---

# Agent Post-Mortem

Analyze decisions and systems, not personalities. Do not assume the current problem framing, implementation, or accumulated work should survive the analysis. State each fact once, omit non-causal layers, and keep a typical report within 800–1,200 words. The workflow must remain sound with one agent; use independent agents only as an optional challenge, never as a prerequisite.

## Output

Present the post-mortem using [assets/post-mortem-template.md](assets/post-mortem-template.md) after the user confirms both the incident framing and the proposed diagnosis. Do not modify the failed task unless separately authorized.

## Framework

### 1. Gather evidence and recover the real goal

Inspect the requests, instructions, transcript, tool results, diffs, commits, logs, tests, acceptance evidence, memory, handoffs, and current state.

Restate the desired outcome without naming or assuming the chosen solution. Choose the smallest incident scope broad enough to include the decision to select the solution class, the earliest evidence-backed divergence, and the resulting impact. Define the scope by the outcome and decision horizon, not by the name or boundary of the implementation under review. Preserve valid work and unaffected areas explicitly.

### 2. Check the framing with the user

Before root-cause analysis, send only the factual incident framing:

- **Goal:** “I understand the desired outcome as …”
- **Success:** “The task would have succeeded if …”
- **Scope:** “I plan to analyze … because …”
- **Observed failure:** “The evidence shows … happened.”

Ask: **“Is this the right outcome, scope, and observed failure to analyze? Please confirm or correct anything above.”** Wait for the answer. Do not include a suspected cause or ask the user to approve one at this stage. Ask one additional concrete question only when a missing fact would materially change the framing. If corrected, restate and confirm again.

### 3. Reconstruct what happened

Build a compact timeline from the last known-good state through the earliest meaningful divergence, ignored stop signals, later amplifiers, failure, and containment.

At the earliest divergence, classify decision-relevant context as:

- **Present and used:** available and reflected in the decision.
- **Present but missed or contradicted:** available but ignored or inconsistent with the decision.
- **Assumed:** acted upon without adequate evidence.
- **Unknown:** unavailable or unresolved.

Use only information available at that point. Label missing, hidden, compacted, or later-learned evidence.

### 4. Diagnose from the top down

Test these layers in order and stop at the highest layer that materially explains the incident. Do not let abundant implementation evidence substitute for testing a higher layer:

1. **Outcome:** Was the desired capability or success condition wrong, obsolete, or unclear?
2. **Problem framing:** Did the chosen solution become confused with the problem itself?
3. **Strategy:** If starting today without sunk cost, would the same build/adopt/buy/integrate decision be made? Which parts are commodity and which are genuinely domain-specific?
4. **Architecture and boundaries:** Were responsibilities, invariants, data flow, provenance, or component boundaries missing or wrong?
5. **Execution and controls:** Did requirements, tests, evaluators, stop conditions, reporting, permissions, or agent coordination fail?
6. **Local implementation:** Was the strategy sound but a specific design or code decision wrong?

Before settling on architecture, controls, or implementation:

- restate the required capability independently of the current solution;
- identify credible alternative solution classes using enough relevant local or external evidence to expose the real choice and decisive constraints; repository silence is not evidence that alternatives do not exist, but do not conduct an exhaustive landscape survey unless requested;
- separate commodity capability from genuinely domain-specific behavior; and
- retain the current strategy only when evidence-backed requirements and tradeoffs justify it. Plausibility, existing investment, or working components are not sufficient.

If the evidence cannot distinguish build, adopt, integrate, simplify, reframe, or stop, mark the strategy unresolved and gather only the decisive missing evidence or ask one concrete question. Do not silently descend to architecture. Do not delegate by default. If material uncertainty remains in a broad or costly incident, one available independent agent may challenge the framing and strategy. Give it the solution-neutral outcome, constraints, and raw evidence, but withhold the preliminary causal hypothesis; never wait on delegation when the single-agent evidence is sufficient.

For every causal layer, cite evidence, explain why the choice looked reasonable then, and identify the counterfactual decision or guardrail. Explicitly show why each higher layer was rejected before naming a lower layer as primary. Do not force a systemic explanation when a local one is sufficient, or a local explanation when the framing or strategy was wrong.

### 5. Confirm the diagnosis and direction

Select a provisional evidence-supported disposition:

- **Continue:** the framing and strategy are sound; repair execution.
- **Simplify:** retain the useful core and remove unnecessary custom scope.
- **Adopt or replace:** use established tooling, open-source software, managed services, standards, or known algorithms for commodity capability.
- **Reframe or redesign:** change the problem definition or solution strategy before more implementation.
- **Stop or defer:** the outcome no longer justifies the cost or risk.

Do not prefer custom building or replacement automatically. Compare fit, maturity, integration cost, operations, performance, privacy, licensing, and maintainability only as relevant. Keep custom logic focused on domain-specific behavior that standard solutions do not provide.

Before writing, send a compact diagnosis check:

- **Primary failure:** the proposed highest causal layer and one-sentence evidence basis;
- **Strategy verdict:** whether the current solution class survives the zero-based check, and any material uncertainty; and
- **Direction:** the proposed disposition.

Ask: **“Does this match what went wrong and the direction to take? Please confirm or correct it.”** Wait for the answer. If corrected, revise the diagnosis and check it again. User confirmation validates the interpretation of the evidence; it does not replace missing evidence.

### 6. Write the path forward

Map prevention items to failed guardrails and observable verification. Put hard constraints in the harness where possible. Keep **Next Steps** high level and make the **Continuation Prompt** pursue the original outcome under the chosen disposition, not merely continue the existing implementation.

## Quality Gate

Before presenting, verify that the report:

- uses a solution-neutral statement of the desired outcome;
- records factual incident confirmation separately from diagnosis confirmation;
- does not anchor the initial confirmation with a suspected cause;
- tests problem framing and credible alternatives with evidence before architecture and implementation;
- does not preserve the current strategy merely because it is plausible or partially working;
- either rules out each higher causal layer with evidence or leaves the diagnosis unresolved;
- identifies the highest causal layer supported by evidence;
- distinguishes preserved work from sunk-cost attachment;
- chooses an explicit path forward and defines the commodity/domain-specific boundary when relevant;
- maps fixes to evidence and verification rather than generic advice;
- retains the required template headings, stays concise, and exposes no secrets.
