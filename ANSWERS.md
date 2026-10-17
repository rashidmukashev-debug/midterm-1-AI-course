# Midterm 1: answers

GitHub username: `rashidmukashev-debug`  
Session code: `maple-66`  
Fingerprint: `21df940e`

## AI-use declaration

I used ChatGPT to help me understand the exam instructions, explain the formulas, and check my calculations. I used Google Colab to run the provided data generator and obtain my synthetic dataset. I reviewed the results and used AI explanations to improve my understanding of retrieval metrics, confidence intervals, token costs, and document-processing risks. I am responsible for verifying my final answers and explaining my reasoning during the oral check.


## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

| config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|---|---|---|---|
| A |0.65|0.7333 |0.8500 |0.7245|
| B |0.4667| 0.6667 | 0.7500 | 0.5609|

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---|---|---|
| A, k=3 | 0.7333 | 0.6099 | 0.8287 |
| A, k=5 | 0.8500 | 0.7389 | 0.9190 |
| B, k=3 | 0.6667 | 0.5406 | 0.7727 |
| B, k=5 | 0.7500 | 0.6277 | 0.8422 |

### 1c. Annual model cost in USD

| candidate | annual cost |
|---|---|
| A, k=3 | 39955.94 |
| A, k=5 | 53872.36 |
| B, k=3 | 24900.29 |
| B, k=5 | 28779.61 |

### 1d. Decision (at most 150 words)

Chosen candidate:
Chosen candidate: B, k=5

I choose B with k=5 because its annual cost is 28779.61 USD, which is within the 34400 USD budget. Its overall recall is 0.75, compared with 0.6667 for B with k=3. Candidate A performs better at the same k, but both A options exceed the budget. The 95% Wilson interval for B at k=5 is 0.6277–0.8422, so the estimate is still uncertain. Recall by language is 0.85 for EN, 0.75 for RU, and 0.65 for KK. Kazakh has the weakest retrieval performance and needs further evaluation.

### 1e. Next measurement (at most 60 words)
Evaluate both configurations on a larger, independently sampled test set, especially for Kazakh questions. Measure recall by language, query difficulty, and document type, and compare the results with production logs. This will reduce uncertainty and help determine whether the observed performance differences are reliable.


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
