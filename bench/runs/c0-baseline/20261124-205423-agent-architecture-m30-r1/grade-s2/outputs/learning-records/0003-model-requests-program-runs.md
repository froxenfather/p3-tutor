# Open: Riley still says the model runs the tools, and has not yet seen why a loop needs a step limit

On the second attempt at quiz 0001 (s2), Riley got the loop (q1), the tool request (q2) and what happens to a result (q5) right, but still wrote that "the model can only run one tool itself" (M4) while counting 4 model calls correctly.
Riley also picked "it will eventually fix the bug" over a step limit (M6), and named only the tool's name as how the model chooses it (partial).
Lessons on context and tool descriptions should keep the split explicit: the model writes a request, and the program runs the tool and makes each new model call.

**Evidence:** quiz 0001, submission s2, items q3, q4, q6. Submission s1 had M4 on q2 and q4, so M4 has improved but is not gone.

**Implications:** Do not assume M4 is fixed. A later retrieval check should ask who runs the tool, and tool-description writing (success criterion 2 in the mission) is the natural place to correct q6.
