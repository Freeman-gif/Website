# Residulas 


---
### Notes and Ideas:

**Defination**:
- $$e_i=y_i-\hat{y}_{i}\text {   In.Sample.Error}$$
- Residuals in a statistical or machine learning model are the differences between observed and predicted values of data. They are a diagnostic measure used when assessing the quality of a model. They are also known as errors 
- $e_{i}$ is an estimation of $\epsilon_{i}$ =0 . unbiased $E(e_{i})=0$
- Note:
	1. $e_i$ is an unbiased estimator of $E\left(\varepsilon_i\right)=0$
	2. Sampling distribution of $e_i$:
		- Normally distributed
		- $\begin{aligned}
& E\left(e_i\right)=0 \\
& \operatorname{Var}\left(e_i\right)=\sigma^2\left[1-\frac{1}{n}-\frac{\left(x_i-\bar{x}\right)^2}{s_{x x}}\right]
\end{aligned}$
		
		


		 
$$
\text { bias }=E\left(y_0\right)-\hat{y}_0 \sim N\left(0, \sigma^2\left(\frac{1}{n}+\frac{\left(x_0-\bar{x}\right)^2}{S_{x x}}\right)\right)
$$


$$
\begin{aligned}
& \varepsilon_i=Y_i-\left(\beta_0+\beta_1 x_i\right) \\
& \varepsilon_i \sim N\left(0, \sigma^2\right) \\
& e_i=Y_i-\left(\hat{\beta}_0+\hat{\beta}_1 x_i\right)
\end{aligned}
$$

**Out of Sample Error:**
given $x=x_0$ (new data)
$$
\begin{aligned}
& \hat{y}_0=\hat{\beta}_0+\hat{\beta}_1 x_0 \\
& e_0=y_0-\hat{y}_0
\end{aligned}
$$
properties:
Sampling distribution of $e_0$:
- Normally Distribution
- $E\left(e_0\right)=0$
- $\operatorname{Var}\left(e_0\right)=\sigma^2\left[1+\frac{1}{n}+\frac{\left(x_0-\bar{x}\right)^2}{-s_{x x}}\right]$
$$
\hat{y}_0 \mid x_0 \sim N\left(\beta_0+\beta_1 x_0, \sigma^2\left(1+\frac{1}{n}+\frac{\left(x_0-\bar{x}\right)^2}{\sum_{i=1}^n\left(x_i-\bar{x}\right)^2}\right)\right)
$$

**Use** :
- Residuals are importatant when determining the quality of a model. We can examine residuals in terms of their mahnitude and/ or whether they form a parttern
- Where the residuals are all 0, the model predicts perfectly. THe further residuals are from 0, the less accurate the model. In the case of [[Linear Regression]], the greater the sum of squared residucals, the smaller the r-squared tatistic, all else being equal
- Where the average residual is not 0, it implies that the model is systematically biased(i.e., consistently over-or under-predicting)

**Residual plot**:
-   In the case of simple linear regression (regression with 1 predictor), we set the **predictor** as the x-axis and the residual as the y-axis
-   In the case of multiple linear regression (regression with >1 predictor), we set the **fitted value** as the x-axis and the residual as the y-axis


**Residcual function**:
$$e_{i} = y_{i}-\hat{y}$$
$$ =y - (\hat{b_0}+\hat{b_1}x_1+\hat{b_2}x_2+......+\hat{b_n}x_n)$$



---

### Properties:
1. mean of the residuals should be 0
2. Variance of e $$Var(e) = Var(Y-X\beta)$$ $$=Var(Y-X(X'X)^{-1}X'Y)$$ $$=Var(I-X(X'X)^{-1}X')Y$$ $$= (I-X(X'X)^{-1}X')\sigma^2$$
3. Non-independence, Scine $Cov(e_{i},e_{j})\ne 0$
4. $E(e_{i})$ is normally distributed
5. $E(e_{i})=0$
For simple linear regression(2D):


---
#### TAGS
#Linear_regression