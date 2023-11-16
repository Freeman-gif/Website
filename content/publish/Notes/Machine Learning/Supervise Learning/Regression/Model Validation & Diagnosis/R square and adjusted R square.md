# R square and adjusted R square(class notes 0912)


---
### definition :
- R2 shows how well terms (data points) fit a curve or line. Adjusted R2 also indicates how well terms fit a curve or line, but adjusts for the number of terms in a model. If you add more and more **useless** variables to a model, adjusted r-squared will decrease. If you add more **useful** variables, adjusted r-squared will increase.
- <mark style="background: #FF5582A6;">Adjusted R2 will always be less than or equal to R2</mark>
$R^2:$
$$
R^2=\frac{S S R}{S S T}=\frac{\sum\left(\hat{y}_i-\bar{y}\right)^2}{\sum\left(y_i-\bar{y}\right)^2}=1-\frac{S S E}{S S T}
$$
$R_{a d j}^2:$
$$
1-\frac{S S E /(n-P)}{S S T /(n-1)}=1-\frac{M S E}{M S T}
$$
$\mathbb{\Psi}$
$$
\text { RMSE }=\sqrt{\frac{S S E}{n}}
$$
- $\mathrm{N}$ is the number of points in your data sample.
- $K$ is the number of independent regressors, i.e. the number of variables in your model, <mark style="background: #FF5582A6;">excluding the constant</mark>.

---
### notes:
- When adding more predictors, SSE always decreases, $R^2$ always increases. (YOUR SST would stay the same ), so it can't suggest if the model is <mark style="background: #FF5582A6;">significantly improved or not</mark>
- $R^2$ only measures the reduction in SSE, not the lost in degrees of freedom
- 


---
### use:
- Both R2 and the adjusted R2 give you an idea of how many data points fall within the line of the regression equation. However, there is **one main difference** between R2 and the adjusted R2: R2 assumes that every single variable explains the _variation in the dependent variable. The adjusted R2 tells you the percentage of _variation explained by only the independent variables that actually affect the dependent variable_
---
### problem:
1. $R^2$ increases with every predictor added to a model. As $R^2$ always increases and never decreases, it can appear to be a better fit with the more terms you add to the model. This can be completely misleading.
2. Similarly, if your model has too many terms and too many high-order polynomials you can run into the problem of over-fitting the data. When you overfit data, a misleadingly high $\mathrm{R}^2$ value can lead to misleading projections.




---
#### TAGS