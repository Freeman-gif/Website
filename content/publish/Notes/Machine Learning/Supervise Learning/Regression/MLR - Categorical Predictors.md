# MLR - Categorical Predictors(09/14)


---
### Notes :
- Y is numerical (values taken from a continuous scale)
<mark style="background: #FF5582A6;">MLR</mark>
- $Y$ is categorical : Classification. <mark style="background: #FF5582A6;">Logistic Regression </mark>
x can be any date type, type of <mark style="background: #FF5582A6;">x doesn't affect the model approach</mark>
---
### Approach:
Dummy encoding in MLR
$$
\begin{aligned}
x=\left\{\begin{array}{l}
c_1 \\
c_2 \\
\vdots \\
c_k
\end{array} \quad \Rightarrow \quad x_1= \begin{cases}0 & \text { obs } \notin c_1 \\
1 & \text { obs } \in c_1\end{cases} \right. \\
x_2= \begin{cases}0 & \text { obs } \notin c_2 \\
1 & \text { obs } \in c_2\end{cases} \\
\vdots
\end{aligned}
$$
- (k-1) dummy variables
- when $x_{1} = x_{2} =\dots=X_{k-1}=0$, the obs is in $C_{k}$
- ex:
	- car brand: 
$$
\begin{array}{|l|l|l|}
\hline \text { Car Brand } & \text { Horsepower } & \text { Price (\$) } \\
\hline \text { Toyota } & 120 & 20,000 \\
\hline \text { Honda } & 110 & 18,500 \\
\hline \text { Ford } & 125 & 19,000 \\
\hline \text { Toyota } & 130 & 21,500 \\
\hline
\end{array}
$$

Dummy Encoding:
For dummy encoding, we'll convert the "Car Brand" categorical variable into separate binary (0 or 1) columns for each brand.
We'll use ' $\mathbf{k - 1}$ ' dummy variables where ' $\mathbf{k}$ ' is the number of categories. This avoids the "dummy variable trap", which can cause multicollinearity issues in MLR.


Price $=\beta_0+\beta_1 \times$ is_Toyota $+\beta_2 \times$ is_Honda $+\beta_3 \times$ Horsepower $+\epsilon$

Using the above principle:
- Toyota: $(1,0)$
- Honda: $(0,1)$
- Ford: $(0,0)$
- If both `is_Toyota` and `is_Honda` are 0, the car is implicitly a Ford.
- The coefficients $\beta_1$ and $\beta_2$ capture the average price differences between Toyota and Ford, and Honda and Ford, respectively, after accounting for horsepower.
- The coefficient $\beta_3$ captures the price change for a one-unit increase in horsepower, holding brand constant.









- class notes(0914, page 4)
---

### t test:
$t$ test for $\beta_k$
$H_0: \beta_K=0 \quad$ vs. $\quad \beta_K \neq 0$

If $H_{0}$ is rejected: the mean value of $C_{k}$ is significant different from the mean Y value of reference level. from the example, if `is_Toyota` has a significant coefficient, it would mean that being a Toyota( of course) has a significant impact on the car's price after accounting for other variables in the model

if  we failed to reject: 
- The category represented by that coefficient does not have a statistically significant difference in the mean outcome when compared to the reference category
- if the coefficient for `is_Toyota` is not statistically significant, it suggests that, after adjusting for other predictors, there's no significant evidence to claim that Toyota cars have a different average price than the reference category (e.g., Ford)

- Not rejecting the null hypothesis can offer insights about the relationship between the categorical predictor and the outcome. It tells us that, at least in the context of the current dataset and model, the specific category doesn't appear to influence the outcome any differently than the reference category doe


---
**F test**:
Given:
$$
Y \sim X \text {-color }+X_2
$$
Type1:
$$
x \text {-color F test for } x \text {-color }
$$
$$
\begin{array}{ll}
H_0: & Y_i=\beta_0+\varepsilon_i \\
H_1: & Y_i=\beta_0+\beta_1 x_{\text {Blue }}+\beta_2 x_{\text {yellow}}+\varepsilon_i
\end{array}
$$
Type2:
$$
H_0: Y_i=\Gamma_0+\beta X_2+\varepsilon_i
$$

$$
H_1: Y_i=\beta_0+\beta_1 x_{\text {Blue }}+\beta_2 x_{\text {yellow }}+\beta X_2+\varepsilon_i
$$

---
### NOtes:
- don't simply drop a dummy variable because your fail to reject(same as relationship)
- MLR is bad on handle too many predictors well
	- more predictors means:
		- MOre data to support estimating
		- more parameters
		- more complex
- When there's a predictors with too many categories:
	- regroup to less
---
#### TAGS