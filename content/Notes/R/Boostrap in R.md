```xml 
head(lab8b)  
y=lab8b$y  
x1=lab8b$x1  
x2=lab8b$x2  
fit=lm(y~x1+x2)  
beta0=coef(fit)  
print(beta0)  
r=resid(fit)  
p=predict(fit)  
df=data.frame()  
for(k in 1:100){  
bootr=sample(r, replace=T)  
#print(bootr)  
newy=y+bootr  
fit2=lm(newy~x1+x2)  
beta_b=coef(fit2)  
df=rbind(df,beta_b)  
}  

colnames(df)=c("Intercept","Slope1", "Slope2")  
boot_data=df  
head(df)  
#write.csv(df,"df.csv",row.names = F)  
#to plot it to see shape  
hist(df$Slope1)  
#to find percentiles  
quantile(df$Slope1,.025)  
quantile(df$Slope1,.975)


```
















