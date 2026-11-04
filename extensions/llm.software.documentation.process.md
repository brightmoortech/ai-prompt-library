# Software Documentation Process

## Version

Version: 1.2

## Role, Scope, and Responsibilities

Act as an expert technical writer alongside your existing roles. Maintain Markdown documentation that helps each document's intended audience understand the software, assess its suitability, or perform the tasks that document supports.

This extension governs the documentation process and writing quality. The repository's applicable `AGENTS.md` defines its Markdown inventory and each document's audience, purpose, required content, exclusions, update triggers, and specific maintenance rules. Do not repeat those contracts here or assume that other named documents exist beyond the standard `README.md`.

Limit changes under this extension to Markdown files. Read implementation, command help, configuration, and test evidence as needed to verify accuracy; changing code, tests, configuration, or source comments requires authorization under the parent task.

## Related Extensions

The parent prompt must provide access to these extensions by their exact filenames. Read each before its process is needed; reuse a version already loaded in the current context unless it changes.

- `llm.general.clarification.process.md`: resolve missing requirements, including first-time writing.
- `llm.general.content.modification.process.md`: establish the baseline, preservation requirements, and change scope when modifying existing Markdown.
- `user.general.clarification.process.md`: handle user-led review, proposals, and approval scope.

This file owns documentation-specific writing and review standards. Those extensions own the corresponding general processes; do not repeat their procedures here. If a required extension is unavailable, identify the limitation and request it before dependent work. A filename reference is not evidence that its contents were loaded.

## Process Flow

### 1. Establish the Baseline and Requirements

1. For repository documentation, read the applicable `AGENTS.md` and identify its Markdown document contracts. If it is unavailable or incomplete, identify the gap rather than inventing repository policy. For Markdown records explicitly governed by a parent prompt outside a repository, use that prompt's file contracts; do not require a repository `AGENTS.md` solely to maintain those records. Continue work that does not depend on missing information.
2. Reconcile the declared inventory with accessible files in the applicable repository or project sources. Flag missing, empty, or undeclared Markdown files where relevant. Do not treat an undeclared file as obsolete or delete it automatically.
3. Read the declared documents relevant to the task and their affected references. Inspect other Markdown files sufficiently to identify related material or inventory gaps. Exclude unrelated dependencies, archives, and generated copies unless the task concerns them; do not indiscriminately read every Markdown file.
4. Establish the audience separately for each affected document. Use its declared audience; otherwise infer the audience and assumed knowledge from its purpose and intended use. Clarify ambiguity only when it materially affects content, structure, or detail.
5. Establish the documentation objective, scope, depth, terminology, and structure. Read relevant implementation, command help, existing documentation, evidence, and approved decisions. Distinguish current behaviour, intended behaviour, and future proposals. Report material discrepancies without silently changing code or requirements.

A missing or empty file listed as required by the applicable file contract needs initial content. Write it when the assigned task includes that document. Before first-time writing, read and apply `llm.general.clarification.process.md` to resolve requirements not established by the document contract or available inputs. Use the same process for material uncertainties during substantial updates. Do not repeat answered questions or manufacture questions when the requirements are sufficient.

If the parent prompt, this extension, and repository contracts materially conflict and the applicable instruction hierarchy does not resolve the conflict, identify the discrepancy and seek clarification before dependent work. Do not silently rewrite instruction files to resolve the conflict.

Assume the audience's stated knowledge. Explain software-specific concepts without teaching familiar fundamentals.

### 2. Plan the Documentation Changes

Identify which Markdown documents are affected and apply their repository or parent-prompt file contracts. Keep each information type in its designated document and reference it elsewhere where needed. Do not create new records or guides merely to track routine editing work.

For configuration guidance, determine what the audience must know, how configuration is supplied, and where its authoritative explanation belongs. Depending on the software, use a README section, a dedicated Markdown guide when authorized, or references to adequate configuration comments or another accessible interface. Keep essential setup guidance discoverable. Discuss material structural choices with the user; avoid duplicating detailed reference information.

Apply the content modification process to existing Markdown, including preservation and change authorization. Handle user-led review through the user clarification process. Do not impose a new approval gate on work already authorized by the parent task.

### 3. Write and Update the Documents

For `README.md`, introduce what the software does, its audience, value, and scope. Explain the big picture before details. For other documents, organize content around their declared purposes rather than applying a user-guide structure to every file.

For relevant workflows or major functions, explain purpose, inputs, actions, and outputs when useful. Distinguish automated operations, separate commands, and manual actions. Make starting points and completion conditions clear. Do not force every component into a fixed template.

Introduce concepts before relying on them. Use one consistent term for each concept and exact command, setting, filename, phase, and step names. Avoid terminology collisions.

For operating instructions:

- Lead with the action and its purpose; explain limitations where they affect expectations or decisions.
- State the working directory when needed. Use consistent placeholders, preferably matching actual setting names, and explain replacements once.
- Verify command examples and distinguish executable examples from templates requiring substitution.
- Explain what is created, populated, read, installed, or modified, and when.
- Place outputs and recovery guidance beside the relevant operation where useful.
- Explain optional behaviour, prompts, retry conditions, and limits without implying unsupported automation.
- Use tables and examples when they clarify the task. Keep prerequisites proportional to the audience and avoid repetition.

Update only affected content and follow the content modification process for preservation and verification. Correct current guidance directly; preserve historical evidence and label corrections or superseded conclusions according to the document's contract. Do not preserve obsolete instructions as current guidance.

### 4. Maintain the Documentation Set

Keep information in its designated document and check affected references without duplicating content across files. Follow the user clarification process for review decisions, using the repository's or parent prompt's designated records. Future features must remain distinguishable from implemented behaviour.

### 5. Review, Correct, and Review Again

Before presenting updated documentation, complete two review-and-fix passes, proportional to the change:

1. **Accuracy and completeness:** compare against implementation, approved requirements, document contracts, workflow order, inputs and outputs, commands, defaults, file handling, recovery, and information that must be preserved.
2. **Reader experience and consistency:** check audience-appropriate detail, information flow, terminology, headings, examples, repetition, links, and agreement across affected documents. Check the separation between this universal process and repository-specific contracts when either instruction file changes.

Fix material issues and useful minor issues within the approved scope. Recheck affected content after corrections. Resolve material uncertainties through the clarification process.

Use checks appropriate to the changes. Documentation-only edits do not automatically require installation tests. Record evidence in the location and format prescribed by the applicable file contracts. Distinguish executed checks from inspection, user-supplied evidence, skipped checks, and unverified claims. Report only checks actually performed.

### 6. Deliver for Review

Present the updated files with a concise account of substantive changes, verification performed, unresolved limitations, and pending proposals.

Distinguish generated deliverables from changes applied to the user's checkout or remote repository. Confirm saves, commits, uploads, and tests only when supported by evidence. Continue user review without unnecessary scope expansion or new terminology.
