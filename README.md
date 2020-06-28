## Problem definition

From frontline support teams to C-suites, customer satisfaction is a key measure of success. Unhappy customers don't stick around. What's more, unhappy customers rarely voice their dissatisfaction before leaving.

Santander Bank is asking Kagglers to help them identify dissatisfied customers early in their relationship. Doing so would allow Santander to take proactive steps to improve a customer's happiness before it's too late.

In this competition, you'll work with hundreds of anonymized features to predict if a customer is satisfied or dissatisfied with their banking experience.

##  Data description

train.csv - the training set including the target
test.csv - the test set without the target
sample_submission.csv - a sample submission file in the correct format

##  Script strategy

The train and test datasets are composed by 370 columns, in addition to the target variable. The great amount of possible predictive variables need to be handled in a suitable way to fit the predictive model requirements. This problem was turned around on this scrip by performing the following steps:

- Columns where the standard deviation is null were removed (around 103 columns)
- Columns where the correlation to the target variable is less than 0.18 (person method) were removed to be trated separately
- A PCA technique was used to turn the low correlation variables into 4 componets, with an explained variance ratio of 0.99

The outcome of this strategy turned the initial 370 columns into 14, which is more likely to be properly handled by the predictive model.

In addition, the data is normilized. 

New variables were created to enhance the predictions:

-var15_levels - reflecting the correlation to the target variable on var15
-zeros - number of zeros for each row (ID)
-zeros_level - reflecting the correlation of the "zeros" to the target variable

![var15](/Pictures/var15.png)
![var15_level](/Pictures/var15_level.png)
![zeros](/Pictures/zeros.png)
![zeros_level](/Pictures/zeros_level.png)

Predictive-Model.ipynb:

Logistic Regression is used for the predictive model.

