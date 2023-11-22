# Linear Regression Models Main


---
### Notes and Ideas:
- [[Simple Linear Regression]]
- [[Mutiple Linear Regression]]
- [[Piecewise Regression]]
- [[Standarized Regression]]
- [[Weighted Leaset Squares Regression]]
- [[Polynomial Regression]]
- [[LoweSS(Local Regression)]]
- [[Least Mean Square Regression]]
- [[Standarized Regression]]
- [[Robust Regression]]
- [[General Linear Model]]
- [[Non-Linear Model]]:
	- [[None Linear Regression]]

---
### Definition:
Linear Regrssion Means [[Linear Algebra Basic Guide]] of features
**Genral Linear Model**










**Funciton**
$$\hat{y} = w[0]\times x[0] + w[1]\times x[1]+...+ w[n]\times x[n] + b$$
- From the euqation above, we have shown the lienar model based on the n number of features. Considering only a subject feature as us probably already have understood that $w[0]$ will be the slope and the b will represent the intercept.
- **Cost Function**:
	- We are looing for optimizing $w$ and $b$ such taht it minimizes the cost function which 
		- $$\sum_{i=1}^{M}(y_i-\hat{y_i})^2=\sum_{i=1}^{M}(y_i-\sum_{j=0}^{p}w_j\times x_{ij})^2 $$ 
		- Assumed that the dataset has M instances and p features.
	- **Cost Function**:
	- We are looing for optimizing $w$ and $b$ such taht it minimizes the cost function which 
		- $$\sum_{i=1}^{M}(y_i-\hat{y_i})^2=\sum_{i=1}^{M}(y_i-\sum_{j=0}^{p}w_j\times x_{ij})^2 $$ 
		- Assumed that the dataset has M instances and p features.

	**Linear Regression Assumptions**:
	 - Ordinary Leaset Square:
	  
- Linear Relationship between predictors and the target variable, meaning the pattern must in the form of a straight-line(or a [[hyperplane]] in case of multiple linear regressions)
	- This assumption is validated if there is _no_ discerning, nonlinear pattern in the residual plot. Let’s consider the following example
	- Example:
		- In the above case, the assumption is violated since a U-shape pattern is apparent. In other words, the true relationship is nonlinear.
		![[Pasted image 20220613140108.png]]
- Homoscedaticity, i.e, constant [[variance]] of the [[Residulas]]
	- This assumption is validated if the residuals are scattered evenly (about the same distance) with respect to the zero-horizontal line throughout the x-axis in the residual plot.
	- Example:
		- In the below case, the assumption is violated since the variance is getting smaller on larger fitted values
		![[Pasted image 20220613135822.png]]
	- Independenet observations, this is actually equivalent to independent [[Residulas]]
		- This assumption is validated if there is _no_ discerning pattern between several consecutive residuals in the residual plot.
		- Example:
		- In the below case, the assumption is violated since there are discerning patterns (both are linear with a negative slope) between consecutive residuals
		![[Pasted image 20220613140206.png]]
	- Normality of Residuals, i.e., the residuals follow the normal distribution
 **Find the Best Model**:
 - see [[Model Selection]]
 - Apply Penalty(Ridge and Lasso regression are some of the simple techniques to reduce [[model complexity]] and prevent [[over-fitting]] which may result from simple linear regression ):
	  - ![[Ridge Regression]]
	  - ![[Lasso Regression]]
	
	
	  




---

### Key words:

---
#### TAGS