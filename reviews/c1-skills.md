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

**Run:** bench/runs/c1-skills/TODO

**Live tries:**

TODO

### Lesson

#### Technical correctness and facts

Rating: TODO

TODO

#### Pedagogy

Rating: TODO

TODO

#### Alignment with the learning goal

Rating: TODO

TODO

#### Overall quality

Rating: TODO

TODO

### Quiz

#### Difficulty

Rating: TODO

TODO

#### Coverage of the lesson's core

Rating: TODO

TODO

#### Wording and possible misreadings

Rating: TODO

TODO

#### Writing quality

Rating: TODO

TODO

#### Alignment with the learning goal

Rating: TODO

TODO

### Feedback

#### Useful

Rating: TODO

TODO

#### Explains enough

Rating: TODO

TODO

#### Personalized to how I like things explained

Rating: TODO

TODO

### Tutor

#### Guardrails

Rating: TODO

TODO

#### Personalization

Rating: TODO

TODO

### Compared with the previous step

TODO

### What the next step should fix

TODO
