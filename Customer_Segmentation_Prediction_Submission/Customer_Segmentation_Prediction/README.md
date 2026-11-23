# Customer Segmentation & Prediction

## Project objective
Use unsupervised clustering to identify customer groups, train separate churn prediction models for each segment, evaluate model performance and recommend segment-specific business actions.

## Dataset
`customer_churn(2).csv` (500 records; 9 source columns). The dataset contains 447 retained customers and 53 churned customers. No missing values were found in the supplied file.

## Project structure
- `customer_segmentation.ipynb` – analysis and modeling notebook
- `segmentation_data.csv` – customer records with cluster assignments
- `segment_profiles.md` – segment names, profiles, methodology and recommendations
- `model_evaluation_results.csv` – segment-level classification metrics and tuning status
- `clustering_algorithm_comparison.csv` – K-Means, Agglomerative and DBSCAN comparison
- `business_recommendations.pdf` – business recommendations report
- `visualizations/` – visual evidence charts
- `models/` – saved segment Random Forest pipelines
- `customer_churn_source.csv` – copy of original input dataset
- `requirements.txt` – dependencies

## Setup
1. Install Python 3.10 or later.
2. Create and activate a virtual environment (optional but recommended).
3. Run `pip install -r requirements.txt`.
4. Open `customer_segmentation.ipynb` in Jupyter Notebook or upload the project folder to Google Colab.
5. Run the notebook from top to bottom. The notebook uses `segmentation_data.csv` as the prepared data for reproducing model training; the original source is included.

## Technical methodology
- Preprocessing: median imputation, standard scaling for numeric features and one-hot encoding for categorical features.
- Clustering: K-Means with elbow/silhouette assessment, Agglomerative clustering and DBSCAN comparison.
- Target leakage prevention: `Churn` and `CustomerID` are excluded from clustering.
- Prediction: separate Random Forest churn classifier for each K-Means segment.
- Hyperparameter tuning: GridSearchCV optimizes tree count, maximum depth and split/leaf constraints when class counts permit.
- Evaluation: accuracy, precision, recall, F1-score and ROC-AUC.

## Testing and validation
- Checked shape, data types, missing values, duplicate customer IDs and non-negative tenure/charge values.
- Confirmed cluster labels are assigned to every retained customer.
- Confirmed per-segment evaluation output is generated.
- Model scores must be interpreted with segment sample sizes and churn-class counts; small segments can produce unstable metrics.

## Visual documentation
See `visualizations/` for cluster scatter plot, segment sizes, segment churn rates, charge distributions and segment profile heatmap.

## Limitations
The input has 500 records and 53 churn cases. Segment-level models may have limited minority-class examples; AUC is unavailable if a test segment contains only one target class. The source does not include customer lifetime value, intervention costs or campaign outcomes, so financial impact should be measured after a controlled retention test rather than invented.
