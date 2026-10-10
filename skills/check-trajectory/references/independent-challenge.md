# Independent Challenge

Use context isolation to reduce anchoring on the active agent's explanation. The challenger advises; it never owns the task or decision.

## When to Use It

Use one challenger when:

- the next decision changes solution class or creates substantial irreversible work;
- repeated local fixes have not improved the actual outcome;
- current evidence supports multiple credible framings;
- the active agent has accumulated strong sunk-cost or recommendation anchoring; or
- an evidence claim needs independent verification before the strategy changes.

Do not delegate routine progress review, ordinary implementation debugging, or decisions already resolved by direct evidence.

## Select the Challenge

Choose the smallest relevant mode:

1. **Zero-based strategy challenge:** Would the same solution class be chosen if starting now?
2. **Evidence challenge:** Do raw artifacts support the claimed conclusion and materiality?
3. **Simplification challenge:** Which components exist because of sunk cost rather than current requirements?

Use one challenger by default. Add another only when the modes are genuinely independent and the decision warrants the cost.

## Neutral Brief

Give the challenger:

- the solution-neutral outcome;
- ordered priorities;
- hard constraints and non-goals;
- raw evidence and authoritative artifacts;
- current observable behavior; and
- the exact decision that must be made.

Withhold:

- the active agent's suspected cause;
- its preferred solution or recommendation list;
- arguments based on prior investment;
- summaries that replace available raw evidence; and
- instructions to validate a predetermined conclusion.

Example:

```text
Assess this task from zero using the supplied outcome, constraints, and raw
evidence. Identify the highest-level point at which the current approach may
be wrong, the strongest credible alternative, and the evidence that should
decide between them. Do not propose implementation details unless the current
strategy survives.
```

For an evidence challenge, ask for fact, inference, and unknown to be separated explicitly.

## Integrate the Result

Compare the challenge with the raw evidence; do not accept it by deference or majority vote. Record:

```text
challenge supported
challenge rejected by evidence
decisive evidence still missing
```

If the challenge exposes a higher-level uncertainty, return to the trajectory check at that layer. If it only finds a local defect and the strategy survives, continue without broadening the task.
