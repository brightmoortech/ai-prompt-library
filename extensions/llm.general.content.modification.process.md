# Content Modification Process

## Version

Version: 1.1

Changes: Added an explicit design-consistency check covering purpose, authority, necessity, existing agreements, and simplicity. No changes to approval authority or other process responsibilities.
## Objective and Scope

Modify existing material while preserving required behaviour, meaning, constraints, and unrelated work. Apply to code, configuration, documents, prompts, and workflows, including material the agent has previously seen: establish the current baseline rather than relying on memory.

The parent prompt defines the authorized task and approval gates. Apply domain-specific instructions, including documentation rules when relevant, without treating this process as authority to expand scope.

Before using the referenced clarification process, read `llm.general.clarification.process.md` supplied by the parent prompt. If it is inaccessible, request it and pause only work that depends on it; do not invent its instructions.

## Process

1. **Establish the starting point.** Read the current relevant material, applicable instructions, and affected dependencies. Identify the authoritative version and any local or concurrent changes. For software, trace affected behaviour, prerequisites, execution order, interactions, checkpoints, outputs, and failure paths. For documents and prompts, trace purpose, audience, obligations, references, and dependencies. Do not infer correctness from filenames, counts, summaries, or a partial inspection.
2. **Validate the premise.** Check whether the proposed change is necessary and supported by evidence. Distinguish observed defects, intended behaviour, proposals, and unresolved questions. Investigate available sources before requesting information. Apply `llm.general.clarification.process.md` when material uncertainty prevents reliable progress.
3. **Define preservation and scope.** Identify what must remain, what is authorized to change, and what is deferred. When consolidating or extracting material, map existing responsibilities to their new locations. Account for removed files, rules, and behaviour; a reference must lead to an accessible replacement. Preserve unrelated content and work.
4. **Validate design consistency.** Before proposing or implementing changes, evaluate the design against the established purpose, responsibilities, authoritative sources, and approved decisions:
	   - **Purpose:** Does the proposed content or functionality belong in this artifact?
	   - **Authority:** Does it preserve the established source of truth without introducing unnecessary duplication or competing authority?
	   - **Necessity:** Is each new field, rule, component, or abstraction required to achieve the intended outcome?
	   - **Consistency:** Does the proposal preserve existing agreements, architectural principles, and separation of responsibilities?
	   - **Simplicity:** Can the outcome be achieved with less complexity, duplication, or maintenance overhead?

   When reviewing a questionable design element, first determine whether it is necessary before attempting to improve it. Remove or avoid unnecessary elements rather than refining them. Resolve material conflicts through the applicable clarification process before proceeding.
5. **Explain material departures.** Describe consequential changes, removals, and trade-offs before implementation. Obtain approval for departures outside the authorized scope. Approval to improve or simplify material does not authorize unrelated changes. Use existing authorization for routine corrections; do not repeatedly request permission for the same plan.
6. **Apply and verify the change.** Make focused edits against the established baseline. Recheck currentness before overwriting potentially changed shared material, using conflict/version guards when available; reconcile conflicts rather than overwriting blindly. Compare the result with the preservation requirements and use appropriate checks. File consolidation, successful execution, or newly passing tests alone do not prove equivalence. Recheck affected content after corrections.
7. **Report the evidence.** State substantive changes, verification performed, unresolved uncertainties, and limitations. Distinguish inspected, tested, and inferred conclusions. Do not claim preservation, equivalence, successful saving, or application to the user's environment without evidence.

Keep the process proportional to the change. If new evidence invalidates the premise or reveals an omission, pause dependent work, explain the finding, and revise the approach. Continue independent authorized work where possible. Do not create additional reports solely to satisfy this process; use the parent prompt's records or a concise conversation summary.
