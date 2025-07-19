# Student Study Habits - Final Grade Prediction

## Project Overview

This project explores the impact of various student study habits on their final grades using a dataset sourced from Kaggle: [Student Study Habits Dataset](https://www.kaggle.com/datasets/prekshad2166/student-study-habits). The primary goal is to build and compare multiple linear regression models to understand how different combinations of features influence the prediction of a student's final grade. This project demonstrates a foundational understanding of feature selection and model evaluation in machine learning.

## Project Steps

The project involved the following key steps:

1.  **Data Loading and Initial Exploration:**
    * The `ssh.csv` dataset was loaded into a Pandas DataFrame.
    * Initial data inspection was performed to understand the structure, data types, and identify potential issues.

2.  **Feature Selection Strategy:**
    * The target variable for prediction was identified as `'final_grade'`.
    * Features were selected based on their correlation with the `'final_grade'`. The rationale for feature selection was as follows:
        * `'study_hours_per_week'`: Highest correlation (approx. 0.517).
        * `'assignments_completed'`: Next highest correlation (approx. 0.389).
        * `'sleep_hours_per_day'`: Moderate correlation (approx. 0.238).
        * `'attendance_percentage'`: Moderate correlation (approx. 0.197).
    * Other categorical columns with 0/1 output were intentionally excluded from this linear regression analysis.

3.  **Model Development and Training:**
    Three distinct linear regression models were developed, each with a different set of features to observe their impact on performance:

    * **Model A:**
        * **Features Used:** `'study_hours_per_week'`
        * **Description:** This model serves as a baseline, using only the most strongly correlated feature.
        * **Performance:**
            * Mean Absolute Error (MAE): 5.002
            * Mean Squared Error (MSE): 40.801
            * Root Mean Squared Error (RMSE): 6.388
            * R-squared: 0.276

    * **Model B:**
        * **Features Used:** `'study_hours_per_week'`, `'assignments_completed'`
        * **Description:** This model expands on Model A by including the second most correlated feature.
        * **Performance:**
            * Mean Absolute Error (MAE): 4.382
            * Mean Squared Error (MSE): 33.441
            * Root Mean Squared Error (RMSE): 5.783
            * R-squared: 0.406

    * **Model C:**
        * **Features Used:** `'study_hours_per_week'`, `'sleep_hours_per_day'`, `'attendance_percentage'`, `'assignments_completed'`
        * **Description:** This model incorporates all chosen numerical features to assess the combined influence.
        * **Performance:**
            * Mean Absolute Error (MAE): 4.015
            * Mean Squared Error (MSE): 26.208
            * Root Mean Squared Error (RMSE): 5.119
            * R-squared: 0.535

4.  **Model Evaluation:**
    Each model's performance was evaluated using standard regression metrics:
    * **Mean Absolute Error (MAE):** Measures the average magnitude of the errors in a set of predictions, without considering their direction.
    * **Mean Squared Error (MSE):** Measures the average of the squares of the errors. It gives higher weight to larger errors.
    * **Root Mean Squared Error (RMSE):** The square root of the MSE, providing an error metric in the same units as the target variable.
    * **R-squared ($R^2$):** Represents the proportion of the variance in the dependent variable that is predictable from the independent variables. A higher $R^2$ indicates a better fit.

## Python Packages Used

The following Python libraries were essential for this project:

* **pandas:** For data manipulation and analysis.
* **scikit-learn:** For machine learning functionalities, including:
    * `train_test_split` for splitting data.
    * `LinearRegression` for model training.
    * `mean_absolute_error`, `mean_squared_error`, `r2_score` for model evaluation.
* **matplotlib:** For creating static visualiztion.
* **seaborn:** For creating advanced visualiztion.
* **math:** For `sqrt` function to calculate RMSE.

## Files in Repository

* `Model_A.ipynb`: Linear Regression with 1 feature
* `Model_B.ipynb`: Linear Regression with 2 feature
* `Model_C.ipynb`: Linear Regression with 4 feature
* `ssh.csv`: The dataset used in the project. (Renamed the original dataset variable from `student_study_habits` to `ssh` for easier reference during coding)
* `README.md`: This documentation file.

## Key Insights and Conclusion

Based on the performance metrics of the three models, the following insights can be drawn:

* **Impact of Feature Addition:** There's a clear improvement in model performance as more relevant features are added.
    * Model A (single feature) had the lowest $R^2$ (0.276) and highest errors.
    * Model B (two features) showed a significant improvement in $R^2$ (0.406) and reduced errors.
    * Model C (four features) performed the best, achieving an $R^2$ of 0.535 and the lowest MAE, MSE, and RMSE. This suggests that a combination of study hours, assignments completed, sleep hours, and attendance percentage are all influential factors in predicting a student's final grade.

* **Feature Importance:** While all chosen features contribute positively, `'study_hours_per_week'` and `'assignments_completed'` appear to be the most impactful initially, given the jump in performance from Model A to Model B.

* **Model C is the Best Performer (Among These):** For predicting final grades based on the chosen features and linear regression, Model C, utilizing all four selected features, provides the most accurate predictions among the three models developed.

* **Limitations of Linear Regression:** Although Model C performs better, an $R^2$ of 0.535 indicates that approximately 53.5% of the variance in final grades can be explained by the selected features using a linear model. This suggests that other factors not included in the model (or non-linear relationships) might also play a significant role.
