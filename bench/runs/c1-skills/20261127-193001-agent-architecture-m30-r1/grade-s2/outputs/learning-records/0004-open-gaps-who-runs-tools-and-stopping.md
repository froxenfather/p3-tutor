# Open: who runs the tools, why loops must be stopped, and what the model chooses tools from

Riley picked the right output for a tool call (q2) but then said the model runs each tool itself (M4, q4), and expected a stuck agent to succeed if left running (M6, q3).
Riley also named only the tool's name as the basis for choosing a tool (q6), leaving out its description and parameters.

**Evidence:** quiz 0001, submission s2, items q2, q3, q4 and q6.

**Implications:** Correct M4 and M6 before building on the loop, and re-check them with new questions; the q2 answer alone does not show that M4 is resolved.
Tool descriptions need practice before Riley writes one for the makerspace assistant.
