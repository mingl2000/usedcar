# usedcar
### Link to the notebook:
    - [used car notebook](https://github.com/mingl2000/usedcar/blob/main/prompt_II.ipynb)
    - <https://github.com/mingl2000/usedcar/blob/main/prompt_II.ipynb>

### Summary of findings:
    -  The model tests clearly show that the Lasso selection model got the lowest mean square value for both training and testing among the training and testing of the following models:
        - Linear regression 
        - PolynomialFeatures
        - Ridge regression
        - Lasso
        - SequentialFeatureSelector
        - Feature selection using Lasso
    -  Top feature selected by this model are ploynomail of year and features mostly. If diesel is used as fule, it has strong impact as well.      

#### What's learned
    Model has 29000+ discret values. This turns out to be the biggest chanllenge for SequentialFeatureSelector model.
    - In this model, PolynomialFeatures with power of 3 and onehot encoder for all discret columns. When all models are used, more memory is needed than what the machine has.
    - The solution is to find the most important models and replace the rest to "other". 
    - 283 models have 50% of market share in this dataset. All other models, 29000+ are changed to "other". This dramatically reduce the training data dimensionality. 