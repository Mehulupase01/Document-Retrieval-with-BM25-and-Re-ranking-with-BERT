# Document Retrieval with BM25 and Re-ranking with BERT
 This project uses BM25 for document retrieval on the MS MARCO passage ranking task and compares its performance with BERT-based re-ranking. The project demonstrates how BM25 serves as a first-stage ranker before re-ranking with more advanced models like BERT, evaluating the results using MAP, Recall@1000, and NDCG@10 metrics

# Document Retrieval with BM25 and Re-ranking with BERT

This project demonstrates the use of the **BM25** model for document retrieval on the **MS MARCO** passage ranking task and compares it with the performance of **BERT-based re-ranking**. BM25 serves as the first-stage ranker, with the re-ranking step applying BERT to improve the results. The project evaluates these models using standard Information Retrieval (IR) metrics: **MAP**, **Recall@1000**, and **NDCG@10**.

## Overview

### Task 1: BM25 Retrieval with Pyserini
- Implement document retrieval using **BM25** and evaluate it using the **pyserini** library. The notebook processes queries and documents from the **MS MARCO** passage dataset, ranks the documents based on BM25, and produces a ranked list.
  
- The output is evaluated using **trec_eval** for performance metrics:
  - **MAP** (Mean Average Precision)
  - **Recall@1000**
  - **NDCG@10** (Normalized Discounted Cumulative Gain)

### Task 2: Re-ranking with BERT
- Re-rank the documents using a pre-built **BERT-based model** provided for this task. The output of the BERT re-ranker is evaluated similarly using the same metrics.

### Code Structure:

1. **`bm25_pyserini_msmarco_passage_demo_(Assignment).ipynb`**: A Jupyter notebook that implements document retrieval using BM25 with **Pyserini** and compares its performance with BERT re-ranking.

2. **Evaluation**: The notebook uses **pytrec_eval** to evaluate the retrieval performance of BM25 and BERT based on the **qrels file** (which provides relevance judgments for the queries) and **ranking files**.

### BM25 and BERT Performance Metrics:

| Metric                 | BM25            | BERT Re-ranking |
|------------------------|-----------------|-----------------|
| **MAP**                | 0.228           | 0.399           |
| **Recall@1000**        | 0.192           | 0.346           |
| **NDCG@10**            | 0.237           | 0.399           |

### Query and Document Format:

- **Ranking file**: A TREC-formatted file containing query-id, document-id, rank, and relevance score.
  
  Example:

    ```
    1102330 Q0 7867446 1 20.756399 Anserini 1102330 Q0 3368049 2 19.465799 Anserini

    ```

- **Qrels file**: Contains relevance judgments for queries and documents.

Example:

  ```
  1 0 AP880212-0161 0 1 0 AP880216-0139 1

  ```

### Output:

- **BM25** output: Ranked list of documents with corresponding relevance scores, evaluated using MAP, Recall@1000, and NDCG@10.
- **BERT** output: Similar output with re-ranked results, showcasing improvements in ranking quality.

### Results & Discussion:

- **BM25** provides a fast and effective first-stage ranking, but its performance can be significantly improved with a second-stage **BERT re-ranking**.
- **BERT** significantly improves ranking quality, as shown by the higher MAP, Recall@1000, and NDCG@10 metrics.

### Conclusion:

This project showcases the application of **BM25** for document retrieval and its improvement through **BERT-based re-ranking**. The combination of BM25 and BERT highlights the strengths of traditional IR models and deep learning models working together to improve search performance.

## References:

1. **Pyserini Library**: http://pyserini.io/
2. **MS MARCO**: http://www.msmarco.org/
3. **BERT: Devlin et al. (2018)**: BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding.
4. **TREC Evaluation**: https://github.com/cvangysel/pytrec_eval
