# Customer Segment Profiles

## Method
K-Means was selected from a silhouette comparison of K-Means and Agglomerative clustering for k=2–6. DBSCAN was evaluated across multiple epsilon values. Churn was excluded from clustering to prevent target leakage. The selected K-Means solution uses the best silhouette score among k=3–6 to support separate models for at least three segments.

## Segment summary
| Segment | Name | Customers | Share | Avg tenure | Avg monthly charges | Churn rate |
|---:|---|---:|---:|---:|---:|---:|
| 0 | Established Higher-Spend | 125 | 25.0% | 36.7 | 116.8 | 11.2% |
| 1 | Newer / Shorter-Tenure | 117 | 23.4% | 36.0 | 106.7 | 11.1% |
| 2 | Newer / Shorter-Tenure | 132 | 26.4% | 35.4 | 109.4 | 9.1% |
| 3 | Established Higher-Spend | 126 | 25.2% | 38.0 | 121.3 | 11.1% |

## Interpretation and actions
### Segment 0: Established Higher-Spend
- Customer count: 125
- Churn rate: 11.2%
- Recommendation: Prioritize retention outreach: contact at-risk customers, investigate service/billing friction, and test targeted loyalty offers.
### Segment 1: Newer / Shorter-Tenure
- Customer count: 117
- Churn rate: 11.1%
- Recommendation: Prioritize retention outreach: contact at-risk customers, investigate service/billing friction, and test targeted loyalty offers.
### Segment 2: Newer / Shorter-Tenure
- Customer count: 132
- Churn rate: 9.1%
- Recommendation: Strengthen onboarding: provide setup guidance, early-life check-ins and clear explanations of plan value.
### Segment 3: Established Higher-Spend
- Customer count: 126
- Churn rate: 11.1%
- Recommendation: Prioritize retention outreach: contact at-risk customers, investigate service/billing friction, and test targeted loyalty offers.

## Clustering comparison
- Selected K-Means cluster count: 4.
- Best K-Means silhouette score among k=3–6: 0.181.
- Agglomerative clustering was evaluated with Ward linkage.
- DBSCAN was tested over eps values 0.8 to 2.0 (min_samples=5); noise points are recorded in clustering_algorithm_comparison.csv.

## Prediction approach
A separate Random Forest model predicts churn within each selected segment. GridSearchCV tunes tree count, maximum depth and split/leaf constraints where there are enough observations from both target classes. See model_evaluation_results.csv for per-segment holdout metrics and tuning status.

## Limitations
The dataset contains 500 customers and 53 churn cases. Segment-level churn counts can be small, making metrics sensitive to the train/test split. AUC is undefined when a segment's test partition contains only one class. Customer lifetime value, campaign cost and intervention outcomes were not provided, so financial impact is not quantified.