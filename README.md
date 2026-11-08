# AI Prompt Library

A public library of reusable AI prompts, process extensions, and document templates maintained by **Brightmoor Technologies Inc.**

## Purpose

The library provides modular instructions for working with AI assistants on structured tasks. Separating high-level prompts from reusable processes reduces duplication, keeps responsibilities clear, and makes instructions easier to maintain and reuse across projects.

## Repository contents

| Directory                    | Purpose                                                                   |
| ---------------------------- | ------------------------------------------------------------------------- |
| [`prompts/`](prompts/)       | High-level prompts that define a task, workflow, and required inputs.     |
| [`extensions/`](extensions/) | Reusable processes and rubrics that a parent prompt can invoke as needed. |
| [`templates/`](templates/)   | Starting documents for outputs produced through a prompt workflow.        |

### Prompts

| File | Description |
| --- | --- |
| [`llm.software.config.generation.prompt.md`](prompts/llm.software.config.generation.prompt.md) | Guides a developer through identifying software environment configuration, preparing and approving a `TARGET_SPECIFICATIONS.md`, and then generating, validating, comparing, and separately approving native configuration files. Uses the target specifications template and relevant extensions. |

### Extensions

| File                                                                                                      | Description                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`llm.general.clarification.process.md`](extensions/llm.general.clarification.process.md)                 | Resolves material uncertainty through focused, one-at-a-time questions while preserving established answers and decisions.                                                                                |
| [`llm.general.content.modification.process.md`](extensions/llm.general.content.modification.process.md)   | Governs changes to existing material: establish the baseline, assess necessity and consistency, preserve unrelated work, verify changes, and report evidence.                                             |
| [`llm.software.documentation.process.md`](extensions/llm.software.documentation.process.md)               | Defines a process for writing and maintaining accurate software Markdown documentation, including review-and-fix passes.                                                                                  |
| [`software.architecture.principles.md`](extensions/software.architecture.principles.md)                   | Defines the software architecture principles that the AI must understand and balance based on its set business outcomes and functional scope. These principles are for software, not agentic development. |
| [`software.severity.rubric.md`](extensions/software.severity.rubric.md)                                   | Classifies functional, operational, security, and data-protection issues as Critical, Major, or Minor based on credible impact.                                                                           |
| [`user.general.clarification.process.md`](extensions/user.general.clarification.process.md)               | Supports user-led questions, options, reviews, and decisions while respecting the parent prompt's approval boundaries.                                                                                    |
| [`windmill.workflow.architecture.principles.md`](extensions/windmill.workflow.architecture.principles.md) | Defines reusable naming, architecture, design, implementation, and maintenance principles for Windmill workflows.                                                                                         |

### Templates

| File | Description |
| --- | --- |
| [`TARGET_SPECIFICATIONS_TEMPLATE.md`](templates/TARGET_SPECIFICATIONS_TEMPLATE.md) | Reusable Markdown template for documenting the target software environment, services, networking, storage, configuration, identities, and outstanding configuration choices. Its filename is intentionally retained for compatibility with the configuration-generation prompt. |

## How to use

1. Choose a high-level prompt from `prompts/` that matches your task.
2. Read its required-input and dependency sections. Supply the prompt, the referenced extensions and templates, and any relevant project files to your AI assistant. **A filename reference alone does not load a file.**
3. Follow the prompt's workflow, including its review and approval checkpoints. Keep project-specific outputs and decisions in the relevant project, not in this reusable library.

You can read and edit these standard Markdown files with any compatible editor. No special editor or automation framework is required. The assistant's ability to access local files depends on the environment in which it is running.

## Naming and versions

Prompt and extension filenames use lowercase dot-separated components:

`[<actor>.]<domain>.<subject>[.<action>].<module_type>.md`

The actor and action components are optional. Module types include `prompt`, `process`, and `rubric`. The existing `TARGET_SPECIFICATIONS_TEMPLATE.md` is an intentional exception to the lowercase convention.

Document versions are recorded **inside each file**, not in its filename. Git history records repository changes. When a file is renamed, references in dependent files must be updated as part of the same change.

## License

Unless a file says otherwise, the original material in this repository is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

Copyright © 2026 Brightmoor Technologies Inc. See [`LICENSE`](LICENSE) for the full license text. Attribution is required when sharing or adapting the material, including for commercial use.
