---
name: check-trajectory
description: Audit an active multi-step task for drift between its confirmed outcome, priority order, current strategy, and new evidence, then decide whether to continue, simplify, gather decisive evidence, reframe, ask, or stop. Use after repeated failures, material scope growth, contradicted assumptions, context handoffs, or before changing solution class. Do not use for ordinary planning or retrospective incident analysis.
---

# Check Trajectory

Run a lightweight in-flight decision check. Determine whether the current work is still the best route toward the desired outcome; do not turn the checkpoint into another implementation project or a full post-mortem.

## Triggers

Use this skill when one or more of these occur:

- Two attempts fail without materially new evidence.
- A local failure is about to cause a global redesign.
- The task is about to change architecture, prompt contract, persistence model, public interface, or solution class.
- Scope, implementation size, or evaluation machinery has grown materially beyond the plan.
- A compatibility layer, parallel implementation, or historical mode is being retained without a current consumer.
- New evidence contradicts a central assumption or success metric.
- A user correction changes priorities, scope, or materiality.
- Context compaction or handoff may have weakened the active task model.
- The work passes local checks but no longer clearly advances the outcome.
- An expensive or difficult-to-reverse action is next and the strategy remains uncertain.

Do not invoke it merely because a task has several steps or has taken time.

## Inputs

Use the confirmed Goal Charter when available. Otherwise reconstruct the solution-neutral outcome, priority order, constraints, and non-goals from authoritative user instructions and mark material inferences explicitly.

Inspect only the evidence needed to decide direction: the active plan, decisions, tool results, diffs, tests, logs, or artifacts already in scope. The checkpoint itself is read-only. Do not implement fixes while deciding whether the strategy survives.

## Check From the Top Down

Stop at the highest layer that materially explains the drift:

1. **Outcome:** Is the desired capability still correct and current?
2. **Problem framing:** Has the chosen mechanism become confused with the goal?
3. **Strategy:** Starting from zero with current evidence, would the same solution class be chosen?
4. **Architecture and boundaries:** Are responsibilities, invariants, provenance, and tool roles assigned correctly?
5. **Execution and controls:** Are scope, plan, tests, evaluator, stop conditions, or coordination driving the wrong behavior?
6. **Local implementation:** Is the strategy sound and the issue genuinely local?

Classify the evidence before redesigning:

```text
isolated deviation
recurring within one mechanism
recurring across mechanisms
evaluator or metric mismatch
missing decisive evidence
outside the material failure threshold
```

Do not preserve a strategy because of sunk cost, and do not replace it because of one vivid example. Name the decisive unknown when evidence cannot distinguish credible directions.

## Independent Challenge

The solo workflow must remain sufficient. Use one independent challenger only when a costly or hard-to-reverse strategy choice remains genuinely uncertain, repeated local fixes have failed, or anchoring risk is material.

Read [references/independent-challenge.md](references/independent-challenge.md) before delegating. Do not use a panel by default.

## Disposition

Choose one:

- `continue` — strategy and scope remain evidence-supported.
- `simplify` — preserve the useful core and remove unnecessary scope.
- `gather_decisive_evidence` — run the smallest bounded check that distinguishes credible directions.
- `reframe` — revise the problem or strategy before more implementation.
- `ask_for_direction` — outcome, priority, authority, or scope cannot be inferred safely.
- `stop_this_line_of_work` — evidence no longer justifies continuing the current direction.

Continue, simplify, or gather read-only evidence autonomously when that remains within the authorized outcome and scope. Pause for the user before changing the outcome, materially expanding scope, requiring new authority, or abandoning an explicitly chosen direction.

## Output

Keep an ordinary checkpoint short:

```markdown
- **Outcome:**
- **Priority order:**
- **Material evidence learned:**
- **Invalidated assumptions:**
- **Drift:** none | outcome | framing | strategy | architecture | execution | local
- **Decisive unknown:**
- **Disposition:**
- **Next bounded action:**
- **Reconsider when:**
```

Omit empty fields. If the disposition is `continue`, do not burden the user with a report; state the conclusion briefly and resume. If a material incident has already occurred and the user wants retrospective causal analysis, use the repository's post-mortem workflow instead.
