# Open misconception: the model runs the tools itself (M4), and remembers on its own (M3)

In quiz 0001 (submission s1) Riley wrote that the model "runs the 3 tools itself" in a single call (q4, q2), and that it remembers which tool it picked in earlier sessions (q6). Riley does know the loop, the need for a stopping condition, and that the model chooses tools from their descriptions.
Before building on the loop, teach that the model only writes text (a tool request or an answer), the program runs the tool, and each result triggers a new model call. Teach too that nothing carries over between sessions unless the program saves it and sends it back, which leads into context and memory.

**Evidence:** quiz 0001, submission s1, items q1 and q3 correct; q2 and q4 wrong (M4); q6 partial (M3).
