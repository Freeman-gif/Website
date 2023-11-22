# Moving-average smoothing
[[Naïve methods]]

---
### Why:
When they’re too many noises, sometimes moving-average  
smoothing can help to identity trend.

--
### Apply:
Choose a window size $k$, estimate the moving average $W_t$ at time $t$ be the average value of the $k$ observations around time $t$
![[Pasted image 20231024083734.png]]

### Setup:
Default setting: rolling backward with window size k:
$$
w_t=\sum_{j=0}^{k-1} x_{t-j} / k
$$

example : k = 3
$$
\begin{array}{lll}
t & x_t & w_t \\
\hline & & \\
0 & x_0 & N a N \\
1 & x_1 & N a N \\
2 & x_2 & \frac{x_0+x_1+x_2}{3} \\
3 & x_3 & \frac{x_1+x_2+x_3}{3} \\
\vdots & \vdots & \\
n & x_n & \frac{x_{n-2}+x_{n-1}+x_n}{3}
\end{array}
$$

when center = True, k is odd and k = 2q+1
$$
\begin{aligned}
&w_t=\sum_{j=-q}^q x_{t-j} / k\\
&\begin{array}{lll}
t & x_t & w_t \\
0 & x_0 & N a N \\
1 & x_1 & \frac{x_0+x_1+x_2}{3} \\
2 & x_2 & \frac{x_1+x_2+x_3}{3}
\end{array}
\end{aligned}
$$
when center = True, k is even, k = 2q
$$
\begin{array}{cll}
w_t & =\sum_{j=-q}^{q-1} x_{t-j} / k \\
t & x_t & w_t \\
0 & x_0 & N a N \\
1 & x_1 & \frac{x_0+x_1}{2} \\
2 & x_2 & \frac{x_1+x_2}{2}
\end{array}
$$

**Choose window size :**
1. the window size of the filter should be chosen based on the application and the data being filtered. for example, weekly, monthly,quarterly
2. It’s common to choose the seasonality period if exists
3. The bigger the window, the <mark style="background: #FF5582A6;">smoother </mark>the trend  



---

### Key words:

---
#### TAGS
#timeseries 