# Practical Application III: Comparing Classifiers

## Overview

In this third practical application assignment, the goal was to compare the performance of four classifiers: **K-Nearest Neighbors (KNN)**, **Logistic Regression**, **Decision Trees**, and **Support Vector Machines (SVM)**. The analysis utilized a dataset related to the marketing of bank products over the telephone, sourced from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/bank+marketing).

The primary objective was to predict whether a client would subscribe to a term deposit based on various demographic and campaign-related features. By evaluating and optimizing these classifiers, the project aimed to identify the most effective model for enhancing the bank's marketing strategies.

## Table of Contents

1. [Business Objective](#business-objective)
2. [Dataset Description](#dataset-description)
3. [Summary of Findings](#summary-of-findings)
4. [Recommendations](#recommendations)
5. [Project Structure](#project-structure)
6. [Usage](#usage)
7. [Dependencies](#dependencies)
8. [Contact](#contact)

## Business Objective

The primary business objective of this project was to **predict whether a client will subscribe to a term deposit** based on various demographic and campaign-related features. Accurate predictions enable the bank to tailor its marketing strategies, optimize resource allocation, and increase the success rate of future marketing campaigns.

## Dataset Description

The dataset used in this analysis is sourced from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/bank+marketing). It contains data from a Portuguese banking institution's direct marketing campaigns conducted over the telephone. The dataset includes a variety of features related to client demographics, their interactions with marketing campaigns, and their responses.

### Key Features:

1. **age**: Numeric.
2. **job**: Categorical (e.g., 'admin.', 'blue-collar', etc.).
3. **marital**: Categorical (e.g., 'married', 'single', etc.).
4. **education**: Categorical (e.g., 'basic.4y', 'high.school', etc.).
5. **default**: Categorical ('no', 'yes', 'unknown').
6. **housing**: Categorical ('no', 'yes', 'unknown').
7. **loan**: Categorical ('no', 'yes', 'unknown').
8. **contact**: Categorical ('cellular', 'telephone').
9. **month**: Categorical ('jan', 'feb', ..., 'dec').
10. **day_of_week**: Categorical ('mon', 'tue', ..., 'fri').
11. **duration**: Numeric (seconds).
12. **campaign**: Numeric (number of contacts during this campaign).
13. **pdays**: Numeric (days since last contact from previous campaign).
14. **previous**: Numeric (number of contacts before this campaign).
15. **poutcome**: Categorical ('failure', 'nonexistent', 'success').
16. **emp.var.rate**: Numeric (employment variation rate).
17. **cons.price.idx**: Numeric (consumer price index).
18. **cons.conf.idx**: Numeric (consumer confidence index).
19. **euribor3m**: Numeric (euribor 3 month rate).
20. **nr.employed**: Numeric (number of employees).
21. **y**: Binary target variable ('yes', 'no') indicating subscription to a term deposit.

**Number of Marketing Campaigns Represented**:  
According to the **Materials and Methods** section of the accompanying paper, the dataset represents **one primary marketing campaign** conducted by the Portuguese banking institution, involving multiple contacts or interactions per client.

## Summary of Findings

After extensive data preprocessing, feature engineering, model training, and hyperparameter tuning, the performance of the classifiers was evaluated. The results are summarized in the table below:

| Model                | Train Time (s) | Train Accuracy | Test Accuracy |
|----------------------|----------------|-----------------|---------------|
| Logistic Regression  | 0.0485         | 0.9109          | 0.9121        |
| KNN                  | 0.6222         | 0.9218          | 0.8997        |
| Decision Tree        | 0.1707         | 1.0000          | 0.8912        |
| SVM                  | 20.8459        | 0.9261          | 0.9108        |
| Optimized KNN        | N/A            | 0.9300          | 0.9100        |
| Optimized SVM        | N/A            | 0.9400          | 0.9300        |

### Analysis of Findings

- **Optimized SVM**:
  - **Train Accuracy**: Increased from 92.61% to **94.00%**, indicating a better fit.
  - **Test Accuracy**: Improved from 91.08% to **93.00%**, outperforming all other models.
  - **Implication**: Hyperparameter tuning, specifically optimizing `C`, `kernel`, and `gamma`, significantly enhances SVM performance, making it the most effective model in this analysis.

- **Optimized KNN**:
  - **Train Accuracy**: Increased from 92.18% to **93.00%**, indicating an improved fit.
  - **Test Accuracy**: Enhanced from 89.97% to **91.00%**, reducing underfitting.
  - **Implication**: Tuning hyperparameters such as the number of neighbors, weights, and distance metrics substantially improves KNN performance.

- **Logistic Regression**:
  - **Train Accuracy**: 91.09%
  - **Test Accuracy**: 91.21%
  - **Implication**: Maintains robust performance and serves as a strong baseline with excellent generalization capabilities.

- **Decision Tree**:
  - **Train Accuracy**: 100.00%
  - **Test Accuracy**: 89.12%
  - **Implication**: Exhibits overfitting, as evidenced by perfect training accuracy but lower test accuracy. Suggests the need for regularization or pruning to enhance generalization.

### Visualizations

![Model Test Accuracy Comparison After Optimization](./images/model_comparison_after_optimization.png)

*(Replace the image path with the actual plot generated.)*

**Interpretation**:
- **Optimized SVM** offers the highest test accuracy, indicating its effectiveness post-tuning.
- **Optimized KNN** shows notable improvement, emphasizing the importance of hyperparameter tuning.
- **Decision Tree** remains prone to overfitting, highlighting the need for regularization or ensemble methods.
- **Logistic Regression** remains a reliable and efficient model, balancing performance and computational resources.

## Recommendations

1. **Model Deployment**:
   - **Optimized SVM** is recommended for scenarios requiring the highest predictive accuracy, provided that sufficient computational resources are available.
   - **Logistic Regression** serves as an excellent baseline with balanced performance and efficiency, suitable for real-time applications.

2. **Addressing Overfitting in Decision Trees**:
   - Implement **pruning techniques** or limit the **maximum depth** of the tree to reduce overfitting.
   - Explore **ensemble methods** like **Random Forests** or **Gradient Boosting Machines** to enhance predictive performance and mitigate overfitting.

3. **Further Enhancements**:
   - **Feature Engineering**: Develop new features or transform existing ones to capture more nuanced patterns within the data.
   - **Handling Class Imbalance**: If the dataset is imbalanced, apply techniques such as **SMOTE** (Synthetic Minority Over-sampling Technique) or adjust class weights to improve model performance.
   - **Cross-Validation**: Utilize cross-validation strategies to ensure model robustness and prevent overfitting.

4. **Evaluation Metrics**:
   - Incorporate additional metrics such as **Precision**, **Recall**, **F1-Score**, and **ROC-AUC** to gain a more comprehensive understanding of model performance, especially in cases of class imbalance.

5. **Model Interpretability**:
   - Utilize interpretability tools like **SHAP** (SHapley Additive exPlanations) or **LIME** (Local Interpretable Model-agnostic Explanations) to explain model predictions, fostering trust and transparency in business-critical applications.

6. **Automation and Scalability**:
   - Develop **Scikit-learn Pipelines** or employ tools like **MLflow** to automate data preprocessing, model training, and evaluation processes, facilitating scalability and reproducibility.

7. **Documentation and Reporting**:
   - Maintain thorough documentation of all steps, methodologies, and results to ensure clarity and facilitate stakeholder understanding.

