# Student Stress, Sleep & Screen Time Analysis

**Research question:** What factors appear to be associated with student stress?

## Hypotheses

1. Students who sleep less will have higher stress.
2. More screen time will be associated with higher stress.
3. A greater amount of exercise will reduce stress.

## Dataset Overview

- **Rows:** each row represents the data for a student with a particular student ID.
- **Columns:** `student_id`, `age`, `gender`, `sleep_hours`, `screen_time_hours`, `stress_level`, `study_hours`, `physical_activity`, `caffeine_intake`, `academic_pressure`
- **Target variable:** `stress_level` (Low / Medium / High)
- **Missing values:** none
- **Sample size:** 500 students

### Interesting observations

- The data from the first five rows seemed inconsistent with each other, and no clean relationships appeared at a glance — further investigation was required.
- It isn't stated whether "study time" also contributes to "screen time" (since in the modern day the two are often inseparable), or if the two metrics are completely independent. I assumed they're independent, considering that student S001 has 2.7 hours of screen time while also having 7.4 hours of study time, while S004 has 11.4 hours of screen time and 4.4 hours of study time. It would be nice if it were explicitly stated that the two were completely different.
- It doesn't seem like academic pressure causes an increase in hours spent studying. S003 reported high academic pressure but only 2.0 hours of studying, with 3.2 hours of screen time. Meanwhile S001 also reported high academic pressure but studied for 7.4 hours with only 2.7 hours of screen time.

## Numerical Variable Exploration

*(rounded to the nearest hundredth)*

### Age

| Mean | SD | Min | 25% | 50% | 75% | Max |
|---:|---:|---:|---:|---:|---:|---:|
| 21.53 | 2.24 | 18.00 | 20.00 | 22.00 | 23.00 | 25.00 |

**Notes:** given that the age range is 18–25, the students recorded in this dataset appear to be typical college undergrads and maybe some grad students.

### Sleep hours

| Mean | SD | Min | 25% | 50% | 75% | Max |
|---:|---:|---:|---:|---:|---:|---:|
| 6.55 | 1.44 | 4.00 | 5.30 | 6.50 | 7.80 | 9.00 |

**Notes:** the students are most certainly not sleeping enough, given that the mean is 6.55 hours. There's a good bit of variation — the lowest is 4 hours and the highest is 9. That's not a huge numerical range, but for a human being it's the difference between a caffeine-dependent zombie and a well-rested person.

### Screen time hours

| Mean | SD | Min | 25% | 50% | 75% | Max |
|---:|---:|---:|---:|---:|---:|---:|
| 7.11 | 2.91 | 2.00 | 4.57 | 7.30 | 9.50 | 12.00 |

**Notes:** the average screen time is 7.11 hours. For supposedly dedicated college students, that seems quite high, and a maximum of 12 hours is a lot. It's unclear whether the screen time measured here is completely distinct from hours spent studying, since the two can bleed into each other.

### Study hours

| Mean | SD | Min | 25% | 50% | 75% | Max |
|---:|---:|---:|---:|---:|---:|---:|
| 5.02 | 1.76 | 2.00 | 3.50 | 5.00 | 6.60 | 8.00 |

**Notes:** it's hard to say whether students are studying "enough." It would be worth further investigating whether STEM majors tend to study more than, say, Business majors — but the dataset has no major/field-of-study variable, so this can't be tested here. It's also unclear whether `study_hours` is strictly equivalent to "hours spent doing schoolwork," since something like a group project might not be classified as studying by every respondent, and it's unknown whether studying more corresponds to higher grades (there's no grades variable either).

### Caffeine intake

| Mean | SD | Min | 25% | 50% | 75% | Max |
|---:|---:|---:|---:|---:|---:|---:|
| 1.98 | 1.39 | 0.00 | 1.00 | 2.00 | 3.00 | 4.00 |

**Notes:** students don't seem to drink too much caffeine — an average of about 2 units is neither high nor low.

## Visualization of Numerical Variables

### Figure 1 — Distribution of Sleep Hours Among Students

![Distribution of sleep hours](figures/fig01_sleep_hist.png)

**What this graph shows:** the distribution of hours slept among students. The data is slightly left-skewed.

**What surprised me:** the results seem fairly uniform across the range, which is consistent with the mean of about 6.55 hours.

### Figure 2 — Distribution of Screen Time Hours Among Students

![Distribution of screen time hours](figures/fig02_screen_hist.png)

**What this graph shows:** the distribution of screen time hours among students. The data is slightly right-skewed.

**What surprised me:** the results seem fairly uniform, despite the slight right skew — there are about as many students with 2–3 hours of screen time as with 10–11 hours.

### Figure 3 — Distribution of Age Among Students

![Distribution of age](figures/fig03_age_hist.png)

**What this graph shows:** the distribution of age among students.

**What surprised me:** there's a noticeable concentration of students between ages 24 and 25. I'd assume students aged 22–25 are more likely to be graduate students, but the dataset doesn't say why there's a disproportionate number of 24–25 year olds specifically.

### Figure 4 — Distribution of Study Hours Among Students

![Distribution of study hours](figures/fig04_study_hist.png)

**What this graph shows:** the distribution of study hours among students. The data is remarkably uniform, with a slight right skew.

**What surprised me:** the amount of students who study 2–4 hours is about the same as those who study 6–8 hours, with only a slight dip in the 4–6 hour range.

### Figure 5 — Distribution of Caffeine Intake Among Students

![Distribution of caffeine intake](figures/fig05_caffeine_hist.png)

**What this graph shows:** the distribution of caffeine intake among students. The data is a bit right-skewed, but the average is about 2 — a sizeable group of students drinking 0.0–0.5 units brings the mean down toward a more neutral value.

**What surprised me:** there's actually a greater quantity of students who consume 2 or more units of caffeine than students who consume fewer than 2 units, yet the average caffeine intake is 1.98.

## Relationship Analysis

Two exploratory relationships were examined in detail, both expected to be negative:

### Screen Time vs. Sleep

**Prediction:** a negative relationship.

**Result:** there appears to be no relationship between screen time hours and sleep hours — the density of points in the scatterplot is uncannily even.

**Correlation coefficient (Pearson):** −0.020

![Screen time hours vs sleep hours](figures/fig06_screen_vs_sleep.png)

**Interpretation:** it would be expected that more screen time results in less sleep, but the scatterplot doesn't reflect this at all — there are no visible clusters or trends. This, along with the uniform distributions in Figures 1–5, raised the possibility that the dataset was synthetically generated. That said, this is a data-quality hypothesis, not a definitive conclusion (see Limitations).

### Caffeine Intake vs. Sleep Hours

**Prediction:** a negative relationship.

**Result:** there appears to be no relationship between caffeine intake and sleep hours.

**Correlation coefficient (Pearson):** 0.087

![Caffeine intake vs sleep hours](figures/fig07_caffeine_vs_sleep.png)

**Interpretation:** similar to the previous case, it's unexpected that caffeine intake shows no apparent relationship with sleep hours. The even data distribution reinforces the possibility that the dataset was synthetically generated, though again this remains an open question rather than a conclusion.

## Testing the Three Hypotheses Against Stress

The relationships above (screen time vs. sleep, caffeine vs. sleep) turned out to be flat. The more direct test, however, is each hypothesis against the actual target variable, `stress_level`. Because `stress_level` is ordinal (Low / Medium / High), group means plus **Spearman rank correlation** are used rather than Pearson correlation.

### Hypothesis 1 — Sleep → Stress: supported descriptively

| Stress level | Average sleep (hours) |
|---|---:|
| Low | 7.97 |
| Medium | 6.76 |
| High | 5.01 |

**Spearman ρ ≈ −0.603** (sleep hours vs. stress rank)

![Average sleep hours by stress level](figures/fig08_sleep_by_stress.png)

Average sleep drops steadily and substantially from the Low- to the High-stress group. This is the strongest relationship found anywhere in the dataset.

### Hypothesis 2 — Screen Time → Stress: supported descriptively

| Stress level | Average screen time (hours) |
|---|---:|
| Low | 3.33 |
| Medium | 7.09 |
| High | 9.39 |

**Spearman ρ ≈ +0.549** (screen time vs. stress rank)

![Average screen time by stress level](figures/fig09_screen_by_stress.png)

Average screen time rises steadily from Low- to High-stress students. Notably, screen time shows almost no relationship with sleep (see Relationship Analysis above) but a clear relationship with stress directly — suggesting screen time and sleep may affect stress through largely separate pathways, rather than screen time driving stress mainly by displacing sleep.

### Hypothesis 3 — Physical Activity → Stress: not supported

Physical activity is recorded only as a binary Yes/No, not a duration or intensity.

| Reports physical activity | % reporting High stress |
|---|---:|
| No | 21.1% |
| Yes | 19.7% |

![High-stress rate by physical activity](figures/fig10_highstress_by_activity.png)

The high-stress rate is nearly identical between the two groups. A gap this small isn't a meaningful difference, so this hypothesis is not supported by the data as collected. A duration- or frequency-based activity variable would be needed to test it properly.

## Follow-Up Questions

Several follow-up questions were raised while exploring the numerical distributions. Each is answered here directly against the data.

| Question | Answer |
|---|---|
| Do students sleeping <6 hours consume more caffeine? | **No** — average caffeine intake is nearly identical between the two groups (≈1.87 vs. ≈2.05 units). |
| Is more screen time associated with greater academic pressure? | **No clear relationship** — average screen time is broadly similar across Low, Medium, and High academic-pressure groups (6.8–7.3 hours). |
| Does high-stress frequency change with age? | **No clear pattern** — the percentage of students reporting High stress fluctuates across ages with no consistent upward or downward trend. |
| Do students who study more report less physical activity? | **No meaningful difference** — average study hours are close between students who do (≈4.93 hrs) and don't (≈5.10 hrs) report physical activity. |
| Does more caffeine correspond to more study time? | **Essentially no relationship** — Pearson correlation ≈ −0.035. |
| Does study time take away from sleep? | **Essentially no relationship** — Pearson correlation ≈ 0.047. |
| Do STEM students study more than Business students? | **Cannot be answered** — no major/field-of-study variable in the dataset. |
| Do students who study more earn higher grades? | **Cannot be answered** — no grades/GPA variable in the dataset. |
| Does sleep affect mental clarity or aptitude? | **Cannot be answered** — no cognitive-performance or test-score variable in the dataset. |

## Interpretation & Limitations

- Several numerical-variable distributions appeared unusually uniform.
- The scatterplots for screen time vs. sleep and caffeine intake vs. sleep showed little obvious structure, even though sleep and screen time each show a clear, monotonic relationship with `stress_level` directly. This suggests sleep and screen time act on stress along largely separate pathways, rather than screen time driving stress mainly by cutting into sleep.
- The original uniformity raised the possibility that the dataset was synthetically generated; the clean group-level patterns found when testing against `stress_level` are consistent with either a real, well-behaved dataset or a synthetic one, so this remains an open question rather than a settled conclusion.
- The meaning of some variables is not fully specified — for example, it's unclear whether screen time and study hours are meant to be completely independent measures.
- Physical activity is recorded as a binary Yes/No, which is too coarse to properly test the exercise–stress hypothesis; a duration or frequency measure would be needed.
- Several follow-up questions (major/field of study, grades, cognitive performance) cannot be answered at all, because the dataset does not include those variables.

These limitations mean that the observed relationships should be treated as exploratory rather than causal or definitive.

## Conclusion

This exploratory analysis examined distributions and relationships among several student lifestyle and academic variables, then tested each of the three original hypotheses directly against `stress_level`.

- **Sleep → stress:** supported. Average sleep falls from 7.97 hours (Low stress) to 6.76 hours (Medium) to 5.01 hours (High), with a Spearman ρ of about −0.603 — the strongest relationship in the dataset.
- **Screen time → stress:** supported. Average screen time rises from 3.33 hours (Low stress) to 7.09 hours (Medium) to 9.39 hours (High), with a Spearman ρ of about +0.549.
- **Physical activity → stress:** not supported. High-stress rates are nearly identical for students who do (19.7%) and don't (21.1%) report physical activity, though the binary Yes/No measure limits how much this test can show.

Of the eight follow-up questions raised during the initial exploration, two (caffeine vs. sleep duration, screen time vs. academic pressure) showed no meaningful relationship, two more (age vs. high-stress frequency, study hours vs. physical activity) showed no clear pattern, two (caffeine vs. study hours, study hours vs. sleep) showed essentially no correlation, and three (major vs. study hours, study hours vs. grades, sleep vs. cognitive performance) could not be answered because the dataset lacks the necessary variables.

Taken together, sleep and screen time both show clear, monotonic descriptive relationships with stress, while most of the other variables examined do not show meaningful relationships with each other. The analysis demonstrates a full exploratory data-analysis workflow: loading data, inspecting variables, calculating descriptive statistics, visualizing distributions, examining relationships, testing hypotheses against the target variable, answering follow-up questions, and critically evaluating limitations — while stopping short of any causal claims.
