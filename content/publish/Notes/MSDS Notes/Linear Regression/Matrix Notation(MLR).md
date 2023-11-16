### MLR Model(class summary notes 0907and hw3 ):


---
### Model setup:
- A population model for a multiple linear regression model that relates a _y_-variable to _p_ -1 _x_-variables is written as:
$$
y_i=\beta_0+\beta_1 x_{i, 1}+\beta_2 x_{i, 2}+\ldots+\beta_{p-1} x_{i, p-1}+\epsilon_i .
$$

- The model includes p-1 x-variables, but p regression parameters (beta) because of the intercept term $\beta_0$.
---
1. x, y matrix: 
$$
\vec{y}=\left(\begin{array}{c}
y_1 \\
\vdots \\
y_n
\end{array}\right) \quad \vec{x}=\left(\begin{array}{cccc}
1 & x_{1,1}, \cdots, & x_{1, p-1} \\
\vdots & \vdots & & \\
1 & x_{n, 1}, \cdots, & x_{n, p-1}
\end{array}\right)
$$
- (p-1) predictors: $x_{1},\dots,x_{p-1}$
- sample size: n
- example : 
	![[Pasted image 20230925192627.png]]

$$
\underbrace{\left[\begin{array}{c}
y_1 \\
y_2 \\
\vdots \\
y_n
\end{array}\right]}_Y=\underbrace{\left[\begin{array}{cc}
1 & x_1 \\
1 & x_2 \\
\vdots & \vdots \\
1 & x_n
\end{array}\right]}_{=X} \underbrace{\left[\begin{array}{c}
\beta_0 \\
\beta_1
\end{array}\right]}_\beta+\underbrace{\left[\begin{array}{c}
\epsilon_1 \\
\epsilon_2 \\
\vdots \\
\epsilon_n
\end{array}\right]}_{+\epsilon}
$$
---
True Model : $\vec{y}=\vec{x} \vec{\beta}+\vec{\varepsilon}, \vec{\varepsilon} \sim \operatorname{MVN}\left(\overrightarrow{0}, \sigma^2 I_n\right)$

OLSE: $\vec{b}=\left(\begin{array}{c}\hat{\beta}_0 \\ \vdots \\ \hat{\beta}_{p-1}\end{array}\right)=\left(\vec{x}^{\top} \vec{x}\right)^{-1} \vec{x}^{\top} \vec{y}$

![[Pasted image 20230925192939.png]]

----
**GAUSS - MARKOV**: OLSE is a B.L.U.E of $\vec{\beta}$:
- $E(\vec{b})=\vec{\beta}$
- $\operatorname{Var}(\vec{b})=\sigma^2\left(\vec{x}^{\top} \vec{x}\right)^{-1}$
- Model / Fitted line: $\quad \hat{\vec{y}}=\vec{x} \cdot \vec{b}=H \vec{y}$
- where H = $\vec{x}\left(\vec{x}^{\top} \vec{x}\right)^{-1} \vec{x}^{\top}$

- Residuals: $\vec{e}=\vec{y}-\hat{\vec{y}}=\left(I_n-H\right) \vec{y}$
- Estimate of $\sigma^2:$MSE $=\frac{S S E}{n-P}=\frac{\vec{e}^{\top} \vec{e}}{n-P}$
- --
### some notes: 
- Hat matrix is powerful!






---
### resources: 
- class notes
- https://online.stat.psu.edu/stat501/lesson/5/5.4
- textbook
