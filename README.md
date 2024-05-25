This is the result of the final project for a machine learning course I took at the University of Colorado - Boulder.  It includes the standard steps for a project like this:
1) Exploratory Data Analysis:  A class was written to help with this protion.  The class loads the data and automatically produces a train/test split.  The class also has some usefull data manipulation and plotting methods for producing the typical data visualization plots in attractive formats as shown in the following plot.
   ![plot](https://github.com/cualum/Shinkansen-Experience/assets/137105371/98f6a9c7-fabb-423d-ac76-cfe0ce8d3de8)

2) 



The data will be preparred in the following manner:

    Numerical missing data will be imputed using IterativeImputer with the KNeighborsRegressor as the estimator
    Categorical missing data will be imputed using SimpleImputer with 'most_frequent' as the strategy
    Numerical data will be scaled with RobustScaler
    Ordinal categorical data will be encoded with OrdinalEncoder
    Nominal categorical data will be encoded with OneHotEncoder

The flow if this preparation will be automated using a combination of ColumnTransformer and Pipeline from the Scikit-learn library

Finally the data preparation and modeling will be automated using PipeLine.

The best hyperparameters will be found using GridSearchCV with KFolds defining the splits.

Example of workflow is given below. The data imputation, scaling, and encoding will be handled at each GridSearch fold seperately thereby avoiding data leakage.

![workflow](https://github.com/cualum/Shinkansen-Experience/assets/137105371/2a64b13f-4b60-4461-af5a-d3bf608fc739)


An exhaustive list of metrics will be produced but F1_score will primarily be used for optimization because it is a good choice for binary classification problems.
