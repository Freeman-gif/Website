### **Author: Freeman Chen, John Ginos**
### **Date: 2023-03-29**
### **Stats 530**

---
### Abstract

This project aims to study the effects of basketball shooting by examining differences between shooting from the right-hand and left-hand sides of the basket, as well as the impact of shooting angles and distances. The experiment will also explore whether player warm-up has any effect on shooting accuracy. The dependent variable in this study is the time taken to make three shots from a specific angle and distance, while the independent variables include the shooting angle, distance, and indicator variables for which player shoots the basketball and from which side.



### Data Collection

The data for this study was collected from a sample of 2 basketball players who were experienced in basektball. the shooting performance of each player was recorded. The following steps were taken to collect the data:
he data for this study was collected from a sample of 2 basketball players who were expe-
rienced in basektball. the shooting performance of each player was recorded. The following
steps were taken to collect the data:
- Shooting efficiency/Shooting Time:The shooting time was measured by recording the time that took a player to make 3 shots in that distance and angel. (lower the better)
- Shooting Angle and Distance: The shooting accuracy data was complied in a spreedsheet and analyzed using r,and a simple regression analysis was used to identify the independent variable that was strongly associated with shooting efficiency.
- Limitation :Limitations of the experiment include the relatively small sample size and the use of self-reported data for the variables. However, we have tried to minimize these limitations by using standardized data collection procedures and statistical methods.
- Collecting: We start shooting at the 10-feet mark while positioned at a 0-degree angle, we proceeded to each take shots and carefully observe the results. Subsequently, we relocated to the same 10-feet mark, but this time aimed at a 45-degree angle, and continued in this fashion. The process has shown as below.
```{r}
plot(model$residuals)
```
![[project.PNG]]


