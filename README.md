# Snowfall Prediction Challenge

## Overview

This project aims to predict whether it will snow tomorrow based on historical weather data from over 9000 stations worldwide.
The goal is to forecast the weather for the date exactly 15 years ago.

## Setup and Installation

**Install Necessary Libraries**:

```bash
pip install google-cloud-bigquery google-cloud-bigquery-storage pyarrow db-dtypes pandas numpy matplotlib seaborn scikit-learn
```

**Authenticate and Configure Google Cloud**:

```bash
gcloud auth application-default login
gcloud config set project your-project-id
```

## Usage

**Load BigQuery Extension**:

```python
%load_ext google.cloud.bigquery
```

Load the BigQuery extension to facilitate SQL queries directly within the Jupyter notebook.

**Set Environment Variables**:

```python
import os
os.environ["GOOGLE_CLOUD_PROJECT"] = "your-project-id"
```

Set up the Google Cloud project environment to ensure proper configuration for BigQuery.

**Query Data**:

```python
%%bigquery
SELECT
*
FROM `bigquery-public-data.samples.gsod`
LIMIT 20
```

Use BigQuery to retrieve historical weather data for analysis and modeling.

**Data Processing**:

- **Clean and prepare data**: Remove any inconsistencies or errors in the dataset to ensure accurate analysis.
- **Handle missing values**: Address any missing data points to prevent them from skewing the model's performance.
- **Feature engineering**: Create new features or modify existing ones to improve the model's predictive power.

These steps are crucial to prepare the dataset for effective modeling.

**Model Selection and Training**:

- Random Forest is chosen for its robustness and ability to handle large datasets with many features, reducing
  overfitting through ensemble learning.
- Logistic Regression is also trained for comparison, offering simplicity and interpretability.

**Model Evaluation**

- Accuracy is a straightforward metric to gauge the model's performance, indicating the proportion of correctly
  predicted instances.
- Confusion matrix and classification report provide detailed insights into the model's performance, including
  precision, recall, and F1-score.

**Prediction**:

- Making specific predictions demonstrates the model's practical application in forecasting weather conditions
  for a given date.

## Conclusion

The Random Forest classifier achieved an accuracy of 91.11% on evaluation data and 90.72% on test data, demonstrating
strong performance in identifying both snowfall and non-snowfall days. In comparison, the Logistic Regression model had
an accuracy of 89.57% on evaluation data and 89.35% on test data. Therefore, the Random Forest model outperformed the
Logistic Regression model and is the recommended choice for predicting snowfall.

## License

This project is licensed under the MIT License.
