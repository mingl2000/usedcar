# usedcar
### Business Understanding
    The bsuiness wants to find what impact used car price most and how.
####  Data Observation
    - Model column has a lot of discret values. 7% of the values in this column contributes to 80% of the records. 
        - Replace all other models not in the top models found here will reduce the one-hot encoding columns by 27000. 
    - Id and VIN column are not price related and should be dropped from modeling process
    
### Data Preparation
    - Drop ID and VIN column which won't have any impact to price.
    - All null values for non-numerical columns are replaced by "other" which seems to be the default value for these columns.
    - All null values for numerical columns are replaced by 0
    - All models in model column not in the top 7% of the models are replaced by "other". This reduces the one-hot encoding columns by 27000. It signficently reduce the processing time and hardware requirements

### Modeling
    - The following models are studied:
        - Linear regression 
        - PolynomialFeatures
        - Ridge regression
        - Lasso
        - SequentialFeatureSelector
        - Feature selection using Lasso
    -  polynomial of year and odometer are used in the following models:
        - PolynomialFeatures
        - Lasso
        - SequentialFeatureSelector
        - Feature selection using Lasso
    - OrdinalEncoder is used for condition column
    - OneHotEncoder is used for all other non-numerical columns.


### Valuation
    -  The model tests clearly show that the Lasso selection model got the lowest mean square value for both training and testing. 
    -  Top feature selected by this model are ploynomail of year and features mostly. If diesel is used as fule, it has strong impact as well.      

### Deployment

    Based on the finding, we can use the Lasso selection model to select the features and then use the Linear Regression model to predict the price.


#### What's learned
    Model has 29000+ discret values. This turns out to be the biggest chanllenge for SequentialFeatureSelector model.
    - In this model, PolynomialFeatures with power of 3 and onehot encoder for all discret columns. When all models are used, more memory is needed than what the machine has.
    - The solution is to find the most important models and replace the rest to "other". 
    - 283 models have 50% of market share in this dataset. All other models, 29000+ are changed to "other". This dramatically reduce the training data dimensionality. 