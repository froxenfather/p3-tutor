# Reviews: c1-skills

Your quick rounds while you build `c1-skills`, and then its major review, once you have snapshotted it and made its full run.
In this step no round adds a subagent, because subagents arrive in `c2-review` and `c3-split`: a round changes or adds a skill, or makes another change the skills need, such as an allow rule (Kind `other`).
Your first round can start from the tutor as it ships, so the baseline is the output without your first change.
The major review covers all four jobs, and its previous step is `c0-baseline`, so compare with your baseline runs.
What it finds becomes the checklists of your reviewer subagents in `c2-review`, so be specific.
`reviews/README.md` says how to write each part.
A rating on every criterion and What the next step should fix make the major review complete; the lines under each rating, Live tries and Compared with the previous step are optional, and you may leave their markers as they are.
You write your thoughts, ratings and feedback; Claude Code writes only the What changed part of each round.
Keep every heading as it is, because `p3 check` reads them, and add a round by copying the last one with its marker lines.

## Quick rounds

### Round 1

**Run:** bench/runs/c0-baseline/20261124-210541-agent-architecture-m30-r3

**My thoughts:**
The lesson was good, but its multiple-choice questions turn the right answer green while a "show answer" button sits right below, so it's too easy to skip the thinking. I'd remove the button, make learners retry until they get it, and make free-response questions require typing something before any feedback.

**What changed:**

- Kind: modified skill
- Files: tutor/.claude/skills/teach/references/lesson-template.html, tutor/.claude/skills/teach/references/LESSONS.md
- Why: Your thoughts said the show-answer buttons make practice too easy to skip, so multiple-choice questions lose the button and free-response questions need a typed attempt before the solution appears.

### Round 2

**Run:** bench/runs/c0-baseline/20261124-210541-agent-architecture-m30-r3

**My thoughts:**

The lesson is better with the typed answers, and its length felt right. I didn't change my mind about anything else in the lesson. My concern is now the tutor chat.
Seems like it always replies on why it cant do something and overexplains it before teelling them what it can do.

**What changed:**

- Kind: new skill
- Files: tutor/.claude/skills/tutor/SKILL.md
- Why: Your thoughts said the tutor over-explains why it cannot do something, so a new tutor skill leads with a redirect to where to study and keeps the refusal to one sentence.

### Round 3

**Run:** bench/runs/_live/20261127-191435-agent-architecture-m30-r1

**My thoughts:**

The new tutor is good. Its tone is a bit harsh, but that works for me, and I'm building this tutor for me. I like its structure, and I like that it points me to the workspace when there is one. I'd keep the tutor as it is and move on to the quiz.

**What changed:**

- Kind: new skill
- Files: tutor/.claude/skills/quiz/SKILL.md, tutor/.claude/skills/grade/SKILL.md
- Why: Your thoughts said to keep the tutor and move on to the quiz, so the quiz skill and, in the same pass to save tokens, the grade skill were added, which completes the four jobs.



## Major review

**Run:** bench/runs/c1-skills/20261127-193001-agent-architecture-m30-r1

**Live tries:**

Attempted several times to bypass the tutor's guardrails
and obtain quiz answers. The tutor consistently refused
without leaking answers. I also asked questions about
material that was not fully covered in the lesson.

### Lesson

#### Technical correctness and facts

Rating: 4/5

The material presented appears technically correct. However,
the judge identified one missing fact (F3.4). The issue
appears to be incomplete coverage rather than misinformation.
A baseline run also missed this same fact.

#### Pedagogy

Rating: 4/5

The teaching structure is effective, and I particularly
like having to type answers rather than simply clicking a
show-answer button. The tone and teaching style work well
for me. However, the lesson feels dense for its duration
and occasionally leaves important details unexplored.

#### Alignment with the learning goal

Rating: 3/5

The lesson teaches the core concepts well but does not
fully expand upon them or consistently connect all the
ideas necessary to achieve the broader learning goal.

#### Overall quality

Rating: 4/5

The lesson is well structured, uses an effective teaching
style, and feels appropriate for the requested duration.
Its biggest weakness is incomplete coverage of important
material.

### Quiz

#### Difficulty

Rating: 5/5

The questions are appropriately challenging. Each answer
choice is genuinely plausible without sufficient knowledge
of the material. The correct answers are not obvious,
and the questions do not unintentionally reveal them.

#### Coverage of the lesson's core

Rating: 3/5

The quiz adequately covers the core concepts presented
in the lesson. However, because the lesson itself does
not fully expand on every important concept, the quiz
coverage also feels incomplete.

#### Wording and possible misreadings

Rating: 5/5

The questions and answer choices are clear, concise,
and unambiguous. I did not encounter any noticeable
wording issues or misleading interpretations.

#### Writing quality

Rating: 5/5

The quiz is exceptionally well written. The questions
are structured effectively, and the answer choices
are meaningful without giving away the correct answer.

#### Alignment with the learning goal

Rating: 3/5

The quiz effectively tests individual concepts but does
not always connect those concepts to the broader learning
goal. More comprehensive questions connecting multiple
ideas would improve its alignment.

### Feedback

#### Useful

Rating: 5/5

The feedback is constructive, relevant, and useful.
The tutor understands my questions and helps me work
through misunderstandings effectively.

#### Explains enough

Rating: 4/5

The tutor provides sufficient explanations, even when
I ask about material that was not covered in the lesson.
However, it is frustrating to discover important concepts
through follow-up questions when they should have been
included in the original lesson.

#### Personalized to how I like things explained

Rating: 5/5

The feedback is extremely well personalized to my learning
preferences. It is direct, appropriately challenging,
and does not unnecessarily soften corrections.

### Tutor

#### Guardrails

Rating: 5/5

The guardrails are extensive and effective. After several
attempts to obtain quiz answers or bypass restrictions,
I was unable to do so. The tutor keeps its refusals short
without leaking answers or providing unnecessary information.

#### Personalization

Rating: 5/5

The tutor's tone and teaching approach align extremely
well with my learning preferences. Although the tone
can be harsh, I prefer direct feedback. I also appreciate
being directed toward the workspace when one is available.

### Compared with the previous step

This configuration improves upon the baseline in lesson
structure, quiz quality, tutor personalization, and
guardrail effectiveness.

However, these improvements come at a substantial
computational cost. Lesson generation consumes approximately
1.4 times the baseline's tokens, while quiz generation
consumes approximately 1.9 times as many tokens.

My initial concern was factual correctness, but the judge
identified a missing fact rather than an incorrect one.
A baseline run also missed the same fact.

The primary concern moving forward is whether these
improvements can be maintained while reducing computational
cost and improving lesson completeness.

### What the next step should fix

- Reduce token consumption without sacrificing teaching,
  quiz, or tutor quality.
- Ensure the lesson covers all required facts and concepts.
- Improve the connections between individual concepts
  and the broader learning goal.
- Include important explanations in the original lesson
  rather than relying on the learner to discover missing
  material through follow-up questions.
- Preserve the existing personalization, quiz difficulty,
  and tutor guardrails.
