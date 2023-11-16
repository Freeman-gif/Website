# Lasso Regression(L1 Penalty)


---
### Defination and Ideas:
- In Lasso Regression, the cost function for lasso(least absolute shrinkage and selection operator) regression can be written as:
	- $$\sum_{i=1}^{M}(y_i-\hat{y_i})^2=\sum_{i=1}^{M}(y_i-\sum_{j=0}^{p}w_j\times x_{ij})^2 + \lambda \sum_{j=0}^{p}|w_j|$$
	- For some t>0, $\sum_{j=0}^{p}|w_j| < t$
-This type of regluarization not only helps in reducing over-fitting but it can help us in [[Feature Selection]]. 
- 


---

