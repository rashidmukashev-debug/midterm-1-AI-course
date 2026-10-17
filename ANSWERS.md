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
| H | 0.8833 | KK, degraded | 0.7333 | 0.5555 | 0.8582 | 36299.25 |
| L | 0.8222 | KK, degraded | 0.6000 | 0.4232 | 0.7541 | 10800 |

Personal-data pages per year sent abroad under H: 219000

### 2b. Memo (at most 300 words)
I recommend pipeline L as the default because it processes documents within Kazakhstan, costs only 10,800 USD per year, and avoids sending personal data abroad. Pipeline H has higher overall accuracy (88.33% versus 82.22%), but its estimated annual cost is 36,299.25 USD, exceeding the 34,400 USD budget by 1,899.25 USD.

The weakest condition for both pipelines is degraded Kazakh-language scans. H achieves 73.33% accuracy in this group, while L achieves 60%. These results show that scan quality and language affect reliability, so the system should flag uncertain extractions for human review rather than silently accepting them.

At 7,500 pages per day, approximately 219,000 pages containing personal names and ИИН would be sent abroad annually under H. This creates a significant data-protection concern. Before deploying either pipeline, I would test it on a larger, representative dataset, monitor accuracy separately by language and scan quality, and manually verify high-risk fields such as ИИН and invoice totals. L is the more practical default under the current budget and privacy constraints. H could be reconsidered if its accuracy advantage proves necessary and appropriate safeguards and funding are available.

## Part 3: Explain your own numbers

### Q1
Number: The annual cost difference between the two configurations.
Why: The annual cost depends on the retrieval configuration and the number of documents processed. A more expensive configuration should be chosen only if its improvement in retrieval quality justifies the additional cost.

### Q2
Number: Recall@3 = 0.7333 and Recall@5 = 0.8500 for configuration A.
Why: Increasing k from 3 to 5 improves recall because the system considers more retrieved results. However, retrieving more documents can increase processing costs.

### Q3
Number: Recall for Kazakh (KK) = 0.65.
Why: Kazakh has the weakest retrieval performance among the three languages. This suggests that the system may need better Kazakh-language data and additional evaluation.

### Q4
Number: Pipeline L accuracy on degraded Kazakh scans = 0.6000.
Why: Poor scan quality can make text harder to recognize, especially in Kazakh. Low-confidence fields should be flagged for human review instead of being accepted automatically.


### Q5
Number: 15.90
Why: By this criterion, the model is over-trained relative to Chinchilla's compute-optimal ratio. Chinchilla showed that models such as GPT-3 were under-trained: they used too many parameters relative to their training data and could perform better with more tokens and fewer parameters at the same compute budget.
Number:
Why (at most 40 words):
