# Linear Regression in ML


---
### Review of Linear Model:
1. $X, y, \beta$ are matrices or vectors.
2. A row or column of a matrix will use a subscript:
	- $x_{i j}$ is a scalar, the ith row and jth column of $X$
	- $X_i$. is a vector, the ith row of $X$
	- $X_{\cdot j}$ is a vector, the jth column of $X$
3. Parameters will typically be Greek symbols: $\beta, \gamma, \lambda, \sigma, \mu$
4. Estimates will be Greek symbols wearing a hat: $\hat{\beta}, \hat{\sigma}, \hat{\mu}$
5. $P(Y=1 \mid X)$ is the probability that $Y=1$ given $X$, where:
	- X, Y are random variables
6. $\mathcal{L}$ represents either a loss function, or the likelihood function
	- $\ell$ represent the log-likelihood function


X(n by p+1), features with columns of list
Y(n by 1), target variable
B(p+1 by 1) coefficient, parameters
Y = XB + E 



---

### Training linear model means finding optimal coefficients :
Finding optimal $\beta$ amounts to find vector $\hat{\beta}$ that minimizes the loss function $\mathcal{L}$, which is the sum of squared error:
$$
S S E=\sum_{i=1}^n\left(y_i-\hat{y}_i\right)^2
$$

which is equivalent to:
$$
\mathcal{L}(\beta)=\sum_{i=1}^n\left(y_i-x_i \beta\right)^2=(y-X \beta)^T(y-X \beta)
$$
---
### Finding $\hat{\beta}$
by taking the derivative of our loss function and setting it equal to zero


$$
\hat{\beta}=\left(X^T X\right)^{-1} X^T y
$$

---
#### TAGS