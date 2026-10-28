---
name: staged-implementation
description: Orchestrate substantial implementation work with separate implementation and review agents, risk-based verification, and a commit after each completed stage before continuing. Use for multi-stage features, redesigns, or refactors, or when the user requests this agent workflow. Skip narrow edits that do not benefit from staged delivery.
---

# Staged Implementation

Deliver the whole experience in progressively more complete passes. The coordinating agent owns scope and acceptance; implementation agents own edits; independent reviewers evaluate completed work. After accepting each completed stage, the coordinator commits its changeset and proceeds to the next stage without waiting for user confirmation.

## Shape the stages

Inspect the existing integration points and applicable repository guidance. Before technical stage planning, the coordinator must read and use `$shape-change` when user paths, navigation destinations, states/recovery, record semantics, API behavior, compatibility, or operational constraints are materially ambiguous. Pass its resolved experience/data contract and acceptance scenarios to implementers and reviewers. Reuse an already accepted contract rather than reshaping settled decisions; skip shaping for narrow work whose observable behavior is explicit. Reapply `$shape-change` if new evidence opens a material product or contract decision during implementation.

Choose the smallest useful set of stages. For a substantial UI redesign, start with:

1. **Structure and behavior:** composition, ownership, state transitions, navigation, cancellation, recovery, and integration boundaries across the whole flow.
2. **Content and composition:** correct content, geometry, imagery, typography, scrolling, and adaptive behavior within that structure.
3. **Motion and final integration:** transitions between accepted states, continuity, interruption, and reduced-motion behavior.

Adapt or combine these for other work. Avoid dividing stages merely by screen or file. Each stage must produce a coherent, inspectable result. Establish correctness-critical ordering and lifecycle behavior in the structural stage even when its visual treatment comes later.

Before starting, state each stage's scope, observable exit criteria, verification evidence, and deliberately deferred work. Include acceptance criteria for each affected state and important transition. Later stages inherit earlier accepted invariants. A short plan is sufficient; use a repository planning artifact only when needed for continuity.

## Assign ownership

- **Coordinator:** maintains the contract and stage gates, assigns bounded work, resolves integration decisions, checks evidence, detects drift, commits completed stages, and reports progress. Do not become a competing implementation agent when a subtask gets difficult.
- **Implementation:** use one lead implementation agent by default. Add specialists only for cohesive, separable work with explicit interfaces and file ownership. Shared files and integration decisions have one owner. A dedicated planning agent is optional, not a required role.
- **Review:** use a separate read-only reviewer after implementation and verification finish. Require the reviewer to read and use `$ponytail:ponytail-review` at every stage review gate, including correctness, safety, regression coverage, and unnecessary complexity. Name the skill explicitly in the delegation prompt. One reviewer is normally enough; split reviews only when distinct risk areas justify it, such as flow correctness and visual composition. This is one review gate, not a separate complexity-only review.

Delegate with the accepted outcome, current stage, relevant constraints, owned files/interfaces, required checks, and return conditions. Give reviewers the contract, completed diff, connected code, and evidence; let them form their own conclusions. Do not direct a reviewer to rubber-stamp an implementation report.

Parallelize independent implementation work only. Serialize work that shares mutable resources such as a simulator, device, test fixtures, or snapshot references; name one runner owner. Review must not overlap implementation edits to its scope.

If delegation is prohibited or unavailable, disclose that the required agent separation cannot be performed. If a required skill cannot be found, report which shaping or review gate is blocked instead of silently substituting a generic pass. Do not label self-review independent or claim this workflow was completed. Respect the user's permitted execution mode.

## Complete each stage

1. **Implement and check locally.** Implementation agents add focused tests alongside behavior changes and use fast owner-level checks while iterating. For bugs, establish causal reproduction before repair; use available diagnosis/fix skills when useful.
2. **Exercise the intended outcome.** Validate real user paths and integrations before the broad checkpoint. For UI work, inspect the actual composed screen against its design authority. Include loading, failure/retry, dismissal, and interruption where affected. Verify retained view identity or resource ownership when the defect depends on it; a test that reconstructs the view may miss the real failure.
3. **Run the relevant regression checkpoint.** Use the repository's supported runner and scopes. Unit tests cover functionality and lifecycle decisions; snapshots cover deterministic rendering and selected real-container compositions; UI tests cover important user paths. Build coverage where these boundaries add evidence rather than requiring all three for every edit. Real hardware is needed only for affected capabilities the simulator cannot establish.
4. **Review the completed stage.** Pause implementation edits and hand the coherent diff to the independent reviewer. Review correctness, explicit requirements, regressions, and complexity. A code review does not replace visual or product-path verification.
5. **Resolve findings.** Return warranted findings to implementation. Re-exercise the affected path and rerun relevant checks. Repeat broad suites only when the change or remaining risk warrants it; re-review changed findings rather than restarting the whole review ritual.
6. **Accept as coordinator.** Inspect actual results and artifacts, including skips and limitations. An agent's summary, passing suite, or review verdict is evidence, not automatic acceptance. Ensure the evidence corresponds to the final implementation. Do not rerun checks merely to duplicate another agent's valid evidence.
7. **Commit and continue.** Commit only the completed stage's changeset, excluding unrelated work, with a message describing its content and effect. Report the commit, what is ready, the evidence, and any deferred or unverified behavior; then proceed to the next stage without waiting for user confirmation. Commit the final stage as well. If the commit fails, resolve the failure before proceeding. Explicit user or repository instructions that prohibit commits take precedence: leave the changes uncommitted, report the override, and continue with the remaining stages.

Static snapshots cannot establish transition quality. Inspect recordings or actual motion when continuity, easing, intermediate states, or dismissal order matters. Preserve design-system semantics while changing composition. Honor existing snapshot-recording authorization; inspect updated references and verify without recording, never record merely to hide unexplained drift.

## Keep the work on course

After two failed local corrections, or when symptom patches spread across owners, the coordinator reassesses the mechanism before authorizing more patches. Return to the earliest wrong ownership or state decision. Do not let implementation effort redefine the accepted outcome.

For a separately reproducible shared defect discovered during feature work, isolate its repair and regression coverage under a separate implementation owner, then independently review and commit it separately before resuming, subject to explicit user or repository instructions that prohibit commits. Preserve the shared component's public semantics and styling. Abandon disproven repairs.

Bound verification to unresolved acceptance criteria. If a tool cannot perform a required check, report that precise gap and use an equivalent source of evidence when available; do not keep troubleshooting unrelated gestures or broaden the task indefinitely. Scope changes requiring a product decision go back to the user; routine implementation choices stay with the agents.

## Progress format

Keep the stage update concise:

- **Ready:** stage and observable behavior delivered.
- **Evidence:** checks and inspected artifacts tied to acceptance criteria, with actual pass/fail/skip status.
- **Inspect:** the fixture, build, or user path the developer should try.
- **Limits:** deliberately deferred work and anything not verified.
- **Commit:** commit hash, or the explicit instruction that prevented committing.
- **Next:** next stage being started, or all stages complete.

Invoking this skill authorizes its agent workflow and local stage commits unless explicit user or repository instructions prohibit them. Push, deployment, external messaging, and environment changes retain their existing authorization boundaries.
