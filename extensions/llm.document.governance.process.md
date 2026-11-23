# Document Governance

## 1. Purpose and Scope

Govern the creation, modification, review, and delivery of project documentation. Compliance with instructions, approved decisions, established processes, and correctness takes priority over completion speed. Apply this process to every authorized document creation or modification, including changes to this document and `AGENTS.md`.

For review-only assignments, apply the two audit criteria to the existing document and report findings and recommended corrections without modifying it. Obtain authorization before making corrections. The final-file delivery gate applies when creation or modification is authorized; review-only reports must still identify checks performed, evidence, findings, and limitations.

The assigned task and applicable source documents determine scope and authority. This process does not authorize changes to requirements, software, other documents, or project stages.

## 2. Authorization and Baseline

- Distinguish review, approval of a proposal, and authorization to create or modify a document. Review comments alone do not authorize regeneration or modification.
- Before modifying an existing document, read its complete current version, establish its baseline, inspect available repository status and uncommitted changes, and identify the authorized changes and affected documents. Preserve unrelated content, approved decisions, and user changes.
- For a new document, establish its authorized purpose, audience, location, and applicable sources. Do not create additional documents merely for process completeness.
- Read applicable requirements, decisions, and governing documents before drafting. Resolve conflicts using established document authority and the applicable clarification process; never silently reinterpret requirements.
- If required source material or the current baseline is unavailable, disclose the limitation. Do not proceed with changes that require an unavailable baseline or source, and do not claim checks that depend on unavailable evidence have passed.

## 3. Drafting Standards

- Write for the intended audience. Preserve established terminology, document structure, and section purposes unless changes are authorized.
- Make instructions self-contained and understandable without conversation history. Use references to authoritative project documents instead of duplicating their requirements.
- Keep functional requirements separate from technical specifications. Distinguish implemented functionality from planned functionality.
- Avoid unnecessary historical commentary, repetition, complexity, and explanations. Retain history and evidence where the document's purpose requires them.
- Verify commands, configuration examples, filenames, paths, and references against available sources and implementation evidence. Do not imply that an unexecuted command or test was executed.
- Update only documents affected by authorized changes. Apply established document-specific rules, including approved structure and intentionally blank sections.

## 4. Audit Pass 1: Content Accuracy and Compliance

After creating or modifying the actual file, reopen and read it in full. Compare its content against applicable authoritative sources, approved decisions, the assigned scope, and implementation or execution evidence where relevant.

Check:

- Coverage of all applicable requirements and agreed changes; completeness for the document's intended purpose.
- Factual accuracy, evidence, and clear distinction between confirmed facts, assumptions, proposals, and planned or implemented functionality.
- Consistency with applicable requirements, decisions, instructions, and related documents; no invented requirements or unsupported claims.
- Authorization and scope compliance. For an existing document, compare the original and revised versions to verify that every authorized change is included and unrelated content and user changes are preserved.

Record specific findings, identifying the affected document section and the applicable authoritative source and section or other supporting evidence. Correct issues automatically within the authorized scope. If a correction requires a material user decision or additional authorization, identify the issue and use the applicable clarification process; do not assume approval. Independent authorized corrections may continue.

Reopen the corrected file and verify the corrections before starting Audit Pass 2.

## 5. Audit Pass 2: Document Quality

Reopen and independently review the complete corrected file afresh from the intended reader's perspective against the criteria below. Independence means a distinct review using these criteria, not reliance on the first audit conclusions; it does not require a separate reviewer.

Check:

- Clarity, conciseness, readability, and suitability for the intended audience.
- Consistent terminology, internal logic, organization, section purposes, and logical flow.
- Self-contained instructions, appropriate separation of content, and absence of unnecessary duplication or complexity.
- Accuracy and consistency of commands, configuration examples, filenames, paths, cross-references, and formatting.

Record specific findings, identifying the affected document section and the applicable authoritative source and section or other supporting evidence. Correct issues within scope and verify the corrections. If a correction affects a previously verified requirement, decision, or factual statement, repeat the affected Pass 1 checks. Repeat affected checks until material findings are resolved.

## 6. Final Verification and Delivery Gate

Before presenting any created or modified document as final:

1. Reopen the actual final file and verify that all corrections are present. For modifications, compare it with the original baseline again to confirm preservation and authorized scope.
2. Confirm both distinct audit passes were performed against the actual file, not merely the draft plan or an earlier version. For multiple files, verify each file and relevant cross-document consistency.
3. Confirm all material findings are resolved and applicable checks have supporting evidence. If a material issue remains, report the blocker rather than deliver the document as final or claim that the audits passed.
4. Provide a concise audit summary identifying the document reviewed, the sources or evidence consulted, the checks actually performed, material findings and corrections for each pass, and any outstanding limitations. If no findings are identified, state this and identify the concrete checks supporting that conclusion. Distinguish passed, failed, blocked, and not applicable checks; explain blocked or not applicable checks where material.

An assertion that an audit passed is not evidence of its execution. Do not fabricate findings, test results, source comparisons, or verification. Do not claim independent reviewers or tools were used unless they actually were. Retain audit evidence in the conversation unless an applicable process specifies another location; do not create an additional audit file without authorization.

Document delivery does not itself constitute user acceptance, repository commit authorization, or permission to advance a project stage.
