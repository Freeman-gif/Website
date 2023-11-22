# Decomposition


---
### Three major components for Time series :
- Trend component: $T_{t}$
- Seasonal components: $S_{t}$
- Remaining components(Noise):$R_{t}$
---
### Decomposition Method:
#### Classical Decomposition:

Classical Decomposition is the most common way
steps:
- Decide the window size k for MA smoothing
- Assume that the seasonal component is <mark style="background: #FF5582A6;">constant</mark>, decide of the <mark style="background: #FF5582A6;">magnitude of the seasonal fluctuations </mark>is additive or multiplicative  
	- Additive: magnitude of the seasonal fluctuations around the trend<mark style="background: #FF5582A6;"> does not change with time </mark>
	- Multiplicative: magnitude of the seasonal fluctuations around the trend, <mark style="background: #FF5582A6;">is proportional to time </mark>, trend is increasing or decreasing, the magnitude of the seasonal fluctuations with trend 
- ![[Pasted image 20231024085142.png]]
---
### Additive Decomposition:
steps:
1. Compute the trend component: Tt = wt from MA smoothing
2. Compute the detrended data : $d_{t}$ = $x_{t}$ − $T_{t}$
3. To estimate the seasonal component for each season, simply average the <mark style="background: #FF5582A6;">detrended </mark>value for that season 
 $$
\begin{aligned}
S_{\text {Mon }} & =\frac{d_{\text {Mon }_1}+d_{\text {Mon }_2}+\ldots}{\# \text { Mondays }} \\
S_{\text {Tue }} & =\frac{d_{\text {Tue }_1}+d_{\text {Tue }_2}+\ldots}{\# \text { Tuesdays }}
\end{aligned}
$$
4. Remaining component (Noise): $R_{t}$ = $x_{t}$ − $T_{t}$ − $S_{t}$  

---
### Multiplicative decomposition
steps:
1. Compute the trend component: Tt = wt from MA smoothing
2. Compute the detrended data : $d_{t}$ = $x_{t}$ /$T_{t}$
3. to estimate the seasonal component for each season, simply  average the detrended values for that season. For example,  with daily data, the seasonal component for each day of the  week is the average of all the detrended values from the  
same day of the week in the data
 $$
\begin{aligned}
S_{\text {Mon }} & =\frac{d_{\text {Mon }_1}+d_{\text {Mon }_2}+\ldots}{\# \text { Mondays }} \\
S_{\text {Tue }} & =\frac{d_{\text {Tue }_1}+d_{\text {Tue }_2}+\ldots}{\# \text { Tuesdays }}
\end{aligned}
$$
4. Remaining component (Noise): $R_{t}$ = $\frac{X_{t}}{T_{t}*S_{t}}$
![[Pasted image 20231024103431.png]]
---
### Alternative Decomposition Methods

X11: based off classical decomposition with a fix of some  
problems (only works for quarterly and monthly data);  
SEATS: seasonal extracted by ARIMA model (only works for  
quarterly and monthly data)  
STL: Seasonal and Trend decomposition using Loess:  
▶ The seasonal component is allowed to change over time, and  
the rate of change can be controlled by the user.  
▶ The smoothness of the trend-cycle can also be controlled by  
the user.  
▶ It can be robust to outliers (i.e., the user can specify a robust  
decomposition), so that occasional unusual observations will  
not affect the estimates of the trend-cycle and seasonal  
components. They will, however, affect the remainder  
component.
---
### Disadvantage of Classical Decomposition
- The estimate of the trend-cycle is unavailable for the first few and last few observation( will base on the window function and does it set as center or rolling )
- the trend cycle estimate tends to over-smooth rapid rises and falls in the data
- it assume the seasonal component repeats for the same season( think of how we estimate $d_{t}$)
- Classical decomposition methods assume that the seasonal component repeats from year to year.
- Occasionally, the values of the time series in a small number of periods may be particularly unusual. For example, the monthly air passenger traffic may be affected by an industrial dispute, making the traffic during the dispute different from usual. The classical method is not robust to these kinds of unusual values.


---
### Resource:
https://towardsdatascience.com/different-types-of-time-series-decomposition-396c09f92693#:~:text=Rather%20than%20a%20sum%2C%20the,time%20series%20from%20its%20variation.

---
#### TAGS
#timeseries 