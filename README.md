This is the result of the final project for a machine learning course I took at the University of Colorado - Boulder.  


This notebook includes the standard steps for a project like this:
1) Exploratory Data Analysis:  A class was written to help with this protion.  The class loads the data and automatically produces a train/test split.  The class also has some usefull data manipulation and plotting methods for producing the typical data visualization plots in attractive formats as shown in the following plot.
   <img src="https://github.com/cualum/Shinkansen-Experience/assets/137105371/98f6a9c7-fabb-423d-ac76-cfe0ce8d3de8" width="200" height="200">


2) Data Preporcessing:  This dataset required little in the way of preprocessing.  It did contain categorical variables which have a natural ordering.  These were rankings like 'poor' and 'excellent'.  These categorical variables were mapped to ordinals using a a method defined in the class described in (1).  This allows for better visualization modeling. Imputation of missing data was deferred to the modeling section to automated techniques could be used.
3) Data Engineering:  In this section, variables were systematically eliminated.  First variables were eliminated with high multicolinearity by retaining variables with a variance-inflation-factor (VIF) of less than 5.  Typically this would be followed by eliminating variables with high p-value which indicates the variable may not be statistically significant. Rule of thumb is to eliminate variables with p-values greater than 0.5.   The Statsmodels package is particularly convenient for this.
4) Model selection and training:  Several models were evaluated to compare there relative advantages in this work (randomforrest, XGBoost, and logistic regression).  The data will be preparred in the following manner:
   - Numerical missing data will be imputed using IterativeImputer with the KNeighborsRegressor as the estimator
   - Categorical missing data will be imputed using SimpleImputer with 'most_frequent' as the strategy
   - Numerical data will be scaled with RobustScaler
   - Ordinal categorical data will be encoded with OrdinalEncoder
   - Nominal categorical data will be encoded with OneHotEncoder

   The flow of this preparation will be automated using a combination of ColumnTransformer and Pipeline from the Scikit-learn library.  Finally the data preparation and modeling will be automated using PipeLine.  The best hyperparameters will be found using GridSearchCV with KFolds defining the splits.  Example of workflow is given below. The data imputation, scaling, and encoding will be handled at each GridSearch fold seperately thereby avoiding data leakage.
   ![workflow](https://github.com/cualum/Shinkansen-Experience/assets/137105371/2a64b13f-4b60-4461-af5a-d3bf608fc739)
   An exhaustive list of metrics will be produced but F1_score will primarily be used for optimization because it is a good choice for binary classification problems.  Example:
   ![ex](https://github.com/cualum/Shinkansen-Experience/assets/137105371/31e96b15-8d12-44a2-839e-5813b7888098)
   ![ex2](https://github.com/cualum/Shinkansen-Experience/assets/137105371/55263238-ee14-46e0-a200-32fab0d62285)
   ![image](https://github.com/cualum/Shinkansen-Experience/assets/137105371/b39dd856-b78d-4e42-99e9-48cf325dd49c)



