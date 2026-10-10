---
name: shape-change
description: Turn an implementation request into a confirmed experience and data contract before technical planning. Use for user-facing, cross-boundary, API, or persistent-data changes when navigation, record semantics, states, compatibility, or operational constraints may be ambiguous. Skip narrow fixes and refactors whose observable behavior is already explicit.
---

# Shape Change

Establish what users and connected systems must observe before choosing architecture. Produce a compact contract that planners, implementers, and reviewers can use as the source of truth. This is requirements shaping, not implementation planning.

## Start From Evidence

Inspect the affected repository and supplied consumer context before asking questions. Find the current entry point, named components, neighboring flows, existing API and persistence semantics, authentication model, and evidence about whether clients or data are live. Treat an existing product flow as the default integration point unless the user requests a replacement.

When necessary evidence belongs to another repository, identify the missing consumer or producer fact explicitly. Do not invent it or turn the uncertainty into a speculative compatibility layer.

If the desired outcome, priority order, constraints, or non-goals are themselves unclear, use `$define-outcome` first. Return here once the goal is stable.

## Trace The Experience

For each affected user path, establish:

1. How the user enters.
2. What appears immediately.
3. What appears after loading or processing.
4. Which actions are available.
5. The exact destination or effect of each action.
6. Which existing experience should be reused.
7. Empty, stale, unavailable, deleted, and authorization-loss behavior when material.
8. How the user leaves, retries, or recovers.

An action without a destination is unresolved. Terms such as “result view,” “history,” “latest,” “same,” “all,” and “available” must be tied to an existing product concept or defined observable behavior.

## Resolve Data Semantics

Check the dimensions that can materially change behavior or storage:

- **Identity:** what makes two records the same.
- **Inclusion:** which states appear or remain hidden.
- **Ordering and grouping:** how representative records are selected.
- **Mutation:** whether historical or derived data remains actionable.
- **Ownership:** user, account, device, installation, or another boundary.
- **Retention:** complete history or only retained records.
- **Freshness:** live, cached, or stale-while-revalidate behavior.
- **Compatibility:** existing clients and persisted data that must keep working.
- **Data risk:** whether proposed operations are additive, reproducible, destructive, or irreversible, and whether the environment is live.

Do not choose endpoints, tables, abstractions, rollout machinery, or migration strategy until these semantics are coherent.

## Ask Only Decision-Changing Questions

Ask when plausible answers would change observable behavior, the data model, a public contract, authorization, destructive work, or released-client compatibility. First use repository evidence and prior answers; do not ask the user to repeat known facts.

Batch at most three related questions. Include a concrete recommended default and its consequence. For lower-impact gaps, record a reasonable assumption and continue unless the user objects.

Do not interrogate the user about implementation preferences the repository can answer. Do not continue when navigation, identity, mutation capability, or material risk remains genuinely ambiguous.

## Experience Contract

Return only relevant sections and keep the result small enough to survive handoffs:

```markdown
# Experience Contract

## User Paths
- Entry → immediate state → action → exact destination or effect

## States And Recovery
- Loading:
- Empty:
- Stale/offline:
- Failure/retry:

## Data Semantics
- Identity:
- Inclusion:
- Ordering/grouping:
- Mutation:
- Ownership and retention:
- Freshness:

## Delivery Constraints
- Environment and data risk:
- Compatibility:
- Hard constraints:
- Explicit non-goals:

## Confirmed Assumptions

## Open Decisions

## Acceptance Scenarios
- Given … when … then …
```

Use three to eight acceptance scenarios covering the primary path and material boundary states. Describe observable outcomes, not implementation structure.

Ask the user to confirm only when open decisions remain or when the contract introduces a material inferred default. Once confirmed, hand the contract to ordinary technical planning; do not expand it into architecture inside this skill.
