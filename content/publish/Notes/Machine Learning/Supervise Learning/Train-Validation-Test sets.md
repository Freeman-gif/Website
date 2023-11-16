# Train-Validation-Test sets


---
#### Train:
a subset of the data used to **Fit the model**
#### validation:
a subset of the data used to **decide between models **
#### Test set :
a subset of the data used to **estimate error**

#### Train - Test split:
- Most commonly used is the random split:
	- Independent events
- Time-based split:
	- Stock market
- Split by id
	- Multiple observations per person
How to select:
- What is the sampling unit
- How are we going to use the model


Grid Search vs. Random Search 

#### Cross validation:
- Leave-one-out:
- k-fold cross-validation:
	- Randomize observations
	- Divide in k groups(folds) of approximately equal size
	- Use one fold for test and the test for training 
	- repeat k times
	- average over all test sets 
Model selection vs estimating test error

##### Feature selection during model selection:
scale the training set after the train-test split
**Feature selection:**

==Normalizaing data & selecting feature should be done inside the training set==

Train and validation in ==Time Series==:
- Consider how does the data collected(etc. pattern every year or month. )
- How much validation we are going to forecast( half cycle or a full cycle )
  1. Examine the pattern of the data to choose train and validation set 
  2. Train is always the history and the validation is always the future
  3. Test set is optional, only have a test set if you're asked to do so

**Step:**
- Split the data into train + test
- use train set to fit all the ARMA(p,q) models with different p and q
- each model will generate forecast on len(test)
- compare RMSE(test, $\hat{test}$) of each model. choose the model with smallest RMSE.


###### note: in TS, everything need to follow a time order. so in term of the cross validation process, it would be different 
**K-fold**:
Expending window cross validation 
- K(3,5,10)
	- thinking about the time take to training, smaller the k take less time
- validation size
	- it depend on the study, how long we want to forecast. choose the same validation size same as the final forecast window
- Rolling size:
	- Use all the data, most likely the same as the validation size 
- Initial training size :
	- n-k * validation 
###### try to design size h that rain and validation sets have 

---

### Def:
we are interested in **generalization error :**
- expected value of the error on<mark style="background: #FF5582A6;"> future</mark> data 
- Estimated by computing error pn a large independent **Test ** set 
- 

---
#### TAGS