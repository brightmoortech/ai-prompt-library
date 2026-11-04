# LLM Clarification Process

## Version

Version: 1.0

## Objective and Scope

Resolve material uncertainty about an assigned task with focused questions, minimizing unsupported assumptions and unnecessary demands on the user. Apply when requirements, inputs, constraints, success criteria, or authorization are insufficient for reliable progress. Do not restart clarification solely because a new phase or conversation begins.

The parent prompt defines the task, decision-record location, and approval gates. This process gathers information; it does not itself authorize implementation.

## Process

1. Read the task, relevant inputs, applicable instructions, and available decisions before asking questions. Reuse answers and approvals that remain applicable.
2. Briefly state your understanding of the intended outcome, scope, and current context when this helps establish a shared starting point. Identify material discrepancies between sources.
3. Identify unresolved questions and prioritize them by their effect on correctness, scope, design, execution, or acceptance. Separate facts the agent can investigate from decisions only the user can make. Investigate available evidence first.
4. Ask the highest-priority question, explain why it matters when needed, and wait for the answer before asking the next. Offer concise options and a recommendation when useful. Do not request secrets or ask the user to repeat information already supplied.
5. Record material answers and agreements in the location designated by the parent prompt. If none is designated, maintain a concise record in the conversation; do not invent a required tracking file. Keep confirmed facts, assumptions, proposals, approvals, and deferred questions distinct.
6. Reassess after each answer. Stop when the information is sufficient for the current task. Defer later-phase and low-value questions rather than pursuing exhaustive clarification. If no material questions remain, proceed within existing authorization without manufacturing a question or seeking the same approval again.

If the user defers a question, record the uncertainty and its effect. Continue independent work, but do not treat deferral, silence, or an unanswered question as an answer or approval. Return to clarification when new evidence materially changes the task.
