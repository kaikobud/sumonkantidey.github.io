---
layout: post
title: Applied Differential Privacy for Releasing Tables
image: rope_regression.png
---

![](https://cdn-images-1.medium.com/max/1600/1*_COjgiypANy8byDnexEFIQ.png)()



Data privacy is in the air in newsrooms & capitals across the world. Facebook was fined $5 bn for being too permissive with data—--data collected via APIs in the name of social science research.  Under GDPR, meaningful, independent research often maps to processing "3rd party sensitive category data collected without consent." Journalists and the public increasingly realize that personal identifying

Yet some of the most valuable data sources for the social and medical sciences reside inside corporate networks. What to do? 

Three big obstacles stand in the way of corporate data sharing--legal risk, privacy, and cost. 

**Does my data even need to be protected**

**Does my data even need to be protected**


Privacy advocates work to protect people from identity theft, scams, information & other abuse, often social scientists advocating for research aren't at the table.
We are seeing a number social cross-currents nexus

Famed social psychologist Richard Nisbett [recently argued](https://www.edge.org/conversation/richard_nisbett-the-crusade-against-multiple-regression-analysis) that regression analysis is so misused and misunderstood that analyses based on multiple regression “are often somewhere between meaningless and quite damaging.” (He was mainly talking about cases in which researchers publish correlational results that are covered in the media as causal statements about the world.)

**Using simulations to unpack regression**

```R
# make the code reproducible by setting a random number seed
set.seed(100)

# When everything works:
N <- 1000
x <- rnorm(N)
y <- .4 * x + rnorm(N)
hist(x)
hist(y)

# Now estimate our model:
summary(lm(y ~ x))

Call:
lm(formula = y ~ x)
Residuals:
    Min      1Q  Median      3Q     Max 
-3.0348 -0.7013  0.0085  0.6212  3.1688 
Coefficients:
            		Estimate Std. Error t value Pr(>|t|)    
(Intercept) 	0.003921   0.031039   0.126    0.899    
x           	0.413415   0.030129  13.722   <2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
Residual standard error: 0.9814 on 998 degrees of freedom
Multiple R-squared:  0.1587,	Adjusted R-squared:  0.1579 
F-statistic: 188.3 on 1 and 998 DF,  p-value: < 2.2e-16

# Plot it
library(ggplot2)
qplot(x, y) +
  geom_smooth(method='lm') +
  theme_bw() +
  ggtitle("The Perfect Regression")
```

