# Testing Evidence

| Test | Result |
|---|---|
| Source data loaded | PASS – 500 rows × 9 columns |
| Missing-value check | PASS – 0 missing cells in source |
| Unique customer IDs after cleaning | PASS – 500 unique IDs |
| Clustering algorithms compared | PASS – K-Means, Agglomerative, DBSCAN |
| Selected K-Means segments | PASS – 4 segments |
| Segment prediction models | PASS – 4 separate Random Forest model pipelines |
| Evaluation results generated | PASS – 4 segment rows in model_evaluation_results.csv |
| Visual outputs | PASS – 5 charts generated |

Model evaluation is a holdout estimate and may be unstable for segments with few churn cases. Review each segment's customer count and class counts alongside the scores.