---
name: review-agent-guidance
description: Review a completed task or chat for durable improvements to applicable AGENTS.md guidance and adjacent enforcement within an explicitly supplied repository, directory, or file scope. Use only when explicitly invoked at the end of a task or conversation to capture learnings, reduce duplicated or contradictory instructions, or decide whether guidance should change; a no-op is valid.
---

# Review Agent Guidance

## Establish scope and gather evidence

1. Require the invoker to supply an exact repository, directory, or file scope. Do not infer or expand it; request the missing scope before continuing.
2. Inspect version-control status and diffs only within that scope, when available, and preserve unrelated work.
3. Read the raw completed-task evidence: the request, user corrections, failures, retries, repeated command friction, validation output, and current diff/status. Prefer primary artifacts over prior conclusions or summaries. When available, record elapsed time, agent and handoff count, failed tool calls, repeated expensive verification, user course corrections, and non-generated diff size; do not manufacture missing measurements.
4. Read every `AGENTS.md` applicable to the supplied scope in full, plus relevant local skills and the owning help or configuration for tooling implicated by the task.

## Classify candidates

Assign each candidate one primary destination:

- **AGENTS guidance:** durable judgment, boundary, or constraint agents must apply.
- **Tooling/automation:** deterministic commands, configuration, orchestration, or repeatable mechanics.
- **Tests/static enforcement:** behavior a machine can reliably reject.
- **Docs/memory/report:** historical context, measurements, setup detail, or explanatory material.
- **No action:** isolated, obvious, already covered, speculative, or too weak to justify maintenance.

Keep an AGENTS candidate only when it is durable, specific to the supplied scope, actionable, non-obvious, likely to recur, and not better enforced mechanically. Keep command choice and rationale in guidance; keep exact syntax, version or toolchain pins, supported targets, runner arguments, and deterministic mechanics in the owning tool, help, or configuration. Never record secrets or transient identifiers, infrastructure state, or isolated measurements in guidance; place genuinely useful historical or setup facts in documentation or reports, otherwise take no action.

## Require independent review before AGENTS changes

1. Spawn a fresh read-only subagent restricted to the exact scope supplied by the invoker.
2. Give it that scope, the raw evidence, and current applicable files, not the primary agent's candidates or conclusions.
3. Ask it to identify durable lessons, semantic duplication, contradictions, better enforcement destinations, and a valid no-op outcome.
4. Reconcile its findings against the evidence; reject unsupported suggestions rather than applying them blindly.

If a fresh independent review is unavailable, do not change AGENTS guidance; report that the required review could not be completed. A report-only retrospective may still classify candidates and recommend next steps without delegation. Separately authorized tooling, tests, documentation, or skill changes may proceed when their own applicable workflow permits it.

## Make the smallest authorized improvement

1. Review semantic duplication and contradictions across every applicable `AGENTS.md`, not only the target section.
2. Prefer delete, merge, replace, or move over append. Treat net line growth as a maintenance cost, not a success metric.
3. Preserve contextual repetition only when local placement materially improves compliance.
4. Prefer changing an existing guidance, skill, tool, or check over creating a competing workflow.
5. Limit each accepted recommendation to one primary enforcement surface. Split unrelated improvements instead of coupling them into one process rewrite.
6. Follow the user's requested mode: propose changes when asked for recommendations; edit only when authorized. Implement small tooling, test, static-check, documentation, or report improvements only when clearly authorized and within the supplied scope; otherwise recommend them separately.
7. Preserve unrelated dirty changes. Do not commit, push, modify external systems, or perform database operations unless separately requested.
8. Make no change when no candidate survives the filter.

## Validate and report

For changed guidance, run `git diff --check` when Git is available, search for stale or duplicated wording, and reread the applicable files for contradictions. Report:

- the supplied scope;
- every candidate's classification and disposition;
- the independent review and critical reconciliation;
- changed files and AGENTS line counts before and after;
- validation performed and anything unverified;
- a clear no-op when applicable;
- separately recommended improvements that were outside scope.
