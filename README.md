# UniMem_Table

About adding more downstream evaluation tasks

Due to time limitations, our experiments were performed on tinyLlama, setting the context length to 512 and memory size of Unimix to 10k tokens, while other hyperparameters were reduced proportionally compared to those specified in the paper. We initiated by fine-tuning the model with a 0.1 billion (0.1B) dataset, followed by supervised fine-tuning using 12k instances from the LongAlpaca dataset. Both the fine-tuning and SFT (Supervised Fine-Tuning) experiments were of moderate scope, which potentially impacted the models' performance on downstream tasks but still demonstrated the correct trends. During the inference stage, the input length was restricted to a maximum of 15k tokens, with any excess data being truncated from the middle.

**Table 1: Comparative Performance on Longbench**

| Model          | NarrativeQA | Qasper | MultiFieldQA\_EN | HotpotQA | 2WikiMQA | Musique | Gov Report | QMSum | Multi News | TREC | TriviaQA | SAMSum | LCC | RepoBench-P | Avg  |
|----------------|-------------|--------|------------------|----------|----------|---------|------------|-------|------------|------|----------|--------|-----|-------------|------|
| Vanilla        | 5.2         | 8.1    | 19.45            | 6.19     | 16.6     | 3.58    | 12.47      | 19    | 10.06      | 11   | 11.9     | 0.42   | 25.34 | 32.53       | 12.99|
| Longformer     | 4.5         | 8.01   | 19.52            | 6.11     | 15.74    | 3.80    | 9.68       | 19.45 | 11.28      | 16.5 | 14.54    | 0.17   | 24.56 | 31.55       | 13.04|
| MemTrans       | 5.88        | 8.69   | 19.18            | 5.55     | 14.12    | 3.49    | 10.84      | 18.72 | 13.14      | 12   | 11.82    | 0      | 26.48 | 30.78       | 12.91|
| Transformer-XL | 4.54        | 8.11   | 18.98            | 5.15     | 14.33    | 3.23    | 13.33      | 19.60 | 13.57      | 13   | 17.79    | 0      | 24.75 | 32.38       | 13.48|
| RMT            | 4.36        | 7.58   | 18.59            | 5.90     | 13.75    | 3.78    | 11.60      | 19.54 | 11.08      | 13   | 12.33    | 0      | 28.40 | 32.02       | 13.00|
| UniMix (Ours)  | 6.19        | 8.26   | 19.27            | 6.82     | 14.45    | 3.77    | 16.00      | 20.02 | 12.09      | 20   | 12.24    | 3.01   | 28.37 | 33.65       | 14.58|

---

**Table 2: Performance on Needles in the Haystack across different text length**

| Model           | 4k   | 8k   | 16k  | 32k  | Avg  |
|-----------------|------|------|------|------|------|
| Vanilla         | 0.05 | 0.04 | 0.03 | 0    | 0.03 |
| Longformer      | 0.07 | 0.03 | 0.03 | 0    | 0.03 |
| MemTrans        | 0.05 | 0    | 0    | 0    | 0.01 |
| Transformer-XL  | 0.20 | 0.04 | 0.03 | 0.01 | 0.07 |
| RMT             | 0.04 | 0.03 | 0.03 | 0.01 | 0.03 |
| UniMix (Ours)   | 0.37 | 0.39 | 0.09 | 0.04 | 0.22 |

