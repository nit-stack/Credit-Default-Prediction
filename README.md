# Credit Default Prediction

## Overview

This project aims to predict the likelihood of a company defaulting on its financial obligations based on its financial statements. A company's inability to manage its debt obligations can lead to default, resulting in a lower credit rating and higher interest rates on existing and future debts. Investors require insights into a company's financial health to make informed decisions about their investments. Our analysis leverages the financial data of companies to predict default risk.

## Problem Statement

Businesses or companies can default if they fail to meet their debt obligations. Defaults lead to lower credit ratings, reducing their chances of obtaining credit in the future and increasing the cost of borrowing. Investors prefer to invest in companies that can handle their financial obligations, grow quickly, and manage growth effectively.

A balance sheet is a financial statement that provides a snapshot of what a company owns, owes, and the shareholders' equity. It is a crucial tool for evaluating a business's performance.

## Data Description

The available data includes financial statements from 2015 and the net worth of companies in 2016, which is used to create the labeled field.

- **Data Dictionary:** Detailed information about the data fields is available in 'Credit Default Data Dictionary.xlsx'.
- **Target Variable:** The default variable takes a value of 1 when the net worth next year is negative and 0 when it is positive.

## Data Exploration and Preparation

### Basic Data Exploration

- The dataset contains 3586 rows and 68 columns.
- There are no duplicate rows, representing 3586 unique organizations.
- Columns “Company Name” and “Company Code” have been dropped due to their insignificance in modeling.

### Descriptive Statistics

- The significant difference between the mean and median indicates asymmetry in the data.
- Comparison of percentiles highlights the presence of outliers.
- Higher standard deviation values indicate greater data spread, except for “Creditors Velocity” and “Value of Output/Total Assets”.
- Approximately 11% of the organizations have defaulted.

### Missing Values

- 13 variables have missing values.
- We decided not to drop rows with missing values as each row represents a unique organization.
- Mean imputation was performed to treat missing values.

### Outliers

- Outliers were identified using boxplots and treated by scaling values beyond the upper and lower quartiles.

### Correlation Analysis

- A heatmap was used to understand the correlation among variables.
- Highly correlated variables were identified and grouped.

## Univariate and Bivariate Analysis

- Performed on the most significant variables for modeling.
- Boxplots confirmed the success of outlier treatment.
- Bivariate analysis indicated that defaulters tend to have:
  - Lower current ratio
  - Higher creditors velocity
  - Slightly lower debtor’s velocity
  - Lower debtors ratio
  - Lower interest cover ratio

## Modeling

### Logistic Regression using Statsmodels

- Data was split into training (67%) and testing (33%) datasets using `random_state=42`.
- Variance Inflation Factor (VIF) was used to identify multicollinearity and select significant variables.
- The logistic regression model was iteratively refined to include only variables with p-values < 0.05.

### Model Evaluation

- The default probability threshold was optimized using the ROC curve metric, resulting in a threshold of 0.16.
- Model performance was evaluated using recall as the primary metric:
  - Recall on the training set: 0.755
  - Recall on the test set: 0.776

The similar recall values for training and test sets indicate that the model is not overfitted.

## Final Inference

The model provides valuable insights for investors, helping them make informed decisions about their investments. By analyzing the financial data of over 3000 companies, the model predicts the likelihood of default, aiding prudent investment choices.
