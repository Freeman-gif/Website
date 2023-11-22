# Simple Linear Regression


---
## Notes and Ideas:
**Model Setup**:
True Model:
$$Y = \beta_{o}+\beta_{1}x_{i}+\epsilon_{i}, i=1,\dots,n$$

- $y_{i}$: observed value of the response variable Y of the observation $i$
- $x_{i}$: observed value of the independent variable x of the observation $i$
- n: sample size
- $\beta_{0}$ and $\beta_{1}$: unknown fixed coeffcient parameters -- constant
- $\epsilon_{i}$: Random Error term -cosntant

simple: only one explanatory variable

Linear: linear in the parameters $\beta$

The slope is denoted by $\beta_{1}$ and the interecpt by $\beta_{0}$

##### note: linear: $y_{i}$ is linear to parameter $\beta_{0}$ and $\beta_{1}$ 
![[Linear vs Non Linear]]
---

## Model Assumption:



- $\epsilon_{i}$ is Random error term:
	- **Estimation Assumptions**:
		- E($\epsilon_{i}$)=0
		- Var($\epsilon_{i}$) = $\sigma^2$, for all i. (The errors have ==constant variance==) unknown fixed parameter
		- Cov($\epsilon_{i}$,$\epsilon_{j}$) = 0. (no correlation between errors for each observations, The errors are independent of each other)
		- Classic Assumption([[Model Inference]]):$$\epsilon_{i}\sim^{iid} N(0,\sigma^2)$$ ^The errors are normally distributed.
- $x_{i}$ is also a [[fixed]] value affect to $y$
- $Y_{i}\to N(\beta_{0}+\beta_{1}x_{i}+\epsilon_{i},\sigma^2)$
	- $Y_{i} = E(\beta_{0}+\beta_{1}x_{i}+\epsilon_{i})$=$\beta_{0}+\beta_{1}x_{i}$
	- $Var(Y_{i}) = Var(\beta_{0}+\beta_{1}x_{i}+\epsilon_{i}) = Var(\epsilon_{i}) = \sigma^2$ -> estimate $\sigma^2$
	- $Cov(y_{i},y_{j})=0$
![[Pasted image 20230822225442.png]]


---
## Model Estimation:
### Goal:
$$E(Y_{i})=\beta_{0} + \beta_{1}x_{i}$$
$$Var(Y_{i})=\sigma^2$$
#### MLE Approach:
$Y_{i} \sim N(b_{0}+b_{{1}}x_{i},\sigma^2)$
![[Pasted image 20230906162634.png]]
![[Pasted image 20230906162724.png]]
![[Pasted image 20230906162739.png]]

#### Ordinary Least Square Estimate(OLSE)
find $\hat{\beta} ,\hat{\beta_{1}}$ that minimize the sum of squared
errors:

$$SSE = S(\beta_{0},\beta_{1}) = \sum(y_{i}-\beta_{0}-\beta_{1}x_{i})^2$$


**Note:**
$$\operatorname{cov}(x, y)=\frac{\sum_{i=1}^n\left(x_i-\bar{x}\right)\left(y_i-\bar{y}\right)}{n-1}=\frac{S_{x y}}{n-1}$$
$$s_x^2=\frac{\sum_{i=1}^n\left(x_i-\bar{x}\right)^2}{n-1}=\frac{S_{x x}}{n-1}$$

$$\beta_1=\frac{\operatorname{cov}(x, y)}{s_x^2}$$

$$S_{x x}=\sum_{i=1}^n\left(x_i-\bar{x}\right)^2=\sum_{i=1}^n x_i^2-\frac{\left(\sum_{i=1}^n x_i\right)^2}{n}$$
$$S_{x y}=\sum_{i=1}^n\left(x_i-\bar{x}\right)\left(y_i-\bar{y}\right)=\sum_{i=1}^n x_i y_i-\frac{\left(\sum_{i=1}^n x_i\right)\left(\sum_{i=1}^n y_i\right)}{n}$$
$$S_{y y}=\sum_{i=1}^n\left(y_i-\bar{y}\right)^2=\sum_{i=1}^n y_i^2-\frac{\left(\sum_{i=1}^n y_i\right)^2}{n}$$
<mark style="background: #FF5582A6;">Important</mark> :
$$
\hat{\beta}_0=\bar{y}-\hat{\beta}_1 \bar{x}
$$

$$
\hat{\beta_1}=\frac{s_{x y}}{s_{x x}}=\frac{\sum\left(x_i-\bar{x}\right)\left(y_i-\bar{y}\right)}{\sum\left(x_i-\bar{x}\right)^2}
$$ 
---

**Example:**
----
Example 1.1 Continued - Coffee Sales and Shelf Space
For the coffee data, we observe the following summary statistics in Table 2.
Table 2: Summary Calculations - Coffee sales data
From this, we obtain the following sums of squares and crossproducts.

$\sum x=72 \quad \sum y=6185 \quad \sum x^2=504 \quad \sum x y=39600 \quad \sum y^2=3300627$

$
\begin{array}{cccccc}
\text { Week } & \text { Space }(x) & \text { Sales }(y) & x^2 & x y & y^2 \\
\hline 1 & 6 & 526 & 36 & 3156 & 276676 \\
2 & 3 & 421 & 9 & 1263 & 177241 \\
3 & 6 & 581 & 36 & 3486 & 337561 \\
4 & 9 & 630 & 81 & 5670 & 396900 \\
5 & 3 & 412 & 9 & 1236 & 169744 \\
6 & 9 & 560 & 81 & 5040 & 313600 \\
7 & 6 & 434 & 36 & 2604 & 188356 \\
8 & 3 & 443 & 9 & 1329 & 196249 \\
9 & 9 & 590 & 81 & 5310 & 348100 \\
10 & 6 & 570 & 36 & 3420 & 324900 \\
11 & 3 & 346 & 9 & 1038 & 119716 \\
12 & 9 & 672 & 81 & 6048 & 451584
\end{array}$

$$
\begin{gathered}
S_{x x}=\sum(x-\bar{x})^2=\sum x^2-\frac{\left(\sum x\right)^2}{n}=504-\frac{(72)^2}{12}=72 \\
S_{x y}=\sum(x-\bar{x})(y-\bar{y})=\sum x y-\frac{\left(\sum x\right)\left(\sum y\right)}{n}=39600-\frac{(72)(6185)}{12}=2490 \\
S_{y y}=\sum(y-\bar{y})^2=\sum y^2-\frac{\left(\sum y\right)^2}{n}=3300627-\frac{(6185)^2}{12}=112772.9
\end{gathered}
$$

From these, we obtain the least squares estimate of the true linear regression relation $\left(\beta_0+\beta_1 x\right)$.

$$
b_1=\frac{S_{x y}}{S_{x x}}=\frac{2490}{72}=34.5833
$$

$$
\begin{gathered}
b_0=\frac{\sum y}{n}-b_1 \frac{\sum x}{n}=\frac{6185}{12}-34.5833\left(\frac{72}{12}\right)=515.4167-207.5000=307.967 \\
\hat{y}=b_0+b_1 x=307.967+34.583 x
\end{gathered}
$$


---
## Gauss-Markov Theorm:


OLSE is the<mark style="background: #FF5582A6;"> Best Linear Unbiased Estimators</mark> of $\beta_{0}, \beta_{1}$:

- $\begin{aligned} \text {Unbiused: } & E\left(\hat{\beta}_0\right)=\beta_0 \\ & E\left(\hat{\beta}_1\right)=\beta_1\end{aligned}$
- Linear: $\hat{\beta}_0$ and $\hat{\beta}_1$ are linear combinations of $y_1, \cdots, y_n$.
- Best: OLSE has the smallest variance among all the linear estimators of $\beta_0$ and $\beta_1$
### Proof:
$$
\begin{aligned}
& E\left(\hat{\beta}_0\right)=\underline{\underline{\beta_0}} \\
& \operatorname{Var}\left(\hat{\beta}_0\right)=\sigma^2\left(\frac{1}{n}+\frac{\bar{x}^2}{s_{x x}}\right) \\
& E\left(\hat{\mu}_1\right)=\underline{\beta_1} \\
& \operatorname{Var}\left(\hat{\mu}_1\right)=\frac{\sigma^2}{s_{x x}}
\end{aligned}
$$

from OLSE we got:
$$
\hat{\beta}_1=\frac{\sum\left(x_i-\bar{x}\right)\left(y_i-\bar{y}\right)}{\sum\left(x_i-\bar{x}\right)^2}
$$
=> ![[Pasted image 20230906192934.png]]
=>![[Pasted image 20230906192952.png]]
$
=\sum k_i y_i
$
##### note:
(i) $\sum k_i=0$
(ii) $\Sigma k i^2=\frac{1}{s_{x x}}$
(iii) $\sum K_i X_i=1$
Thus we have 
$$
\begin{aligned}
E\left(\hat{\beta}_1\right) & =E\left(\sum k_i y_i\right) \\
& =\sum k_i E\left(y_i\right) \\
& =\sum k_i\left(\beta_0+\beta_1 x_i\right) \\
& =\beta_0 \sum k_i{\text{(given that $\sum k_i=0$)}}+\beta_1 \sum k_i x_i{\text{(given that $\sum K_i X_i=1$)}} \\
& =\beta_1
\end{aligned}
$$
for variance $\hat{\beta_{1}}$
$$
\begin{aligned}
& \operatorname{Var}\left(\hat{\beta_1}\right)=\operatorname{Var}\left(\sum k_i y_i\right) \\
& =\sum k_i^2 \operatorname{Var}\left(y_i\right)=\sum k_i{ }^2 \sigma^2 \\
& =\frac{\sigma^2}{S_{x x}}
\end{aligned}
$$

From OLSE we got:
$$
\begin{aligned}
& \hat{\beta}_0=\bar{y}-\hat{\beta}_1 \bar{x} \\
& E\left(\hat{\beta}_0\right)=E\left(\bar{y}-\hat{\beta}_1 \bar{x}\right) \\
& =E(\bar{y})-\bar{x} E\left(\hat{\beta}_1\right)
\end{aligned}
$$ 
-(a)
since $y_{i}\sim N(\beta_{0}+\beta_{1}x_{i}, \sigma^2)$
$$
\begin{aligned}
E(\bar{y}) & =E\left(\frac{\sum y_i}{n}\right) \\
& =\frac{1}{n} \sum E\left(y_i\right) \\
& =\frac{1}{n} \sum\left(\beta_0+\beta_1 x_i\right) \\
& =\frac{1}{n}\left(n \beta_0+\beta_1 n \bar{x}\right) \\
& =\beta_0+\beta_1 \bar{x}
\end{aligned}
$$
Thus we plug back to (a)
$$
\implies\beta_0+\beta_1 \bar{x}-\bar{x} \cdot \beta_{1}\\
$$
$$
=\beta_{0}
$$
For variance of $\hat{\beta_{0}}$:
$$
\begin{aligned}
\operatorname{Var}\left(\hat{\beta}_0\right) & =\operatorname{Var}\left(\bar{y}-\bar{x} \hat{\beta}_1\right) \\
& =\operatorname{Var}\left(\frac{1}{n} \Sigma y_i-\bar{x} \sum k_i y_i\right) \\
& =\operatorname{Var}\left(\sum\left(\frac{1}{n}-k_i \bar{x}\right) y_i\right) \\
& =\sum\left(\frac{1}{n}-k_i \bar{x}\right)^2 \sigma^2 \\
& =\sigma^2\left(\frac{1}{n}+\frac{\bar{x}^2}{S_{x x}}\right)
\end{aligned}
$$
The key assumptions (conditions) that need to be satisfied for the Gauss-Markov theorem to hold:
1. Linearity in Parameters: The regression model is linear in parameters. In the context of a simple linear regression, this can be represented as $Y_i=\beta_0+\beta_1 X_i+u_i$, where $Y_i$ is the dependent variable, $X_i$ is the independent variable, and $u_i$ is the error term.
2. Random Sampling: The data (observations) are obtained using a random sampling process.
3. No Perfect Collinearity: For the multiple regression case, no independent variable is a perfect linear function of other explanatory variables. In simple linear regression, this is trivially satisfied since there's only one independent variable.
4. Zero Conditional Mean: The expected value of the error term, given the independent variable(s), is zero. Mathematically, this is represented as $E\left(\epsilon_{i} \mid X_i\right)=0$. This implies that any variation in the error term is not systematically related to the independent variable(s).
5. Homoscedasticity: The variance of the error term is constant across all values of the independent variable(s). Formally, $\operatorname{Var}\left(\epsilon_{i} \mid X_i\right)=\sigma^2$. This means that the spread of the residuals remains constant as the value of the independent variable(s) changes.


---
## Fitted Value:
$\hat{Y}_{i}$ is the<mark style="background: #FF5582A6;"> fitted value</mark> and $x_{i}$ is from the sample 
- $\bar{y}_{i}$ is an unbiased estimation of $E(y_{i})$
- When talking about $\hat{y_{i}}$ is an "estimation" of $y_{i}$, we are talking about the distribution of the biased/error/residual = $y_{i}-\hat{y_{i}}$ 
- $\beta_1=\frac{\sum_{i=1}^n\left(x_i-\bar{x}\right)\left(y_i-\bar{y}\right)}{\sum_{i=1}^n\left(x_i-\bar{x}\right)^2}=\frac{S_{x y}}{S_{x x}}$
- $\beta_{0}=\bar{y}-\hat{\beta}_1 \bar{x}=\frac{\sum_{i=1}^n y_i}{n}-b_1 \frac{\sum_{i=1}^n x_i}{n} .$

![[Pasted image 20230906200255.png]]
<mark style="background: #FF5582A6;">NOTE</mark>:
- $x_{0},\hat{y_{0}} = \beta_0+\hat{\beta}_1 x_0$ mean out of sample prediction
- (1) $\hat{y}_i$ is an estinate of $E\left(Y_i\right)$ unbiased.
Hint: $E\left(\hat{Y}_i\right) \stackrel{?}{=} E\left(Y_i\right)$
- (2) when $\hat{y}_i$ is an "prediction" / "Estimation" of $Y_i$, we are talking about the sampling distribution of
$$
e_1=y_i-\hat{y}_i
$$

---
## Residuals 
![[Residulas]]

---
## Estimate $\sigma^{2}= Var(\epsilon_{i})$
### Idea: for $Var(x)$:
a sample from $x=x_1, \cdots, x_n$
$$
S^2=\frac{\sum\left(x_i-\bar{x}\right)^2}{n-1}
$$
### Calculate SSE
$$
\text { SSE }=\Sigma\left(e_i-\bar{e}\right)^2=\Sigma e_i^2
$$

###### hint:  
$$
\bar{e}=0
$$
$$
\Sigma\left(e_i\right)=\Sigma\left(y_i-\hat{y}_i\right)
$$
$$
={\sum\left(y_i-\hat{\beta}_0-\hat{\beta}_1 x_i\right)}
$$
(with $\hat{\beta_{0}}=\bar{y}-\hat{\beta}_1 \bar{x}$)

Thus we have:
$$
\begin{aligned}
\text { Thm: } & \frac{\text { SSE }}{\sigma^2} \sim \chi^2(n-2) \\
& E\left(\frac{S S E}{\sigma^2}\right)=n-2 \\
& \left.E\left(\frac{S S E}{n-2}\right)\right)=\sigma^2
\end{aligned}
$$

<mark style="background: #FF5582A6;">**Mean Square Error(MSE)**</mark>:
MSE $=\frac{S S E}{n-2}=\frac{\sum e i^2}{n-2}$ is an unbiased estimate of $\sigma^2$.

---
## Testing:
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



 <mark style="background: #FF5582A6;">Anova and F test in SLR</mark>
<mark style="background: #FFB86CA6;">${F \text { test }} \Leftrightarrow t \text { test for } \beta_1$</mark>
<mark style="background: #ADCCFFA6;">reason:</mark>
$$
\begin{gathered}
F_{\text {stat }}=\frac{M S R}{M S E}=\frac{\sum\left(\hat{y}_i-\bar{y}\right)^2}{M S E} \\
=\frac{\hat{\beta}_1^2 \sum\left(x_i-\bar{x}\right)^2}{M S E}=\left(\frac{\hat{\beta}_1}{\sqrt{M S E / S_{x x}}}\right)^2=t_{\text {stat }}^2 \\
F_{d f_1=1, d f_2=n 2}=t_{d f=n 2}^2
\end{gathered}
$$







$$
\begin{matrix}
\text{Total Sum of Squares in Y }&  & \text{Regression Sum of Squares}  & + & \text{Error Sum o fSquares} \\
SST & = & SSR & + & SSE \\
\Sigma\left(y_i-\bar{y}\right)^2 & = & \sum\left(\hat{y}_i-\bar{y}\right)^2 & + & \sum\left(y_i-\hat{y}_i\right)^2
\end{matrix}

$$

###### Hint: $\hat{y} = \bar{y}$ in SLR, because sum of error is 0. use $\beta_{0}=\bar{y}-\beta_{1}\bar{x}$

**Anova Table**
$$
\begin{array}{lccc} 
& \text { S.S. } & \text { d.f. } & \text { M.S. } \\
\text { Regression } & \text { SSR } & 1 & \text { MSR }=\frac{\text { SSR }}{1} \\
\text { Error } & \text { SSE } & n-2 & \text { MSE }=\frac{\text { SSE }}{n-2} \\
\hline \text { Total } & \text { SST } & n-1 &
\end{array}
$$
$$
F_{\text {stat }}=\frac{M S R}{\text { MSE }}
$$

<mark style="background: #FF5582A6;">NOTE:</mark>
- $E(M S E)=\sigma^2$
- $\begin{aligned} & E(\text { MSR })=E\left(\sum\left(\hat{y_i}-\bar{y}\right)^2\right) \\ & =E\left(\sum\left(\hat{\beta}_0+\hat{p}_1 x_i-\bar{y}\right)^2\right) \\ & \bar{\beta_{0}}=\qquad\left(\bar{y}-\bar{x} \hat{p}_1\right) \\ & =\left(E\left(\begin{array}{c} \\ \hat{\beta}_1^2\end{array}\right)\left(x_i-\bar{x}\right)^2\right)\end{aligned}$
=> 
$E(\hat{\beta_{1}}^2)$ = $\operatorname{Var}\left(\hat{\beta}_1\right)+\left[E\left(\hat{\beta}_1\right)\right]^2$
$=\sigma^2+\beta_1^2 \Sigma\left(x_i-\bar{x}\right)^2$
when $H_{0}: \beta_{1}=0: E(MSR)=E(MSE)$
When $H_0: \beta_1 \neq 0: E(M S R)>E(M S E)$
- F test and t test are equavilent in SLR -> p-value of F = p-value of t, the test statistic relationship between t-test and F-test in the context of SLR is $t^2=F$
F test is used to ocmpare a "shorter" model and a "longer model":

<mark style="background: #FF5582A6;">**Testing set up:**</mark>
$H_0: Y \sim X_1$
$H_1: Y \sim x_1+x_2$

or
$H_0: Y \sim X_1+X_2$
$H_1: Y \sim x_1+x_2+x_3+x_4$

==IN SLR==: 
$$
H_0: \beta_1=0 \quad \text { v.s. } H_1: \beta_{1}\neq 0
$$
<=>
$H_0: Y_i=\beta_0+\varepsilon_i$ <mark style="background: #FF5582A6;">Reduced Model & Null Model</mark> $\hat{y}=\hat{\beta_{0}},SSR=\sum\left(\hat{y}_i-\bar{y}\right)^2$

$H_1: r_i=\beta_0+\beta_1 x_i+\varepsilon_i$ <mark style="background: #FF5582A6;">Full model</mark>

$$
F_{\text {stat }}=\frac{M S R_{\text {-FuLL }}}{M S E_{- \text {FuLL }}}=\frac{\frac{S S R_{- \text {Full }}}{(1)}}{\frac{S S E_{- \text {Full }}}{(n-2)}}

$$
$$
=\frac{\frac{S S T_{\text {-Full }}-S S E_{- \text {Full }}}{1}}{\frac{\text { SSE -full }}{n-2}}
$$

##### note:
$$
S S R_{\text {-FUlL }}=S S E_{\text {-reduced }}-S S E_{\text { Full }}>0
$$
SSE-Reduced > SSE-FULL, Adding predictors to a linear regression model will always reduces SSE. RMSE always selects the model with most predictors
$$
\text { RMSE }=\sqrt{\frac{S S E}{n}}
$$
Lower values of RMSE indicate a better fit of the model to the data, while higher values indicate a poorer fit. However, by itself, RMSE doesn't tell you whether the model's predictions are biased. It merely indicates the magnitude of the error.

---
## R-squared

Coefficient of Determination to measure the goodness of fit of a model.
$$
R^2=\frac{S S R}{S S T}=1-\frac{S S E}{S S T}
$$
The proportion of the variation in Y contained 

<mark style="background: #FF5582A6;">note:</mark>
1. $R^2=r_{x y}^2=\left(\frac{s_{x y}}{\sqrt{s_{x x}} \sqrt{s_{y y}}}\right)^2$ in SLR
2. $0 \leqslant R^2 \leqslant 1$


---
## Prediction  intervals for predictions

let x = $x_{0}$
point prediction $\hat{y}_0=\hat{\beta}_0+\hat{\beta}_1 x_0$

Estimate $\left.E(Y)\right|_{x=x_0} \quad$ "Estimate" $Y \mid x=x_0$
$\text { Bias }=\left.E(Y)\right|_{x=x_0}-\hat{Y}_0 \quad \text { "Bias" }=Y_0-\hat{Y}_0$

<mark style="background: #FF5582A6;">Confidence interval for estimating $\left.E(y)\right|_{x=x_0}$</mark>
	1. $\hat{Y}_0 \sim N\left(E\left(Y_0\right), \operatorname{Var}\left(\hat{y}_0\right)\right)$
	2. $$
\begin{aligned}
\operatorname{Var}\left(\hat{y}_0\right) & =\operatorname{Var}\left(\hat{\beta}_0+\hat{\beta}_1 x_0\right) \\
& =\operatorname{Var}\left(\bar{y}-\hat{\beta}_1 \bar{x}+\hat{\beta}_1 x_0\right) \\
& =\operatorname{Var}\left(\bar{Y}+\left(x_0-\bar{x}\right) \hat{\beta}_1\right) \\
& =\operatorname{Var}(\bar{y})+\left(x_0-\bar{x}\right)^2 \operatorname{Var}\left(\hat{\beta}_1\right) \\
& =\frac{\sigma^2}{n}+\left(x_0-\bar{x}\right)^2 \cdot \frac{\sigma^2}{S_{x x}}
\end{aligned}$$


Thus we have  $\hat{y}_0 \sim N\left(E\left(y_0\right), \quad \sigma^2\left(\frac{1}{n}+\frac{\left(x_0-\bar{x}\right)^2}{S_{x x}}\right)\right)$
=> $\frac{\hat{y}_0-E\left(y_0\right)}{\sqrt{\operatorname{MSE}\left(\frac{1}{n}+\frac{\left(x_0-\bar{x}\right)^2}{S x x}\right)}} \sim t(n-2)$

$100 \times(-\alpha) \%$ c. I . for $E\left(y_0\right)$ is
$$\hat{Y}_0 \pm t \alpha_{\gamma_2}, d f=n-2 \cdot \sqrt{\operatorname{MSE}\left(\frac{1}{n}+\frac{\left(x_0-\bar{x}\right)^2}{S_{x x}}\right)}$$
![[Pasted image 20230906213508.png]]

Confident Interval for estimation of Bias $=Y_0-\hat{Y}_0=\beta_0+\beta_1 x_0+\varepsilon_0-\left(\hat{\beta}_0+\hat{\beta}_1 x_0\right)$<mark style="background: #ADCCFFA6;">compare to bias mean
$E(y_{0})-\hat{y}_{0}$ = $\left(\beta_0+\beta_1 x_0\right)-\left(\hat{\beta}_0+\hat{\beta}_1 x_0\right)$</mark>

$$
Y_0-\hat{y}_0 \sim N\left(0, \sigma^2\left(\frac{1}{n}+\frac{\left(x_0-\bar{x}\right)^2}{S_{x x}}\right)+\sigma^2\right)
$$

$$
\frac{Y_0-\hat{y}_0}{\sqrt{\operatorname{MSE}\left(1+\frac{1}{n}+\frac{\left(x_0-\bar{x}\right)^2}{S_{x x}}\right)}} \sim t(n-2)
$$
Prediction Interval for $Y_{0}$

$$
\hat{y}_0 \pm t_{\alpha / 2}, d f=n-2 \sqrt{M S E\left(1+\frac{1}{n}+\frac{\left(x_0-x\right)^2}{S_{x x}}\right)}
$$ 
 


---
SEL Model Assumption Diagnosis:





---
Example 
![[Pasted image 20230906214709.png]]
![[Pasted image 20230906215345.png]]
![[Pasted image 20230906224601.png]]
![[Pasted image 20230907085337.png]]
#### TAGS