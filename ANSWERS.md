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
| H | 0.9056 | RU, degraded | 0.8667 | 0.7032 | 0.9469 | 14404.73 |
| L | 0.8444 | KK, degraded | 0.6667 | 0.4878 | 0.8077 | 21600 |

Personal-data pages per year sent abroad under H: 689850

### 2b. Memo (at most 300 words)

Internal memo

Topic: Choosing a pipeline for scan recognition and compliance with the law on PD1. 
To: Head of the Operations Department
From: AI Analytics

Overall accuracy indicators hide problems on complex scans. Pipeline H showed the worst accuracy in the RU, degraded cell - 0.8667 (95% Wilson interval: [0.7032, 0.9469]). Pipeline L did the worst with KK, degraded - 0.6667 (95% interval: [0.4878, 0.8077]). Scans from these categories are highly likely to require manual verification.

The situation with personal data based on the Law of Kazakhstan on Personal Data (No. 94-B) is as follows: about 689,850 pages per year contain full name and IIN. 

Where does the scan go? With H, the data is sent abroad to a foreign data center, and with L, it remains inside the bank in the Republic of Kazakhstan.  
Who keeps it? With H, storage is in a third-party foreign company, and with L, only in our bank.   
How long? For H, this is unknown without an audit of the company, and for L, the deadline is determined by the bank's regulations.  

To summarize, sending IIN abroad with H creates serious legal risks under the Law of the Republic of Kazakhstan "On Personal Data". 

Verifiable security measures: If we use H, you need a local script to remove the IIN and full name from the image before sending it. At the same time, for L, there is no such risk initially.

I recommend Pipeline L. Although it will be more expensive ($21,600 per year instead of $14,404 for H), it guarantees the localization of data in the Republic of Kazakhstan. 
Residual risk: Lower L accuracy on damaged scans. We will smooth it out by automatically sending scans with low confidence of the model for manual verification to the operators.

## Part 3: Explain your own numbers

### Q1

Number: 2.34
Why (at most 40 words): Since tokens in English for output are 6 times more expensive than tokens for input (2 for input and 12 for output as it said in Model M). Since in the Kazakh language, if we compare with English, slightly fewer tokens are used for output than for input, we see decrease in the total cost of tokens.

### Q2

Number: 368
Why (at most 40 words): It will be retrived, as the offer ends before the limit of 512 tokens expires, because the offer starts on the 368 token and has a length less than 20. Since it fits within the limit, there will be no errors.

### Q3

Number: 59.8%
Why (at most 40 words): The difference is that top-p cuts off the unlikely tail of tokens based on cumulative probability, while lowering the temperature changes the scale of all logits, that is, it makes the distribution without strictly zeroing out the lower tokens.

### Q4

Number: 24.2%
Why (at most 40 words): Since logical tasks are not based on single training facts that can be memorized, we exclude the sequences of multiplication and arithmetic. And also system prompts will not be able to prevent the hallucination of missing facts.

### Q5

Number: 33800
Why (at most 40 words): The first message is been paid 25 times. Promt caching reduces the cost of repeating historical tokens by up to 90% over these 25 times, turning the quadratic cumulative scaling of the context into an almost linear cost.
