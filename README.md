# MechaCar Statistical Analysis

## Overview

AutosRUs’ newest prototype, the MechaCar, is suffering from production troubles that are blocking the manufacturing team’s progress. AutosRUs’ upper management has called on me, Jeremy, and the data analytics team to review the production data for insights that may help the manufacturing team.

In this challenge, I helped Jeremy and the data analytics team do the following:

- Perform multiple linear regression analysis to identify which variables in the dataset predict the mpg of MechaCar prototypes.
- Collect summary statistics on the pounds per square inch (PSI) of the suspension coils from the manufacturing lots.
- Run t-tests to determine if the manufacturing lots are statistically different from the mean population.
- Design a statistical study to compare vehicle performance of the MechaCar vehicles against vehicles from other manufacturers. 

## Results

## Linear Regression to Predict MPG: 
*Perform multiple linear regression analysis to identify which variables in the dataset predict the mpg of MechaCar prototypes.*

**Results from Linear Regression:**
```
Call:
lm(formula = mpg ~ vehicle_length + vehicle_weight + spoiler_angle + 
    ground_clearance + AWD, data = MechaCar_mpg)

Residuals:
     Min       1Q   Median       3Q      Max 
-19.4701  -4.4994  -0.0692   5.4433  18.5849 

Coefficients:
                   Estimate Std. Error
(Intercept)      -1.040e+02  1.585e+01
vehicle_length    6.267e+00  6.553e-01
vehicle_weight    1.245e-03  6.890e-04
spoiler_angle     6.877e-02  6.653e-02
ground_clearance  3.546e+00  5.412e-01
AWD              -3.411e+00  2.535e+00
                 t value Pr(>|t|)    
(Intercept)       -6.559 5.08e-08 ***
vehicle_length     9.563 2.60e-12 ***
vehicle_weight     1.807   0.0776 .  
spoiler_angle      1.034   0.3069    
ground_clearance   6.551 5.21e-08 ***
AWD               -1.346   0.1852    
---
Signif. codes:  
0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 8.774 on 44 degrees of freedom
Multiple R-squared:  0.7149,	Adjusted R-squared:  0.6825 
F-statistic: 22.07 on 5 and 44 DF,  p-value: 5.35e-11
```
Which variables/coefficients provided a non-random amount of variance to the mpg values in the dataset? **The vehicle length and ground clearance provide non-random amounts of variance to the MPG values in the dataset. The p-value for vehicle length is 2.60e-12 and the p-value for ground clearance is 5.21-08**

Is the slope of the linear model considered to be zero? Why or why not? **The slope of the linear model is not considered to be zero because the p-value is much smaller than the assumed significance level (.05%). Therefore, the null hypothesis is rejected.**

Does this linear model predict mpg of MechaCar prototypes effectively? Why or why not? **Yes, this linear model predicts mpg of MechaCar prototypes effectively. The r-squared value of .7149 means that 71% of all mpg predictions will be determined correctly by this model.**

## Summary Statistics on Suspension Coils
**Collect summary statistics on the pounds per square inch (PSI) of the suspension coils from the manufacturing lots.**

Total Summary:

![Total Summary](https://github.com/Kcav18/MechaCar_Statistical_Analysis/blob/main/Total_Summary_SuspensionCoil.png)

Lot Summary:

![Lot Summary](https://github.com/Kcav18/MechaCar_Statistical_Analysis/blob/main/Lot_Summary_SuspensionCoil.png)

The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 pounds per square inch. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not? **When looking at all lots combined, manufacturing is meeting the specifications as the variance is below 100 psi. But when looking at the lots individually, we can see that lot 3 is not meeting the specifications. Lot 3 has a variance of 170.29 psi, which exceeds the 100 psi max variance specification.**

## T-Tests on Suspension Coils
*Run t-tests to determine if the manufacturing lots are statistically different from the mean population.*

The code used to perform the T-Tests is below:
```
# T-Tests on Suspension Coils - all lots
t.test(Suspension_Coil$PSI, mu=1500)

# T-Tests on Suspension Coils - Lot 1
Lot_1 <- Suspension_Coil[which(Suspension_Coil$Manufacturing_Lot =='Lot1'),]
t.test(Lot_1$PSI, mu=1500)

# T-Tests on Suspension Coils - Lot 2
Lot_2 <- Suspension_Coil[which(Suspension_Coil$Manufacturing_Lot =='Lot2'),]
t.test(Lot_2$PSI, mu=1500)

# T-Tests on Suspension Coils - Lot 3
Lot_3 <- Suspension_Coil[which(Suspension_Coil$Manufacturing_Lot =='Lot3'),]
t.test(Lot_3$PSI, mu=1500)
```
**Results of T-Tests:**

All Lots:

![All lots](https://github.com/Kcav18/MechaCar_Statistical_Analysis/blob/main/TTest_AllLots.png)

*The true mean of the whole sample is 1498.78. The p value is 0.06, which is over the significance level of 0.05. This means that the null hypothesis cannot be rejected and the mean of all the lots combined is statistically similar to the population mean of 1500.*

Lot 1:

![Lot 1](https://github.com/Kcav18/MechaCar_Statistical_Analysis/blob/main/TTest_Lot1.png)

*Lot 1 has the true sample mean of 1500. The p value is 1, which is over the significance level of 0.05. This means that the null hypothesis cannot be rejected and the mean of lot 1 is statistically similar to the population mean of 1500.*

Lot 2:

![Lot 2](https://github.com/Kcav18/MechaCar_Statistical_Analysis/blob/main/TTest_Lot2.png)

*Lot 2 has a sample mean of 1500.02. The p value is 0.61, which is over the significance level of 0.05 which means that the null hypothesis cannot be rejected and the mean of lot 2 is statistically similar to the population mean of 1500.*

Lot 3:

![Lot 3](https://github.com/Kcav18/MechaCar_Statistical_Analysis/blob/main/TTest_Lot3.png)

*Lot 3 has a sample mean of 1496.14. The p value is .04, which is under the significance level of 0.05. This means that the null hypothesis can be rejected and the mean of lot 3 is not statistically similar to the population mean of 1500.*

## Study Design: MechaCar vs Competition

A statistical study that could be conducted against MechaCar and its competition could include important factors such as cost, fuel efficiency, maintenance cost, and safety ratings.

What metric or metrics are you going to test? **I would test how MechaCar compares to competitors in regard to overall cost (initial cost, fuel cost, and maintenance) and the overall safety rating.**

What is the null hypothesis or alternative hypothesis? **The Null Hypothesis is that MechaCar's overall pricing and safety ratings are in line with its competitors.**

What statistical test would you use to test the hypothesis? And why? **A multiple linear regression test because I would be testing how strong the correlation is between several variables. Multiple linear regression would show how the variables impact the safety ratings and what factors have the highest correlation with selling price and overall cost.**

What data is needed to run the statistical test? **A random sample of safety ratings, sales price, fuel cost, and maintenance cost would need to be collected from MechaCar and their competitors.**
