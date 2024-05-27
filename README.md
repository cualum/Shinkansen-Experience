# Final Project Report: Enhancing Passenger Experience on the Shinkansen Bullet Train

*Prepared for: Machine Learning Course, University of Colorado - Boulder*

## Introduction

The Shinkansen Bullet Train in Japan aims to provide passengers with a seamless and satisfying travel experience. In this final project, we analyze a comprehensive dataset collected from passenger surveys to gain insights into passenger preferences and predict their overall experience. By leveraging machine learning techniques, we seek to identify key areas for improvement to enhance service quality.

![image](https://github.com/cualum/Shinkansen-Experience/assets/137105371/f48920e0-6a56-447c-bbeb-7e7b5d655e7f)

## 1. Exploratory Data Analysis (EDA)
We initiated our analysis with thorough Exploratory Data Analysis (EDA) to understand the dataset's characteristics and potential correlations. Utilizing custom visualization techniques, including histograms and scatter plots, we gained valuable insights into the distribution of data and possible relationships between variables.

Example:
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/98f6a9c7-fabb-423d-ac76-cfe0ce8d3de8" width="600">
   </div>

## 2. Data Preprocessing
Minimal preprocessing was required, primarily focusing on mapping ordinal categorical variables for better visualization and modeling. Missing data imputation and multicollinearity checks were deferred to the modeling stage.

## 3. Data Engineering

Systematic variable reduction was conducted, eliminating features with high multicollinearity and insignificant p-values using Statsmodels. This step ensured the selection of relevant predictors for modeling.

## 4. Model Selection and Training

Several models, including Random Forest, XGBoost, and logistic regression, were evaluated. Data preparation involved imputation, scaling, and encoding, automated using Scikit-learn's Pipeline and ColumnTransformer. Hyperparameters were tuned using GridSearchCV with KFold cross-validation.

   - Numerical missing data will be imputed using IterativeImputer with the KNeighborsRegressor as the estimator
   - Categorical missing data will be imputed using SimpleImputer with 'most_frequent' as the strategy
   - Numerical data will be scaled with RobustScaler
   - Ordinal categorical data will be encoded with OrdinalEncoder
   - Nominal categorical data will be encoded with OneHotEncoder
   - hyperparamters will be tuned using GridSearchCV with with KFold crossvalidation from the scikit learn library.

 Example of workflow is given below. The data imputation, scaling, and encoding will be handled at each GridSearch fold seperately thereby avoiding data leakage.
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/2a64b13f-4b60-4461-af5a-d3bf608fc739">
   </div> 

## 5. Model Evaluation

Evaluation metrics, with a focus on F1_score for binary classification, were employed to assess model performance on training and testing data. Random Forest and XGBoost demonstrated similar performance, with XGBoost exhibiting computational efficiency advantages over Random Forest, while logistic regression showed limited performance due to its linear nature.

Example:
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/31e96b15-8d12-44a2-839e-5813b7888098" width="600">
   </div> 
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/55263238-ee14-46e0-a200-32fab0d62285" width="600">
   </div> 
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/b39dd856-b78d-4e42-99e9-48cf325dd49c" width="600">
   </div>


## Key Observations

### Trade-offs Among Models:

#### Random Forest:
- **Strengths:**
  - Random Forest demonstrates robust performance in capturing complex relationships within the data.
  - It's less prone to overfitting due to the ensemble nature of decision trees.
  - Random Forest handles both numerical and categorical data well without requiring extensive preprocessing.
- **Trade-offs:**
  - While Random Forest performs well in many scenarios, it may not provide as much insight into the underlying relationships between predictors and the target variable compared to more interpretable models like logistic regression.
  - The computational cost of training Random Forest can be higher compared to simpler models, especially on large datasets.

#### XGBoost:
- **Strengths:**
  - XGBoost offers superior computational efficiency compared to Random Forest, making it suitable for large datasets and time-constrained scenarios.
  - It provides excellent predictive performance by iteratively building decision trees to correct errors made by previous models.
  - Feature importance analysis in XGBoost is particularly insightful, allowing identification of key predictors contributing to the model's performance.
- **Trade-offs:**
  - While XGBoost excels in predictive accuracy and efficiency, its complexity may pose challenges in terms of model interpretability, especially when explaining predictions to stakeholders or regulatory bodies.
  - Like Random Forest, XGBoost requires tuning of hyperparameters, which can be computationally expensive and require careful optimization.

#### Logistic Regression:
- **Strengths:**
  - Logistic Regression is simple, interpretable, and computationally efficient, making it a quick and effective baseline model.
  - It performs well when the relationship between predictors and the target variable is linear or can be reasonably approximated as such.
- **Trade-offs:**
  - Logistic Regression's simplicity is also its limitation, especially when dealing with complex, nonlinear relationships in the data. It may struggle to capture intricate patterns and interactions among predictors.
  - Feature importance analysis in Logistic Regression is straightforward, but it may not provide as nuanced insights as ensemble methods like Random Forest or XGBoost.

### Insights into Feature Importance:

- **Random Forest:** Feature importance in Random Forest is derived from the reduction in impurity (e.g., Gini impurity) brought by each feature across all decision trees. Features with higher importance contribute more to reducing impurity, indicating their significance in prediction.
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/8334f4d4-9f69-49e0-a28a-7c0f2e01543a" width="600">
   </div>
  
- **XGBoost:** Feature importance in XGBoost is calculated based on the number of times each feature is used to split the data across all decision trees and the average gain in accuracy achieved by those splits. Features with higher importance contribute more to improving model performance.
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/3df4a31f-25cf-4489-aa30-7602d416e5a5" width="600">
   </div>


  
- **Logistic Regression:** Feature importance in Logistic Regression is typically measured by the magnitude of coefficients assigned to each predictor. Larger coefficients indicate stronger influence on the predicted outcome. However, interpretation should be cautious, as coefficients represent the change in log-odds of the target variable for a unit change in the predictor, assuming other predictors remain constant.
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/4cb71d68-91e4-428f-9a5e-65d9fedd5fca" width="600">
   </div>

In summary, each model presents trade-offs between predictive performance, computational efficiency, and interpretability. Understanding these trade-offs is crucial in selecting the most appropriate model for the specific problem at hand, considering factors such as dataset size, complexity of relationships, and interpretative requirements.




## Results and Recommendations

### Key Findings and Recommendations:

- **Onboard Entertainment:** Enhance onboard entertainment options to diversify and engage passengers during the journey.
- **Seat Comfort:** Upgrade seating options to prioritize passenger comfort, especially in economy class.
- **Improvement of Online Services:** Focus on seamless online booking, customer support, and check-in processes to simplify travel logistics.
- **Onboard Services:** Improve catering quality and staff responsiveness to enhance the overall travel experience.
- **Check-In Services:** Streamline check-in procedures and reduce waiting times to facilitate a smoother start to the journey.

## Conclusion

By addressing these key areas of improvement, the Shinkansen Bullet Train can elevate passenger satisfaction, strengthen its reputation, and attract more passengers. Continuous feedback monitoring and implementation of recommendations will ensure the Shinkansen remains a symbol of excellence in high-speed rail travel, fostering loyalty and success in the transportation industry.

   

   



