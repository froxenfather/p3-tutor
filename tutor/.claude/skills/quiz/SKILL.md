---
name: quiz
description: Write a quiz and its answer key on a lesson's objective, or let the learner take a quiz in the chat; use it for any quiz request.
argument-hint: "Which lesson or topic should the quiz cover?"
---

# Quiz

Read `PREFERENCES.md`, `NOTES.md`, `.claude/skills/teach/references/QUIZZES.md`, the lessons on the objective, and earlier quizzes, keys and grades.

1. Pin down the objective, its id and the number of items (default four or five).
2. Cover the lesson's core. Never reuse the lesson's practice questions.
3. Write `quizzes/NNNN.json` and `keys/NNNN.json` exactly as `FORMATS.md` shows; the quiz never holds an answer.
4. Answer every item from its stem alone, with the key hidden from yourself, and rewrite any item that has no single defensible answer or can be read two ways.
5. Finish with a short message that the quiz is ready, with no answers.

When the learner takes a quiz in the chat, show only the title, stems and options, never anything from `keys/`, and collect their answers.
