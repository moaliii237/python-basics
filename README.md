# Python Fundamentals and an SDG Power BI Dashboard (Year 1, Block A)

This is the very first block of my Data Science and AI degree at Breda University of Applied Sciences (BUas), so it is also the first programming work I ever did. The repo has two parts. The first part is eight Jupyter notebooks where I learned and practiced Python from scratch: variables, conditionals, functions, loops, strings, lists, dictionaries, and tuples. The second part is the graded deliverable, an interactive Power BI dashboard that tracks United Nations Sustainable Development Goal (SDG) indicators around a research question I chose myself.

I am the sole author. I am keeping this in my portfolio on purpose, not because the code is advanced, but because it shows where I started and that I actually finished the exercises and the project.

## What is in here

- Eight Python practice notebooks (numbered 1 to 8), with the exercises worked through.
- A Power BI dashboard (`.pbix` files) on food prices and community health, built for the SDG brief.
- The supporting documents I had to hand in: a CRISP-DM write-up, a research question, a learning log, a worklog, and a self assessment rubric (in the `Deliverables` folder).
- Quiz screenshots and math practice from the weekly math and DataCamp work that ran alongside the block.

## The Python notebooks

These follow the course material, and I filled in the exercises. They are beginner level on purpose. A few things I actually wrote and understood:

- In `5. Strings.ipynb` I counted how many times a substring like `yo` appears in a sentence by lowercasing the text, splitting it into words, and looping with a counter. I also did the same letter-counting idea with `input()` so the user picks the word and the letter.
- In `6. Lists.ipynb` I wrote `avg_calculator(numbers)` using `sum()` and `len()`, a `chop(lst)` function that removes the first and last item but handles the edge case of a one-item list, and `unique_words(x)` that returns each distinct word in a sentence by checking `if words not in a` before appending.
- In `8. Tuples.ipynb` I worked with lists of `(name, score)` tuples. `total_scores` builds a dictionary that adds up each person's scores, `num_students` counts distinct names with a set comprehension, and `common_students` returns the names that appear in both course lists using set intersection (`&`).

### The F1-score function

The part of `3. Functions.ipynb` I am most happy I understood is the F1-score example. The notebook frames it as a sick / not-sick classifier, and the point was to learn functional decomposition.

First I followed `f1_calculator(ground_truth, model_predictions)`, which loops over the predictions and counts true positives, false positives, and false negatives, then computes:

- precision = TP / (TP + FP)
- recall = TP / (TP + FN)
- F1 = 2 * precision * recall / (precision + recall)

Then the same logic is split into three smaller functions that call each other: one counts TP, FP, FN; the next uses it to get precision and recall; the last uses that to get the F1 score. That was my first time seeing why you break one function into smaller ones instead of writing everything in one block. I did not know it yet, but precision, recall, and F1 came back in later blocks for evaluating real models, so learning it here paid off.

## The graded project: SDG dashboard

The DataLab deliverable was to pick a data-driven research question tied to the UN Sustainable Development Goals, gather the data, clean it, and build an interactive Power BI dashboard for it.

My research question was: what is the correlation between increasing food prices and the overall health security of the community? I picked it because I am from Iran and I lived through high inflation, and I wanted to check whether the same pattern of rising prices and worse health shows up in other countries too. It maps to two SDG indicators, SDG 1 No Poverty and SDG 2 Zero Hunger, because in my reading inflation pushes people into poverty, and poverty leads to malnutrition.

### My approach

I followed the CRISP-DM steps for this (business understanding, data understanding, data preparation, modeling, evaluation, deployment), which are written up in the document in `Deliverables`.

- Data gathering. I pulled data from a few public sources: Statista, Our World in Data, and the WHO. The variables were things like worldwide inflation and average inflation per continent, a food price index over 10 years, total deaths from malnutrition, the share of people who cannot afford a healthy diet over 10 years, and life expectancy by country over 10 years.
- Cleaning. Because the data came from different sources it did not line up, so this was the hard part. In Power Query I promoted the first row to headers, removed columns I did not need, removed rows with bad or inconsistent values, sorted everything by year (most of my comparisons are year on year), checked spelling so the same category matched across tables, and built relationships between the tables.
- New features. Some columns were on very different scales, for example one was 0 to 100 and another was in the millions. I normalized those to a common 0 to 100 scale so I could actually compare them on the same chart.
- Analysis and visuals. There was no machine learning here. It is descriptive analysis: correlation between inflation, food prices, and health outcomes, plus averages and medians across years and regions. I used line charts for the time series, stacked column charts to compare regions, and pie charts for distribution summaries.

### What I found and where it falls short

My main takeaway was that the SDG indicators are connected, you cannot fix only one, and that there is a lot of inequality between countries. The dashboard does show the link I was looking for between inflation, poverty, and access to a healthy diet.

Being honest about the limits: the research question was new to me and I had to stitch together data from several sources, so the comparisons are rough rather than statistically proven. There is no real correlation coefficient or statistical test behind it, it is visual correlation. If I redid it today I would add filters for things like age or income level, use more country-level detail, and try predictive models instead of only descriptive charts.

## Tech stack

- Python 3 in Jupyter notebooks for the programming exercises. Standard library only, plus `collections.Counter` in one tuples exercise.
- Power BI Desktop for the dashboard, with Power Query for cleaning and shaping the data.
- Data from Statista, Our World in Data, and the WHO.

## How to run

The Python notebooks:

```
pip install jupyter
jupyter notebook
```

Then open any of the numbered `.ipynb` files and run the cells top to bottom. They do not need any data files, the examples are defined inside the notebooks.

The dashboard:

- Open `SDG_IndicatorsDashboard_Mohammadali.pbix` (or the copies in `Deliverables`) in Power BI Desktop on Windows. There is no free viewer for `.pbix` other than Power BI Desktop.
- The raw source data is not bundled in this repo. The cleaned data lives inside the `.pbix` file itself, so the visuals open without extra downloads, but you cannot fully reproduce the cleaning steps without the original source files.
- `power bi (not ready yet).pbix` is an earlier work-in-progress version. The finished one is `SDG_IndicatorsDashboard_Mohammadali.pbix`.

## Repo layout

- `1. Variables.ipynb` ... `8. Tuples.ipynb` the eight Python practice notebooks.
- `SDG_IndicatorsDashboard_Mohammadali.pbix` the final dashboard.
- `DS1_Dashboard_Mohammadali.pbix`, `power bi (not ready yet).pbix` dashboard versions.
- `Deliverables/` the graded hand-ins (CRISP-DM write-up, learning log, worklog, self assessment).
- `Monday/`, `Tuesday/`, `Wednesday/` weekly evidence for the math, research, and DataLab tasks.
- `*.png`, `*.pdf` quiz results and practice evidence collected during the block.

## Note

This is first-block, beginner work. I am not presenting it as production code. I keep it here as the honest starting point of my degree and as proof that I showed up, did the exercises, and shipped the dashboard.
