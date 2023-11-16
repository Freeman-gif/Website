# Time Series Main 


---
### Definition:
- Forecasting
- Goals
- Planning
- short/medium/long-term forecasts

---
### Time Series Data EDA
#### About time series Data:
- A time series is a set of observations $x_t$ of a time-dependent variable $X_t$, at a specific time $t$.
- It's most common to consider data collected from<mark style="background: #FF5582A6;"> discrete time stamps</mark>.
- Time Series Analysis to get helpful information from the historic  
data


#### Examine the histrorical data:
![[Pasted image 20231024082626.png]]
1. Trend
	- the long-term pattern of a time series
	- it can be <mark style="background: #FF5582A6;">positive or negative</mark> 
	- if there's no show an increasing or decreasing pattern then the series is <mark style="background: #FF5582A6;">stationary </mark>
	![[Pasted image 20231024081304.png]]
2. Seasonality
	- A Seasonality occurs when the time series exhibits regular  
fluctuations with<mark style="background: #FF5582A6;"> fixed frequency,</mark> like during the same month
![[Pasted image 20231024082547.png]]
1. Irregularity:
	- An irregular time series is **the opposite of a regular time series**. The data in the time series follows a temporal sequence, but the measurements might not happen at a regular time interval.
1. Cyclic:
	- Any pattern showing an up and down movement around a given  
trend is identified as a cyclical pattern.
![[Pasted image 20231024081516.png]]
5. Anomalies:
	- Anomalies are rare items, events, or patterns that <mark style="background: #FF5582A6;">significantly  
differ</mark> from the majority of the data.

 - ![[Pasted image 20231024082729.png]]

###### note: 
seasonality vs cyclicality: **If the fluctuations are not of a fixed frequency then they are cyclic; if the frequency is unchanging and associated with some aspect of the calendar, then the pattern is seasonal**.

---
### Analysis Methods:
- [[Time series plot]]
- [[Moving-average smoothing]] -> for estimate Trend
- [[Decomposition]] ->  for estimate seasonal 
- [[ACF and PACF plots]]
- [[Missing value imputation]]
- [[stationary process]]
- [[Auto Correlation]]
##### note:
MA smoothing is not MA from ARIMA, use the analysis methods to check if the data is stationary or not 
---
### Models:
- [[Naïve methods]]
#### Stationary model 
- [[ARIMA]] 
#### Non-stationary 
##### Trend:
- [[MA Smoother]]
- [[ARIMA]]

##### Trend + Seasonality:
- [[SARIMA]]
- [[Decomposition]]


---
- [[Traditional statistical models]]
- [[Newer statistical models]]
- [[ML predictive models]]
- [[Recursive Neural Nets]]
- [[Ensembles models]]


---

### Key words:

---
#### TAGS
#timeseries #main