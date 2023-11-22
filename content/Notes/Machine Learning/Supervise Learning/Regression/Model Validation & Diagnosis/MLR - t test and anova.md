##  Testing:
---
1. Global Anova test and set up
2. t-test for individual slope($\beta$)
3. Generalized Linear / Partial F test 
----

**Gloabal**: 

- "Fit the full model" to the data:
	- Obtain the least squares estimates of $\beta_0$ and $\beta_1\dots$.
	- Determine the error sum of squares, which we denote "SSE $(H_{1}) . "$
- "Fit the reduced model" to the data.:
	- Obtain the least squares estimate of $\beta_0$.
	- Determine the error sum of squares, which we denote "SSE(0)."




$H_0: Y \sim \beta_{0}+\varepsilon_i$(Null Model)
$H_1: Y \sim \beta_{0}+\beta_{1}x_{i_{1}}+\beta_{2}x_{i_{2}}\dots+\beta_{2}x_{p-1}+\varepsilon_i$(The model you choose to fit)

or
$H_0: \beta_{1}=\beta_{2}=\dots=\beta_{p-1}=0$
$H_1:$ at least one $\beta_K \neq 0$, for $k=1, \cdots, p-1$
##### note: at least one predictor $X_{k}$ is a significant predictor of Y


$$
F_{\text {stat }}=\frac{\frac{S S E_{H_{0}}-S S E_{1}}{df_{H_{0}}-df_{H_{1}}}}{\frac{SSE_{H1} }{df_{H_{1}}}}
$$
$$
=\frac{MSR_{H_{1}}}{MSE_{H_{1}}}
$$
###### note: $SSE_{H0} =SST$
**Anova Table**
$$
\begin{array}{lccc} 
& \text { S.S. } & \text { d.f. } & \text { M.S. } \\
\text { Regression } & \text { SSR }=\sum\left(\hat{y}_i-\bar{y}\right)^2 & p-1 & \text { MSR }=\frac{\text { SSR }}{p-1} \\
\text { Error } & \text { SSE }=\sum\left(y_i-\hat{y}_i\right)^2 & n-p  & \text { MSE }=\frac{\text { SSE }}{n-p} \\
\hline \text { Total } & \text { SST } =\sum\left(y_i-\bar{y}\right)^2& n-1 &
\end{array}
$$

Reject $H_{0}$ if $F_{stat}\ge F_{\alpha,df_{1}=p-1,df_{2}=n-p}$ or p-value $\le \alpha$ (if $H_{0}$ is rejected, $H_{1}$ model is significant better than the null model. <mark style="background: #FF5582A6;">it does not provide which predictors are significant</mark>)
### Visual Compare reduced model and Full model
Full model:
![[Pasted image 20230911223534.png]]
Reduced model:
![[Pasted image 20230911223551.png]]
---
## note:

$$
S S R_{\text {-FUlL }}=S S E_{\text {-reduced }}-S S E_{\text { Full }}>0
$$
SSE-Reduced > SSE-FULL, Adding predictors to a linear regression model will always reduces SSE. RMSE always selects the model with most predictors
$$
\text { RMSE }=\sqrt{\frac{S S E}{n}}
$$
Lower values of RMSE indicate a better fit of the model to the data, while higher values indicate a poorer fit. However, by itself, RMSE doesn't tell you whether the model's predictions are biased. It merely indicates the magnitude of the error.


---
## T test for individual coefficient($\beta_{k}$):
### In SLR

<mark style="background: #FF5582A6;">Testing for $\beta_{1}$</mark>:
Testing for feature importance 

Test set up:
$$
H_0: \quad \beta_1=0 \quad \text { v.s. } \quad H_1: \beta_1 \neq 0
$$

$$
\hat{\beta}_1 \sim N\left(\beta_1, \frac{\sigma^2}{s_{x x}}\right)
$$
$$
\frac{\hat{\beta}_1-\beta_1}{\sqrt{\frac{\sigma^2}{s_{x y}}}} \sim N(0,1)
$$


$$
\frac{\hat{\beta}_1-\beta_1}{\sqrt{\frac{M S E}{S x x}}} \sim t(n-2)
$$

$$
t_{\text {stat }}=\frac{\hat{\beta}_1}{\sqrt{\frac{M E E}{S_{x x}}}} \sim t(n-2) \text { when $H_{0}$ is true }
$$
Rejection Rule :
Reject $H_0$ when $\left|t_{s t a t}\right| \geqslant t_{\alpha / 2, n-2}$  or  $p$-value $\leqslant \alpha$.
IF $H_{0}$ is rejected, then X is a significance factor of y

### Global T test:
In MLR, t test for $B_{k}$ to check the importance of $X_{k},k-1,\dots p-1$:


$$
H_0: \beta_k=0 \text { u.s. } H_1: \beta_k \neq 0
$$
In matrix form:
$$
\hat{\beta}_K \sim N\left(\beta_k, \sigma^2\left[(\vec{x} ^r \vec{x})^{-1}\right]_{k+1, k+1}\right)
$$
$$
\vec{b}=\left(\begin{array}{c}
\hat{{\beta}}_0 \\
\hat{\beta}_1 \\
\hat{\beta}_{p-1}
\end{array}\right) \sim \operatorname{Var}(\vec{b})=\sigma^2(\vec{x}^T\vec{x})^{-1}
$$
$$
\implies\left(\begin{array}{cccc}
\operatorname{Var}\left(\hat{\beta}_0\right) & & \cdots \\
\dots& & \operatorname{Var}\left(\hat{\beta}_1\right)& \cdots \\ 
\dots & & \ddots & \ddots \\
\dots & & \dots & \operatorname{Var}\left(\hat{\beta}_{p-1}\right)
\end{array}\right)

$$
$$
\implies\frac{\hat{\beta}_K-\beta_K}{\sqrt{M S E\left[(\vec{x}^T\vec{x})^{-1}\right]_{K+1, k+1}}} \sim t(n-p)
$$

$$
\implies t_{\text {stat }}=\frac{\hat{\beta}_K}{\sec \left(\hat{\beta}_K\right)} \text { where } \operatorname{se}\left(\hat{\beta}_K\right)=\sqrt{\operatorname{MSE}\left[\left(\vec{X}^{\top} \vec{X}\right)^{-1}\right]_{k+1, k+1}}
$$


Reject Ho if $\left|t_{\text {stat }}\right| \geqslant t_{\alpha / 2}, d f=n-p$ or $p$-vale $\leqslant \alpha$


If rejected, $Y$ changes significantly (by $\beta_K$ ) When $X$ increases, given all other predictions stay the same. thus $X_k$ is a significant predictor of $Y$. given all the other predictor $X_1, \cdots, X_{k-1}, X_{k+1}, \cdots X_{p-1}$ in the model.



---
## ANOVA Test
### sequential sum of squares
- **sequential sum of squares**(Type=1):
	-  definition:
		- It is the **reduction in the error sum of squares** (_SSE_) when one or more predictor variables are added to the model.
		- Or, it is the **increase in the regression sum of squares** (_SSR_) when one or more predictor variables are added to the model.
	- note: Sequential sum of squares (Type I) breaks down the <mark style="background: #FF5582A6;">variability</mark> explained by each predictor as they're added to the model. For each predictor, we assess how much additional variance it explains beyond preceding predictors. However, in cases of <mark style="background: #FF5582A6;">multicollinearity</mark>, the order of adding predictors can significantly influence the results.
	- The **<mark style="background: #FF5582A6;">sequential sum of squares</mark>** measures either the reduction in the error sum of squares (SSE) when adding predictors or the increase in the regression sum of squares (SSR) due to the same addition.
	- Theory model:
		
For Test $x_2$ using $F_2$ :
$$
\begin{array}{ll}
H_0: Y \sim X_1 \quad\left(Y_i=\beta_0+\beta_1 x_{i-1}+\varepsilon_i\right) \\
H_1: Y \sim X_1+X_2 \quad\left(Y_i=\beta_0+\beta_1 x_{i, 1}+\beta_2 x_{i, 2}+\varepsilon_i\right)
\end{array}
$$
$$
F_{\text {stat }}=\frac{\frac{S S E_{-H_{0}}-S S E_{-H_1}}{d f_{-H_0}-d f_{-H_1}}}{\frac{S S E_{-H_1}}{d f_{-H_1}}}

$$

- in this example, $SSE_{h_{0}}$ denote to the error sum of squares when $x_{1}$ is the only predictor in the model, $SSE_{h_{1}}$  denotes the  error sum of squares when  $x_{1}$ and  $x_{2}$ are both in the model
- The rejection of indicate the significance of $X_{k}$ given the predictors before it already in the model
###### note:
- all ss are collated in the above way, therefore, changing the order of the predictors in the model will CHANGE THE RESULT!
- $$
\begin{array}{ll}
y \sim x_1+x_2+x_3 & s s\left(x_2\right)=s s\left(x_2 \mid x_1\right) \\
y \sim x_3+x_2+x_1 & \text { ss }\left(x_2\right)=s s\left(x_2 \mid x_3\right) \\
y \sim x_1+x_3+x_2 & s s\left(x_2\right)=s s\left(x_2 \mid x_1, x_3\right)
\end{array}
$$
-  when you change the order, you con see the "importance" of the predictors changes.
- SSE in the table is the SSE of full model ( $y \sim$ all the predictor in the table)
- Summation of $s s\left(x_1\right)+s s\left(X_2\right)+s s\left(X_3\right)+S s E \neq S S T$.
### Partial sum of squares:
- definition:
	- we wish to know what percent of the variation _not_ explained by x1 _is_ explained by x2 and x3. In other words, given x1, what additional percent of the variation can be explained by x2 and x3
- Partial sum of squares(Type = 2):
- $$
\begin{aligned}
& x_1: \operatorname{ss}\left(x_1 \mid x_2, x_3\right) \quad H_0: y=\beta_0+\beta_2 x_3+\beta_3 x_3+\varepsilon &H_1: y=\beta_0+\beta_1 x_1+\beta_2 x_2+\beta_3 x_3 \\
& x_2: \operatorname{ss}\left(x_2 \mid x_1, x_3\right) \\
& x_3: \operatorname{ss}\left(x_3 \mid x_1, x_2\right)
\end{aligned}
$$





---
Summary:
1. t-test for Coefficients
- Test if each coefficient $B_k$ is significantly different from zero.
- The coefficients:
$$
\vec{b}=\left(\begin{array}{c}
\hat{\beta}_0 \\
\hat{\beta}_1 \\
\vdots \\
\hat{\beta}_{p-1}
\end{array}\right)
$$
with variance $\operatorname{Var}(\vec{b})=\sigma^2\left(\vec{x}^T \vec{x}\right)^{-1}$ are assumed normally distributed.
- $t$-statistic formula for $\beta_k$ :
$$
t_{\text {stat }}=\frac{\hat{\beta}_K}{\sec \left(\hat{\beta}_K\right)}
$$
where
$$
\operatorname{se}\left(\hat{\beta}_K\right)=\sqrt{\operatorname{MSE}\left[\left(\vec{X}^{\top} \vec{X}\right)^{-1}\right]_{k+1, k+1}}
$$
- Hypothesis:
- $H_0: \beta_k=0$
- $H_1: \beta_k \neq 0$
- Decision Rule: Reject $H_0$ if
$$
\left|t_{\text {stat }}\right| \geqslant t_{\alpha / 2}, \text { with } d f=n-p
$$
or if $\mathrm{p}$-value $\leqslant \alpha$.

---
2. Partial F-test(Type II)
- Compares the fit of the chosen model to a null model.
- Hypothesis:
- $H_0: Y \sim \beta_0+\varepsilon_i$ (Null Model)
- $H_1: Y \sim \beta_0+\beta_1 x_{i_1}+\beta_2 x_{i_2}+\cdots+\beta_{p-1} x_{i_{p-1}}+\varepsilon_i$ (Chosen Model)
- F-statistic formula:
$$
F_{\text {stat }}=\frac{M S R_{H_1}}{M S E_{H_1}}
$$
- Decision Rule: Reject $H_0$ if
$$
F_{\text {stat }} \geq F_{\alpha, d f 1=p-1, d f 2=n-p}
$$
or if $\mathrm{p}$-value $\leqslant \alpha$.
- Note: Rejecting $H_0$ indicates the chosen model is significantly better than the null model. However, it does not identify which predictors are significant.
---
3. **Type III (Marginal F-test)**:








---
4. Analysis of Variance (ANOVA) in Regression
- Type I (Sequential F-test): Tests the significance of predictors in the order they are entered into the model.
- Type II (Partial F-test): Tests each predictor's significance after controlling for other predictors.
- Type III: Marginal F test, tests the significance of each predictor by considering all possible orders of entry of the predictors into the model. This test is particularly useful when there are interactions and higher-order terms in the model, as it offers an unbiased test for each term.


---
**reference**:
Class notes
https://online.stat.psu.edu/stat501/lesson/6/6.3#:~:text=What%20is%20a%20%22sequential%20sum,are%20added%20to%20the%20model.
https://stats.stackexchange.com/questions/20452/how-to-interpret-type-i-type-ii-and-type-iii-anova-and-manova



