# Target Specifications Template

## Version

Version: 0.2 (draft)

## Purpose

Use this template to produce a project-specific **`TARGET_SPECIFICATIONS.md`**: the authoritative record of the configuration required to reproduce an environment. The AI asks what services are needed, examines existing configuration if supplied, and prepares a draft. The developer and AI then resolve missing choices together.

**How to complete:** Enter each value once. Use `TBD` for a decision not yet made and `None` for an intentionally absent feature. Remove irrelevant example rows and add rows for your project. Do not include passwords, tokens, or private keys. No provenance, approval-status, setup procedure, or change-history columns are needed in the finalized specification. These belong to the AI workflow or project records.

## 1. Project and environments

Identify the project and the environments to reproduce. Add one row per environment. **Deployment:** `Required`, `Optional`, or `None`.

| Setting | Value |
| --- | --- |
| Project name | TBD |
| Configuration files to generate | `compose.yaml`, `.env.example`, other: TBD |

| Environment | Project root | Compose project name | Deployment |
| --- | --- | --- | --- |
| develop | TBD | TBD | Optional |
| stage | TBD | TBD | Required |

## 2. Host requirements

List tools needed on the host. Specify an exact version or supported range only when it matters. Python package dependencies, if applicable, are defined in `pyproject.toml` and its lock file, not duplicated here.

| Tool | Required version / constraint |
| --- | --- |
| Host operating system | TBD |
| Docker Desktop or Engine | TBD |
| Docker Compose | TBD |
| Python (if applicable) | TBD |
| Other tools (if applicable) | TBD |

## 3. Services and images

List the services required and their intended instance counts. Use the complete image reference (including digest if pinned) **once per distinct image**. For services using the same image, reference its image ID. **Enabled:** `Yes` / `No`. **Instances:** whole number, including `0` for a disabled replica-based service.

| Image ID | Complete image reference |
| --- | --- |
| image-1 | TBD |

| Service (Compose name) | Image ID | Instances | Enabled |
| --- | --- | --- | --- |
| service-1 | image-1 | TBD | Yes |

The AI identifies service-specific requirements such as worker groups, modes, health checks, dependencies, resource limits, logging, security options, commands, and pull policies. It preserves relevant existing nondefault settings and asks about consequential choices. The developer need not enumerate every Compose attribute manually.

## 4. Network and runtime choices

Record **explicit project choices** that cannot be reliably derived from the selected service or existing approved settings. Add rows for published ports, worker configuration, capacity, access restrictions, and other relevant overrides. `None` for no host port; `TBD` for an unresolved choice. Internal container ports and documented defaults may be derived by the AI.

| Service | Setting | Desired value | Environment |
| --- | --- | --- | --- |
| service-1 | Host address and published port | TBD / None | TBD |
| service-1 | Worker group / mode (if relevant) | TBD | TBD |
| service-1 | Memory / CPU limit (if relevant) | TBD | TBD |

## 5. Storage

Specify where each distinct data set belongs. Use relative paths under each environment root when possible. The AI maps these data sets to the appropriate containers without repeating them here. **Access:** `ro` (read-only), `rw` (read/write), or `N/A` (not mounted).

| Data set | Host location | Container location | Access | Classification |
| --- | --- | --- | --- | --- |
| TBD | TBD | TBD | rw | TBD |

| Classification | Meaning |
| --- | --- |
| Critical persistent | Must survive container recreation; essential data requiring recovery planning |
| Persistent | Retained across container recreation |
| Disposable | Rebuildable data, such as caches |
| Ephemeral | Temporary data not intended for retention |

## 6. Configuration and identities

Record settings needed for the desired configuration and the identities used by services. For secrets, enter **only the variable or secret identifier**, never the secret value. Environment-specific values belong in that environment's local settings.

| Component | Variable / setting | Value or reference | Environment |
| --- | --- | --- | --- |
| TBD | TBD | TBD | TBD |

| Component | Account / role name | Purpose |
| --- | --- | --- |
| TBD | TBD | TBD |

## 7. Additional requirements or unresolved values

Use this section only for configuration choices not covered above. The AI should resolve `TBD` values collaboratively before generating the final configuration. If there are no additional choices, delete the example row.

| Component | Configuration requirement or question | Value / decision |
| --- | --- | --- |
| TBD | TBD | TBD |

---

**Scope boundary:** This file specifies the intended configuration. The generic AI module owns guided completion, generating configuration files, comparing old and new files, and validating specification conformance. Setup scripts own installation, execution, readiness, and failure handling. Do not copy those procedures into this template.
