# variance

[[standard deviation]]
---
### Notes and Ideas:

The Variance of the distribution is  ==the mean of the squared difference from the mean==.

[[Discrete Random Variables]]
The variance of a discrete random variable is given by:
$$\sigma^{2}= Var(X) = \sum\limits (x_{i}- \mu)^2f(x_i)$$
==The formula means that we take each value of x, subtract the expected value, square that value and multiply that value by its probability. Then sum all of those values.==

-> $$\sigma^{2}= Var(X) = \sum\limits (x_{i}- \mu)^2f(x_i) = \sum\limits x_i^2f(xi)-\mu^2 $$ 


- in machine learning, variance is the tendency to be inconsistent

- high varaiance will lead to unstable

---
Properties:

$$Var(x)\geq 0$$
$$Var(ax+b) = a^2Var(x)$$
$$Var(ax+by) = a^2Var(x)+b^2Var(x)$$

### Key words:

---
#### TAGS