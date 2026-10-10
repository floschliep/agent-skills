---
name: fix-bug
description: Choose and validate complete bug fixes after a failure is reproducible. Use when implementing or evaluating a repair requires deciding expected behavior, investigation depth, fix scope, side effects, compatibility, and real-path verification. Use diagnosing-bugs for reproduction and root-cause discovery alone.
---

# Fix Bug

Fix the behavior, not merely the visible failure. A locally valid value, handled exception, or green unit test does not prove the system reached the right state or output.

## Relationship to diagnosis

Start from a tight reproduction and a known causal path. If either is missing, use `$diagnosing-bugs` first. Return here once the failure is reproducible and the suspected transitions can be tested.

Do not discard a valid local fix just because a deeper bug exists. An upstream state bug and an independent downstream robustness bug may both need repairs.

## Define “fixed” before choosing code

State the observable behavior as a matrix or equivalent set of cases:

```text
trigger or input
→ expected state or output
→ permitted next behavior
→ caller or user effect
→ side effects
```

For layered or distributed behavior, cover the combinations that matter—not only type validity, field schemas, or transport statuses. Include negative effects when important, such as “no job scheduled,” “no record created,” “no message emitted,” or “no retry offered.”

If the desired behavior, identity semantics, side effects, or compatibility policy is unclear and would change the repair, use `$shape-change` or ask the smallest decision-changing question before implementation.

## Decide how far the investigation must go

At the failing line, ask: **what state should have reached this line?**

Continue upstream when any of these are true:

- the candidate fix changes error handling or presentation but leaves a surprising input or upstream state intact;
- type- or schema-valid data may still violate the intended behavior;
- a downstream module appears guilty only because an earlier gate admitted invalid work;
- a convenient fallback may violate ownership, provenance, privacy, persistence, or other side-effect policy;
- current supported behavior may differ from dormant code, old tests, documentation, or remembered simplifications;
- a migration may have carried an old invariant onto a broader state.

Use history when it can distinguish an accidental interaction from intentional policy. Inspect the introducing change, its tests, and the older invariant it reused. Do not keep excavating history once it no longer changes the fix.

Stop when all are true:

- the intended current behavior is confirmed;
- the earliest incorrect transition is identified;
- downstream transitions are either correct or independently faulty;
- relevant side effects, ownership, and provenance are understood;
- required behavior across affected callers and modules is explicit;
- further investigation would not change implementation or validation.

## Choose the repair

Prefer the seam that owns the violated invariant.

- Correct the earliest invalid state transition rather than patching every downstream symptom.
- Preserve defensive caller handling when another module can validly produce that state now or later.
- Do not change a downstream completion or error-handling module merely because bad upstream admission caused it to run.
- Do not restore deprecated inputs, broaden side effects, or mutate shared state just to make the example pass.
- Avoid contract expansion when existing states already express the intended behavior.
- For semantic changes across an interface, verify existing callers even when types or schemas are unchanged.

Treat multiple fixes as independent when each protects a valid invariant. Explain what breaks if either one is omitted.

Record explicit non-goals for plausible adjacent changes. This keeps a causal investigation from becoming an unauthorized redesign.

## Test the solution

Validate at three levels, in this order when practical:

1. **Owning seams:** add focused regressions for each independently faulty invariant.
2. **Original execution path:** replay the original input through the real module chain or connected-system path and inspect the actual state, output, behavior, and side effects.
3. **Regression scope:** run the repository-appropriate suite once after the intended outcome is correct.

For the original replay:

- use the same load-bearing data, not a friendlier substitute;
- make the trigger deterministic and agent-runnable;
- assert the expected state and the absence of forbidden work or mutations;
- ensure the running process actually loaded the changed build;
- rerun after warranted review fixes that affect the path.

Mocks may protect a seam, but they do not replace the real execution-path replay. Success in one module does not prove its inputs were correct or that its callers observe the intended behavior.

## Fix decision summary

Keep the final rationale compact:

```text
Observed symptom:
Expected behavior:
Earliest incorrect transition:
Owning fix:
Independent defensive fix:
Side effects/ownership/provenance:
Non-goals:
Original execution-path evidence:
Residual risk:
```

Do not claim deployment or production verification when only a local or development integration was exercised.
