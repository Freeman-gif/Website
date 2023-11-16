# Prediction performance metrics


---
### Use forecasting erros to reflect how well the model works:
#### RMSE(Root Mean Square Error):
$$\sqrt{\frac{1}{n}\sum^{n}_{t=1}(Y_{t}-\hat{Y}_{t})^2 }$$
- Follows the same unit as the original value 
- Prefer models with smaller RMSE 
- penalize the outlier or the larger error, due to the square term. 
###### it's possible RMSE choose a off model since it would take the average of the error term

#### MAE(Mean Absolute Error):
$$\frac {\sum^{n}_{t=1}|Y_{t}-\hat{y_{t}}|}{n}$$
- Same unit as the original value
- prefer models with smaller MAE
- each individual errors takes the same weight in the function

#### MAPE (Mean absolute percentage error):
$$\frac{1}{n} \sum^{n}_{t=1}|\frac{Y_{t}-\hat{Y_{t}}}{Y_{t}}|$$

- MAPE is scale-dependent 
- it work only with data that is<mark style="background: #FF5582A6;"> free from zero values </mark>
- it's asynmetric (same error, contribute different weights in the MAPE)
	- smaller actual value will cost a bigger weight, bigger actual value will cost a smaller weight, which could cost to miss judge the model because of this .
#### SMAPE
---
### Step
A performance metric can only be calculated when there are <mark style="background: #FF5582A6;">atucal value and the predicted value </mark> -> some part of the given data


train, test split the data for model validation 

![[Train-Validation-Test sets]]

---

#### TAGS
#timeseries #performance_metrics 