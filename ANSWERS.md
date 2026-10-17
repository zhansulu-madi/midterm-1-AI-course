# Midterm 1: answers

GitHub username: zhansulu-madi
Session code: ember-92
Fingerprint: 2b97b42d

> Fill in the three lines above from `my_data/DATA.md`. Do not rename headings or table columns: a script reads the numbers.
> Write only in the empty cells and lines. Percentages as 0.78 or 78 %, money as plain numbers.

## AI-use declaration

(About half a page: which assistants or tools you used and for what. If you used none, say so.)

## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

| config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|---|---|---|---|
| A | 0.5167 | 0.6 | 0.65 | 0.5694 |
| B | 0.2333 | 0.55 | 0.6 | 0.4005 |

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---|---|---|
| A, k=3 | 0.6 | 0.4737 | 0.7143 |
| A, k=5 | 0.65 | 0.5236 | 0.7583 |
| B, k=3 | 0.55 | 0.4249 | 0.6691 |
| B, k=5 | 0.6 | 0.4737 | 0.7143 |

### 1c. Annual model cost in USD

| candidate | annual cost |
|---|---|
| A, k=3 | 18467.6 |
| A, k=5 | 23955.07 |
| B, k=3 | 12814.88 |
| B, k=5 | 14533.88 |

### 1d. Decision (at most 150 words)

Chosen candidate: (B, 5)

(Decision, using your intervals and the budget. Give the recall of your choice for EN, RU and KK separately.)

Since our annual budget for this service is 16500 dollars, we cannot choose (A, 3) or (A, 5), because they exceed the budget. Now we only have models (B, 3) and (B, 5) that fit within the annual budget. Since the recall and 95% Wilson interval are higher for (B, 5), I would choose this model. 

Recall for (B, 5):

EN: 0.5
RU: 0.55
KK: 0.75

Here EN is worst

### 1e. Next measurement (at most 60 words)

It is better to add a check of the actual correctness of the answers, as models can often hallucinate. Perhaps the model is looking for a suitable fragment, but does not really give the right answer, so for reliability, it is better to evaluate the quality of generation.

## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---|---|---|---|---|---|
| H | | | | | | |
| L | | | | | | |

Personal-data pages per year sent abroad under H:

### 2b. Memo (at most 300 words)

## Part 3: Explain your own numbers

### Q1

Number:
Why (at most 40 words):

### Q2

Number:
Why (at most 40 words):

### Q3

Number:
Why (at most 40 words):

### Q4

Number:
Why (at most 40 words):

### Q5

Number:
Why (at most 40 words):
