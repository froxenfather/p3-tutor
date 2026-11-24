# Pre-registration: the length study

This file is for 598E students, for whom the length study is the required rider, and for 498E students who chose it as their stretch.
Everyone else can ignore it or delete it.

A pre-registration is a claim you write down, with the analysis that will judge it, before you can see the answer.
Its value is that the claim can be wrong in a way anyone can check, and that you cannot bend it afterwards to fit the numbers.
A clear "no difference as large as the one I cared about" scores as well as a confirmation, so you have no reason to hedge.

**Git history is how I will know the order.**
Fill in sections 1 to 4 and commit this file before the first of the eight length-study runs.
`uv run p3 check --final` reads `git log` and confirms that the commit came first.
After that commit, do not edit sections 1 to 4.
If something must change, add a dated entry in section 6 and leave the original as it was.
Section 5 you write at the end, after the runs and the comparisons.

Each section that needs your words ends with a marker line.
Replace that line with your answer; `uv run p3 check --final` fails while one is left.

The design is fixed: two configs, two lengths, two teach-only runs in each cell, on the shared topic.

| | 10 minutes | 60 minutes |
|---|---|---|
| `c1-skills` | 2 runs | 2 runs |
| `final` | 2 runs | 2 runs |

```
uv run p3 bench --config c1-skills --only teach --minutes 10 --repeats 2
uv run p3 bench --config c1-skills --only teach --minutes 60 --repeats 2
uv run p3 bench --config final --only teach --minutes 10 --repeats 2
uv run p3 bench --config final --only teach --minutes 60 --repeats 2
```

After the runs, one blind comparison per length, each pairing only the study's teach-only runs at that length, two pairs each:

```
uv run p3 compare c1-skills final --job teach --teach-only --minutes 10
uv run p3 compare c1-skills final --job teach --teach-only --minutes 60
```

The 30-minute point comes from the ladder's full runs of `c1-skills` and `final`, so it needs no runs of its own.
These two sessions are your second blind comparison of the project, beside `c0-baseline` against `final`, and you make no other on top.
The numbers for every cell come from one command:

```
uv run p3 report --configs c1-skills,final --teach-only
```

---

## 1. Hypothesis


As the requested lesson length increases from 10 to 60 minutes, I expect c1-skills to experience a greater decline in factual correctness than final, because a single agent must maintain context, instructional structure, and factual accuracy throughout a substantially longer generation process.

---


## 2. The Smallest Difference That Matters

My primary measure will be `teach_facts_correct`, with a
minimum meaningful difference of Δ = 0.30 (30 percentage
points) between the configurations' declines.

With approximately 6-10 evaluated facts per lesson, this
represents roughly two to three facts. A smaller threshold
could be difficult to distinguish from normal run-to-run
variation with only two runs per cell.

Missing or incorrectly teaching several required facts
could substantially impact a learner's understanding,
making this a meaningful difference.

Although previous baseline runs scored near 1.00, I will
retain factual correctness as my primary measure. A lack
of meaningful degradation is still a valid experimental
outcome.

---


## 3. The Measures

### A. Primary Measure: Factual Correctness

My primary measure will be `teach_facts_correct`. For each
configuration and requested lesson length, I will calculate
the mean and range of the two independent runs.

- Mean: (Run 1 + Run 2) / 2
- Range: [Minimum score, Maximum score]

The mean represents the average factual correctness of the
two runs, while the range provides an indication of
run-to-run consistency.

**Example (hypothetical data):**

| Configuration | 10-Min Mean | 60-Min Mean | Decline |
|---|---|---|---|
| c1-skills | 1.00 | 0.60 | 0.40 |
| final | 1.00 | 0.95 | 0.05 |

In this example, the difference in decline is 0.35,
exceeding my minimum meaningful difference of 0.30.


These values are hypothetical and are only intended to
demonstrate how the results will be reported.

### B. Blind Comparison

I will evaluate the lessons without knowing which configuration
generated them. Comparisons will be conducted separately for
each requested lesson length, with one blind evaluation session
per length.

I will never compare a 10-minute lesson against a 60-minute
lesson.

For each length, I will calculate:

**Final preference share:**

$$
\text{Final Preference Share} =
\frac{\text{Final Wins}}
{\text{Final Wins}+\text{C1-Skills Wins}}
$$

Ties will be excluded from the denominator but will still
be reported. If both comparisons result in ties, the
preference share will be reported as undefined.

**Example (hypothetical data):**

| Length | Final Wins | C1-Skills Wins | Ties | Final Share |
|---|---|---|---|---|
| 10 min | 1 | 1 | 0 | 50% |
| 60 min | 2 | 0 | 0 | 100% |

Because there are only two blind comparisons per length,
these results will be treated as descriptive evidence rather
than statistically significant conclusions.

### C. Length Accuracy

I will use `teach_length_ratio` to determine how closely each
generated lesson matches its requested duration.

Estimated lesson length will be calculated using a reading
speed of 150 words per minute.

$$
\text{Estimated Minutes} = \frac{\text{Word Count}}{150}
$$

Length accuracy will then be calculated as:

$$
\text{Length Ratio} =
\frac{\text{Estimated Minutes}}{\text{Requested Minutes}}
$$

A length ratio of 1.00 indicates that the estimated lesson
duration exactly matches the requested duration.

I will consider a length ratio between 0.80 and 1.20,
inclusive, acceptable.

| Requested Length | Minimum Length | Maximum Length |
|---|---|---|
| 10 minutes | 8 minutes | 12 minutes |
| 60 minutes | 48 minutes | 72 minutes |

For example, a 60-minute lesson containing 7,500 words
would have an estimated duration of 50 minutes and a
length ratio of 0.833, falling within the acceptable range.

I will report the mean and range of the length ratios for
each cell.

If either run within a cell falls outside the acceptable
range, I will:

- Flag the cell as having a length accuracy issue.
- Report all results without excluding either run.
- Acknowledge that comparisons involving that cell may
  be confounded by unequal lesson lengths.

This is important because a configuration generating
significantly shorter lessons may appear to maintain higher
quality simply because it is completing less work.

Additionally, this length estimate does not account for
the time a learner spends completing exercises, answering
reinforcement questions, or practicing technical concepts.

### D. Cost Against Length

I will evaluate computational efficiency by measuring the
total number of tokens consumed per estimated minute of
generated lesson content.

I will use estimated lesson minutes rather than requested
minutes to avoid rewarding configurations that generate
shorter lessons than requested.

$$
\text{Tokens per Minute} =
\frac{\text{Total Tokens Consumed}}
{\text{Estimated Lesson Minutes}}
$$

Total token consumption will include input and output
tokens across all relevant agent calls, where available.

I will calculate tokens per minute independently for each
run and report the mean and range for each cell.

**Example (hypothetical data):**

| Configuration | Estimated Length | Total Tokens | Tokens/Min |
|---|---|---|---|
| c1-skills | 10 min | 3,000 | 300 |
| c1-skills | 60 min | 18,000 | 300 |
| final | 10 min | 5,000 | 500 |
| final | 60 min | 48,000 | 800 |

I will also calculate the additional normalized token
overhead introduced by the final configuration.

$$
\text{Overhead} =
\text{Final Tokens/Min} - \text{C1-Skills Tokens/Min}
$$

Using the hypothetical values above:

| Lesson Length | Additional Overhead |
|---|---|
| 10 minutes | 200 tokens/min |
| 60 minutes | 500 tokens/min |

I will compare the normalized overhead at both requested
lesson lengths to determine how the final configuration
scales.

- Increasing overhead: Additional token cost grows faster
  than estimated lesson length.
- Constant overhead: Additional token cost grows
  proportionally with estimated lesson length.
- Decreasing overhead: Additional token cost grows more
  slowly than estimated lesson length.

Ultimately, I want to determine whether the additional
computational cost of the final configuration is justified
by its ability to maintain teaching quality as lesson
length increases.


---

## 4. The analysis and What Each Result Will Mean

### A. Measuring Quality Degradation
I will calculate the decline in mean factual correctness
from 10 to 60 minutes for each configuration.

$$
D = \text{Mean}_{10} - \text{Mean}_{60}
$$

I will then calculate the difference between their declines.

$$
D_{diff} = D_{c1} - D_{final}
$$

**Example (hypothetical data):**

| Configuration | 10-Min Mean | 60-Min Mean | Decline |
|---|---|---|---|
| c1-skills | 1.00 | 0.60 | 0.40 |
| final | 1.00 | 0.95 | 0.05 |

In this example, the difference in decline is 0.35,
exceeding my minimum meaningful difference of 0.30.


### B. Decision Rule

I will retain the original decision rule, with Δ = 0.30
(30 percentage points).


| Result | Conclusion |
|---|---|
| Difference ≥ Δ in the predicted direction, with non-overlapping 60-minute ranges | Supported |
| Difference ≥ Δ in the opposite direction, with non-overlapping 60-minute ranges | Contradicted |
| Absolute difference < Δ | No difference as large as Δ observed |
| Anything else | Inconclusive |

I will report the means and ranges for every cell.
Secondary measures will provide additional context but
will not override this decision rule.

### C. Threats to Validity

- **Blinding failures (Lecture 22):** Differences in writing
  style or structure may reveal which configuration produced
  a lesson. I will report my could-tell share at each length.

- **Judge bias (Lecture 24):** The automated judge may favor
  longer or more detailed responses regardless of their
  actual teaching quality.

- **Length estimation:** The estimate of 150 words per minute
  does not account for exercises, coding, mathematical
  problems, or reinforcement questions.

- **Limited sample size:** Two runs per cell make it difficult
  to distinguish genuine performance differences from
  random variation.

- **Ceiling effect:** Previous baseline runs achieved near
  perfect factual correctness. Both configurations may
  perform near the maximum score, making smaller quality
  differences difficult to detect.

- **Fact coverage:** Shorter lessons may omit required facts
  due to length constraints rather than factual inaccuracies.
  Longer lessons may therefore score higher simply because
  they cover more of the required material.


### D. Greatest Concern

My greatest concern is length estimation. If one
configuration produces significantly shorter lessons,
it may maintain higher factual correctness simply because
it is completing less work.

Additionally, hands-on exercises may require substantial
learning time without contributing much to the word count.

I will therefore qualify my conclusions if either
configuration fails to meet the established length tolerance.


---

## 5. Outcome (write this after the fact)

What did each measure show, cell by cell?
Which row of the table in section 4 is it?
Did the lessons meet their lengths, and what did the cost per minute of lesson do?
What would you do next, and what would you want a reader to take from this?

TODO: your outcome.

---

## 6. Amendments

Dated entries only, one per change, each saying what changed and why.
Leave this section as it is if nothing changed.
