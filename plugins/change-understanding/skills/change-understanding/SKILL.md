---
name: change-understanding
description: Assess the user's understanding of a code change through questions grounded in the diff. Use when asked for an understanding check or a score-based commit gate, rather than an ordinary code review.
---

# Change Understanding

Read the repository instructions, intended diff, and relevant code and tests. State what change is being assessed; clarify the scope only when needed. Use the user's language.

Ask one short question about a single point at a time and wait for the user's answer. Do not bundle multiple API roles, behaviors, or predicted outputs into one question; split them into separate turns. Do not reveal the answer first. Each area may take multiple questions to assess. Cover five areas, each worth 20 points:

- Purpose: the problem and the change in behavior.
- Flow: concrete inputs, state changes, and outputs.
- Design: reasons for the approach and relevant tradeoffs.
- Boundaries: relevant edge cases and failures.
- Verification: which behavior this change needs tested and how to check it. Choose a concrete case from the diff, rather than defaulting to unit versus integration test coverage.

Judge explanations against the code, not fluency or memorized terminology. Allow looking things up. Include at least one prediction about a new input or a small change to the code. Keep questions proportional to the change; do not invent requirements.

After each answer, briefly explain what is correct, what is missing, and the current score. Mark unassessed areas separately. Explain gaps, then reassess with a different example. Resolve your own uncertainty before judging an answer wrong.

A score of 100 means all five areas have been demonstrated, not that understanding is complete. Until then, do not commit while this skill is active. Commit only when the user has requested it and relevant checks pass. Before committing, confirm that the staged diff matches the assessed change; reassess affected areas if it changed. Keep unrelated changes out of the commit.

Respect requests to stop or explicitly waive the gate. Report the assessment honestly. This skill governs the assistant's actions; it does not install Git hooks or restrict manual commits.
