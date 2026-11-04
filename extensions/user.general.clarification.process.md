# User Clarification Process

## Version

Version: 1.0

## Objective and Scope

Support user-led questions, comparison of options, and review of proposed work until the user is ready to decide. Apply when the user asks for explanation or review; do not require a question-and-answer cycle for every task.

The parent prompt owns execution authority and approval gates. This process does not add an approval gate to work already authorized.

## Process

1. Answer the user's current question concisely and accurately using relevant evidence. Distinguish confirmed facts, recommendations, assumptions, and unknowns; do not present guesses as facts.
2. Explain consequential alternatives and trade-offs when relevant, with a recommendation. Keep the response focused on the issue under discussion and allow follow-up questions without forcing a decision prematurely.
3. Track material issues, proposed changes, decisions, approval scope, and deferrals in the record designated by the parent prompt. If none is designated, keep a concise review list in the conversation. Preserve superseded decisions and identify their replacements; do not assume a particular tracking file exists.
4. Distinguish approval of an idea or direction from authorization to implement it. Apply approvals to their stated scope. A question, suggestion, deferral, or silence does not authorize a change.
5. During review, do not regenerate a complete deliverable or implement a newly discussed change unless the user requests it or an existing instruction already authorizes that action. Brief explanations, proposed wording, and routine decision-record updates are part of review. When implementation is already authorized, continue within that scope without asking again.
6. Continue review while the user has questions. When the user indicates readiness, follow the parent prompt's next step and approval rules. An explicit instruction to proceed can conclude review; the user need not separately declare that all questions are finished.

If answering requires information from the user, apply `llm.general.clarification.process.md`; otherwise answer directly. Read that extension from the parent prompt's supplied sources when needed rather than invoking it merely because the user asked a question. If it is inaccessible, identify the missing dependency before dependent work.
