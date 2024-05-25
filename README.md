This is the result of the final project for a machine learning course I took at the University of Colorado - Boulder.  


This notebook includes the standard steps for a project like this:
1) Exploratory Data Analysis:  A class was written to help with this protion.  The class loads the data and automatically produces a train/test split.  The class also has some usefull data manipulation and plotting methods for producing the typical data visualization plots in attractive formats as shown in the following plot.
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/98f6a9c7-fabb-423d-ac76-cfe0ce8d3de8" width="600">
   </div>



3) Data Preporcessing:  This dataset required little in the way of preprocessing.  It did contain categorical variables which have a natural ordering.  These were rankings like 'poor' and 'excellent'.  These categorical variables were mapped to ordinals using a a method defined in the class described in (1).  This allows for better visualization modeling. Imputation of missing data was deferred to the modeling section to automated techniques could be used.
4) Data Engineering:  In this section, variables were systematically eliminated.  First variables were eliminated with high multicolinearity by retaining variables with a variance-inflation-factor (VIF) of less than 5.  Typically this would be followed by eliminating variables with high p-value which indicates the variable may not be statistically significant. Rule of thumb is to eliminate variables with p-values greater than 0.5.   The Statsmodels package is particularly convenient for this.
5) Model selection, training, and hyperparameter tuning:  Several models were evaluated to compare there relative advantages in this work (randomforrest, XGBoost, and logistic regression).  The data will be preparred in the following manner:
   - Numerical missing data will be imputed using IterativeImputer with the KNeighborsRegressor as the estimator
   - Categorical missing data will be imputed using SimpleImputer with 'most_frequent' as the strategy
   - Numerical data will be scaled with RobustScaler
   - Ordinal categorical data will be encoded with OrdinalEncoder
   - Nominal categorical data will be encoded with OneHotEncoder
   - hyperparamters will be tuned using GridSearchCV with with KFold crossvalidation from the scikit learn library.

   The flow of this preparation will be automated using a combination of ColumnTransformer and Pipeline from the Scikit-learn library.  Finally the data preparation and modeling will be automated using PipeLine.  The best hyperparameters will be found using GridSearchCV with KFolds defining the splits.  Example of workflow is given below. The data imputation, scaling, and encoding will be handled at each GridSearch fold seperately thereby avoiding data leakage.
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/2a64b13f-4b60-4461-af5a-d3bf608fc739">
   </div> 

6) Model evaluation:  An exhaustive list of metrics were be produced but F1_score were primarily used for optimization because it is a good choice for binary classification problems.  The training and testing data are evaluated and compared to assess the generalization capability of the model.  Example:
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/31e96b15-8d12-44a2-839e-5813b7888098" width="600">
   </div> 
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/55263238-ee14-46e0-a200-32fab0d62285" width="600">
   </div> 
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/b39dd856-b78d-4e42-99e9-48cf325dd49c" width="600">
   </div>

7) Finally Obserations:  The main goal of this project was to evaluate which aspects of the trip on the bullet train had the most influence on the customer satisfaction.  To this end, 'feature importance' graphs were produced to evaluate their relative importance.  Results from each of the models are show below
   - Random Forest
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/8334f4d4-9f69-49e0-a28a-7c0f2e01543a" width="600">
   </div>

   - XGBoost
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/3df4a31f-25cf-4489-aa30-7602d416e5a5" width="600">
   </div>

   - Logistic Regression
   <div style="text-align: center;">
    <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/4cb71d68-91e4-428f-9a5e-65d9fedd5fca" width="600">
   </div>



   

   



