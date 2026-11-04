# Software Severity Rubric

## Version

Version: 1.0

## Objective and Scope

Classify the impact of functional, operational, security, and data-protection issues consistently. Severity describes impact; it does not by itself determine priority, remediation timing, or authorization to implement a fix. The parent prompt defines issue records and decision gates.

## Assessment Rules

- Use **Critical / Major / Minor**. Assess the credible impact on the actual affected system, users, data, and agreed requirements. Identify the affected capability and explain the rating; do not assume every startup failure or intermittent fault has the same severity.
- Describe exposure, likelihood, existing controls, recovery options, and uncertainty separately when recommending priority or action. Do not lower impact severity merely because an event is unlikely. Controls may limit the credible scope of impact; explain any such limitation rather than treating controls as a generic severity discount.
- Distinguish observed defects, suspected issues, and future requirements. Do not call an unverified weakness a confirmed vulnerability. Use a provisional rating with its assumptions when evidence is incomplete.
- When an issue spans categories, use the highest supported impact and explain the affected categories. Do not inflate severity for hypothetical chains unsupported by the environment or evidence.

## Severity Levels

| Severity | Functional and operational impact | Security and data-protection impact |
| --- | --- | --- |
| Critical | Prevents essential operation or startup of the affected system, breaks core functionality without a practical workaround, or can cause prolonged outage or substantial data loss/corruption. | Can permit broad unauthorized access or administrative compromise, substantial sensitive-data disclosure/destruction, or severe loss of system availability. |
| Major | Substantially impairs an important capability, causes materially poor performance or recurring failures, or requires a significant workaround while essential operation remains possible. | Can permit meaningful unauthorized access, disclosure, or modification, or substantially weakens a protection, with impact more limited than Critical. |
| Minor | Causes limited disruption or inconvenience, with a practical workaround or straightforward recovery and no substantial loss of essential capability. | Creates a weakness whose credible impact is limited in the actual environment; remediation may still be appropriate. |

## Use and Reassessment

Report the concern, evidence, affected scope, severity and rationale, followed by the action recommendation and relevant uncertainty. Use the parent's record format rather than introducing a new issue register.

Deferring an issue does not lower its severity. Reassess when evidence, affected scope, requirements, or environment changes; retain the earlier assessment and reason for revision in the designated record. Ordinary writing preferences are editorial findings, not automatically software defects; do not force them into this rubric.
