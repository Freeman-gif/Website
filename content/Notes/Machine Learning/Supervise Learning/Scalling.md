# Scalling


---
#### Standard scalar:
Subtract the mean and scale by the sttddev

#### Minmax scaling:
transforms each value to a given range

#### Nomralization: 

#### Log/ power transformation:
- non linear 



---

### How to scale data:
- Use the Training data to find the scaling parameters 
	- Estimates of mean and variance
- The , apply the transformation 
#### When to scale data:
- When using linear model with regulariztion
- When using linear models without regularization
	- Model converge faster
	- Don't need to scale if need to interpret in original units
- When using neural networks
	- Gradient deseent 
- When using nearest-neighbor type algorithms

---
### Regularized regression
Data : $(X_{i},y_{i})$
	- i in indexes of n observations
Linear model: $\hat{y}=\beta_0+\sum_{j}x_{j}\beta_{j}$
	- j indexes over p parameters (covariates)
Loss: 


---
#### TAGS