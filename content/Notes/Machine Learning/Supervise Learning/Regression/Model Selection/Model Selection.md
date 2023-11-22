# Model Selection

## Selecting a model among a set of candidate models:
---
#### understand the constraint of the model that we need:
- consider other constraint that is not just related to the numerical and quanitiative mean
- linearity
- what is the best predictors 


#### ![[Train-Validation-Test sets]]
#### Asseesment or Selection:
- Data Splitting
- 
#### Basic performance metrics:
Regression: 
- $R^2$:
	- Generalization error, we are interested in accuracy of predictions when we apply our model to **previously unseen data**
	- $R^{2}$ and a training test is a great matrix 
	- we should not only use $R^2$ to understand the parameters, because it won't count the overfitting, better metrics like adjusted $R^2$, AUC, AOC are better 
	- 
- 
- 
- 
- RMSE, PRESS

Classification: Accuracy, Precision/Recall, AUC-AOC



---

### Model selection:
==regularization = protection against overfitting==

Compare different models:
- lasso logistic regression
	- Comapre different hyperparameters within a class
- Ridge logistic Regression
- Random forest
Most model have "hyperparameters"

<mark style="background: #FF5582A6;">We want to find the optimal hyperparameters </mark>

---

### Steps:
1. split on train/validation/test:
2. Split on train/test 
	- Do cross-validation on the entire set
3. 


#### confidence intervals: 
Repeated holdout 



---
#### TAGS