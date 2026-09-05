# Market Analysis

## Project Overview

This project evaluates the potential of the Indian automobile market using customer-level data.

The analysis uses the Japanese and Indian datasets provided as part of the Data Science project. A machine learning classification model is developed using Japanese customer data to predict the likelihood of purchasing a new car.
The trained model is then applied to the Indian customer dataset to estimate the potential customer base.

The project also includes exploratory data analysis and a Tableau dashboard to analyze and compare customer and purchasing trends.

## Objectives

- Analyze customer characteristics in the Japanese automobile market.
- Identify factors associated with car purchase decisions.
- Build a classification model to predict car purchase likelihood.
- Apply the trained model to Indian customer data.
- Estimate the potential customer base in India.  
- Evaluate whether the estimated customer pool can support a target of 12,000 car sales per year.
- Visualize key market trends using Tableau.

## Datasets

### Japanese Dataset

The Japanese dataset contains 40,000 customer records with the following features:

- `ID`
- `CURR_AGE`
- `GENDER`
- `ANN_INCOME`
- `AGE_CAR`
- `PURCHASE`

`PURCHASE` is the target variable:

- `0` = Did not purchase
- `1` = Purchased

### Indian Dataset

The Indian dataset contains 70,000 customer records with:

- `ID`
- `CURR_AGE`
- `GENDER`
- `ANN_INCOME`
- `DT_MAINT`

The Indian dataset does not contain a purchase outcome, so the model trained on Japanese data is used to estimate purchase likelihood for Indian customers.

## Methodology

### 1. Data Understanding and Quality Checks

The datasets were examined for:

- Missing values
- Duplicate records
- Data types
- Unique customer IDs
- Basic statistical characteristics

Both datasets contained no missing values or duplicate rows.

### 2. Exploratory Data Analysis

The datasets were explored to understand:

- Purchase distribution
- Purchase rate by gender
- Purchase rate by age group
- Income distribution
- Relationship between income and purchase
- Indian customer age and income patterns

### 3. Feature Selection

The common predictive features used by the model are:

- `CURR_AGE`
- `GENDER`
- `ANN_INCOME`

`ID` was excluded because it is an identifier rather than a meaningful predictive feature.

`AGE_CAR` was not used for Indian prediction because this variable is not available in the Indian dataset.

### 4. Data Preprocessing

Gender was encoded numerically:

- Female = `0`
- Male = `1`

The numerical features were standardized using `StandardScaler`.

The Japanese dataset was divided into:

- 80% training data
- 20% testing data

Stratified splitting was used to preserve the class distribution.

### 5. Machine Learning Model

A **Logistic Regression** model was selected because the target variable is binary and the model provides interpretable coefficients.

The model was trained using Japanese customer data and then used to predict purchase probability for Indian customers.

## Model Performance

The model achieved the following results on the test set:

| Metric | Score |
|---|---:|
| Accuracy | 61.33% |
| Precision | 61.80% |
| Recall | 85.95% |
| F1 Score | 71.90% |
| ROC-AUC | 60.45% |

Five-fold cross-validation produced a mean accuracy of approximately **61.92%**, which was close to the test accuracy.

The model showed particularly high recall for customers who purchased a car, while its overall predictive performance was moderate.

## Feature Interpretation

The logistic regression coefficients were:

| Feature | Coefficient | Odds Ratio |
|---|---:|---:|
| CURR_AGE | -0.0895 | 0.9144 |
| GENDER | 0.0881 | 1.0921 |
| ANN_INCOME | 0.3840 | 1.4681 |

Income had the strongest positive association with purchase likelihood among the features used in the model.

Holding other features constant:

- Higher age was associated with lower purchase odds.
- Male customers had slightly higher purchase odds than female customers.
- Higher income was associated with higher purchase odds.

## India Market Prediction

The trained Japanese model was applied to the 70,000 Indian customer records.

### Results

- Total Indian customer records: **70,000**
- Estimated potential customers: **69,946**
- Estimated potential customer percentage: **99.92%**
- Annual sales target: **12,000 cars**
- Target as a percentage of the Indian dataset: **17.14%**

The model-estimated potential customer pool is substantially larger than the 12,000-unit annual target.

## Tableau Dashboard

The project includes a Tableau dashboard containing visualizations for both markets.

### Indian Market

- Potential Customers by Gender
- Average Income by Gender
- Customer Age Distribution
- Purchase Probability by Age

### Japanese Market

- Japan Purchase Distribution
- Japan Purchase Rate by Gender
- Japan Purchase Rate by Age Group

The dashboard provides a visual comparison of customer characteristics and purchase-related trends between the two markets.

## Project Files

- `Market_Analysis.ipynb` - Complete Python analysis and machine learning workflow.
- `Market Analysis.twbx` - Tableau packaged workbook containing the dashboard.

## Key Business Insights

- The Japanese dataset has an overall purchase rate of approximately **57.58%**.
- Purchase rates are higher among customers in the **35-54 age range**.
- Male customers show a slightly higher purchase rate than female customers in the Japanese dataset.
- Income is the strongest positive predictor among the features used in the model.
- The model estimates a large potential customer pool within the Indian dataset.
- The estimated potential customer pool exceeds the target of **12,000 annual car sales**.

## Limitations

- The classification model is trained using Japanese customer data and applied to Indian customer data.
- The Indian dataset does not contain an actual purchase outcome for model validation.
- `AGE_CAR` could not be used for Indian prediction because it is unavailable in the Indian dataset.
- Differences between the Japanese training data and Indian customer data may affect model generalization.
- The estimated potential customer count represents a model-based estimate and should not be interpreted as guaranteed sales.

## Tools & Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Google Colab
- Tableau

## Conclusion

The analysis indicates that the Indian customer dataset contains a potentially large customer pool according to the trained classification model, and the estimated pool exceeds the target of 12,000 annual sales.

The project combines **data analysis, machine learning, statistical interpretation, and business visualization** to support an initial assessment of the Indian automobile market.
