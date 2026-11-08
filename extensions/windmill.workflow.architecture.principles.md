# Windmill Workflow Architecture Principles

## Version

Version: 1.1

## Purpose and Scope

Define reusable naming, architecture, design, implementation, and maintenance principles for Windmill workflows across projects.

Apply these principles to new and modified Windmill workflows unless an applicable project-specific requirement or approved design calls for a different approach. They are design guidance, not a requirement to create tasks, branches, or subworkflows when a simpler workflow suffices. Existing workflows can inform design choices but are not automatically authoritative examples of best practice.

This document governs **how workflows are designed and organized**. It does not define any particular workflow's business logic, services, routing destinations, schedules, acceptance tests, or deployment authorization. Those belong to the applicable project requirements, approved design, and implementation records.

## 1. Naming

| Element | Convention | Example |
| --- | --- | --- |
| Workflow name and YAML filename | Lowercase `snake_case`; YAML basename matches workflow name | `process_records` / `process_records.yaml` |
| Task ID | Lowercase `snake_case`, preferably verb + specific object or outcome | `validate_input`, `save_record` |
| Task display name | Descriptive Title Case | `Validate Input`, `Save Record` |
| Decision task | Describe the specific decision rather than using a generic name | `check_save_outcome` |
| Result task | `return_` followed by the outcome | `return_success` |
| Input parameter / output field | Lowercase `snake_case` | `record_id`, `result_code` |
| Status value | Lowercase `snake_case` | `success`, `needs_review` |

Prefer IDs that describe a task's actual responsibility; avoid generic identifiers such as `check_result` when a clearer name is available. Existing task IDs are not automatically renamed to conform.

## 2. Task Design and Modularity

1. Give each task one distinct logical responsibility.
2. Prefer Windmill's native workflow controls for branches, loops, and orchestration rather than burying control flow inside Python scripts.
3. Reuse existing workflows or shared scripts for established functionality rather than copying their logic.
4. Separate integration operations, business logic, and database persistence when they represent distinct responsibilities.
5. Avoid unnecessary fragmentation: simple transformations may remain within an existing task.

Choose task boundaries to keep the workflow visually understandable, independently testable where useful, and straightforward to troubleshoot.

## 3. Branching and Control Flow

1. Use native Windmill branching to select the next execution path.
2. Write explicit conditions against structured task results, for example `results.save_record.status === "success"`.
3. Name branches for their condition or outcome.
4. Provide a default path for unexpected or unrecognized results; never silently interpret them as success.
5. Use native Windmill loops for repeated work.
6. Keep orchestration visible: task scripts produce results; Windmill controls the subsequent path.

Workflow-specific termination and continuation conditions must be specified in that workflow's approved design; they are not universal defaults.

## 4. Data Contracts and Communication

1. Return structured dictionaries/objects with clearly named fields.
2. Map task inputs explicitly through Windmill `input_transforms`, using `flow_input` or earlier task `results` as appropriate. Do not rely on hidden shared state.
3. For operations with multiple business or technical outcomes, use a `status` field with documented allowed values.
4. Treat output fields consumed downstream as contracts; review affected consumers when changing those fields.
5. Pass the data needed by downstream operations without unnecessary duplication or premature loss of required information.
6. Represent genuinely missing optional values as `null`, not invented defaults.

**Illustrative task result:**

```json
{
  "status": "valid",
  "data": {
    "record_id": "example-001",
    "optional_note": null
  }
}
```

This example illustrates the shape of a structured result; each workflow defines its own fields and permitted statuses.

## 5. Errors, Outcomes, and Failure Propagation

1. Distinguish expected business outcomes (such as invalid input or an identified duplicate) from technical failures.
2. Return structured status and meaningful details for expected outcomes.
3. Retain troubleshooting information needed to investigate technical failures without exposing secrets or sensitive information.
4. Report and explicitly handle unexpected exceptions; do not conceal them.
5. Centralize technical exception handling where practical, using native Windmill capabilities.
6. Do not automatically retry an operation that might have committed data or produced an irreversible external effect unless safe retry behavior has been explicitly designed and approved.
7. Apply the workflow's agreed stop and continuation conditions.

For any operation that changes persistent state or an external system, define whether subsequent execution may continue following a failed or uncertain result. Do not confuse a reported failure with proof that an external operation did not take effect.

## 6. YAML Organization and Maintenance

| Area | Convention |
| --- | --- |
| Workflow file | One YAML definition per workflow; filename matches workflow name |
| Workflow-specific scripts | Embed task scripts in the workflow YAML when functionality is specific to that workflow; use the language appropriate to the task |
| Reusable logic | Invoke an existing workflow or shared script rather than duplicate it |
| Dependencies | Declare required packages explicitly and retain Windmill-generated dependency locks |
| Source control | Keep the exported YAML in Git as the reproducible workflow definition |
| Change process | Modify the source-controlled definition and validate it before replacing a deployed workflow |
| Verification | Check YAML syntax, Windmill import compatibility, task/resource references, and runtime behavior |

A valid YAML document alone does **not** demonstrate a functional Windmill import or execution. Environment-specific resources, credentials, worker capabilities, and dependencies require verification in the target environment.

## 7. Workflow Architecture and Reuse

1. For a business process requiring orchestration, use one main workflow to own its overall execution. A simple workflow need not be split into multiple workflows.
2. Invoke existing workflows when they implement established reusable business capabilities.
3. Keep functionality specific to the main workflow within its YAML unless actual reuse or complexity justifies a separate component.
4. Do not create subworkflows solely for modularity.

A reusable capability should have a stable, documented input/output contract. The parent workflow remains responsible for orchestration, including interpreting the capability's result and selecting the next action.

## 8. Design and Delivery Check

Before generating a workflow YAML, review the existing relevant workflow(s) and explicitly agree on any new architecture or naming decisions that are not covered here. For each new workflow:

- Establish its task responsibilities, data contracts, branches/loops, failure paths, and reused components from the approved workflow-specific design.
- Generate an importable YAML proposal that follows these conventions, while preserving existing dependencies and interfaces where applicable.
- Validate the YAML and its references, import it in Windmill, inspect the visual structure, and verify actual execution against the workflow's approved acceptance tests.
- Treat import, runtime validation, and deployment as distinct results; do not claim that successful generation proves successful execution.

## Authority and Change Boundaries

These principles cover seven areas: naming; modularity; branching/control flow; data contracts; error handling; YAML organization/maintenance; and workflow architecture/reuse. This document does not authorize implementation, modification, import, or deployment. The applicable project requirements, approval rules, and validation procedures govern those actions.
