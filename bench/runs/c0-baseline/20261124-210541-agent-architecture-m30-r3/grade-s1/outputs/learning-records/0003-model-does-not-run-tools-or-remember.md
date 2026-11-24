# The model requests tools but does not run them, and it has no memory on its own (misconception open)

In quiz 0001 (submission s1), Riley believed the model itself opens the booking system and runs the tools inside one call (M4), and that it remembers earlier sessions on its own (M3).
Riley does know that the model chooses a tool from the descriptions it is given, and that an agent needs a stopping condition.
Next lessons should show who does what, program versus model, and why each tool result means another model call, before building memory on top.

**Evidence:** quiz 0001, submission s1, items q2, q4 (M4) and q6 (M3); correct on q1 and q3. Submission s2 is a later attempt and has not been graded yet.

**Implications:** Context and memory lessons should start by showing that the model sees only the text it is sent each call. Revisit M4 with a model/program timeline.
