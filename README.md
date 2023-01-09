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
Which variables/coefficients provided a non-random amount of variance to the mpg values in the dataset?

Is the slope of the linear model considered to be zero? Why or why not?

Does this linear model predict mpg of MechaCar prototypes effectively? Why or why not?

## Summary Statistics on Suspension Coils
**Collect summary statistics on the pounds per square inch (PSI) of the suspension coils from the manufacturing lots.**

Total Summary:

![Total Summary](https://github.com/Kcav18/MechaCar_Statistical_Analysis/blob/main/Total_Summary_SuspensionCoil.png)

Lot Summary:

![Lot Summary](https://github.com/Kcav18/MechaCar_Statistical_Analysis/blob/main/Lot_Summary_SuspensionCoil.png)

The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 pounds per square inch. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?

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

Lot 1:

![Lot 1](https://github.com/Kcav18/MechaCar_Statistical_Analysis/blob/main/TTest_Lot1.png)

Lot 2:

![Lot 2](https://github.com/Kcav18/MechaCar_Statistical_Analysis/blob/main/TTest_Lot2.png)

Lot 3:

![Lot 3](https://github.com/Kcav18/MechaCar_Statistical_Analysis/blob/main/TTest_Lot3.png)

In your README, create a subheading ## T-Tests on Suspension Coils, then briefly summarize your interpretation and findings for the t-test results. Include screenshots of the t-test to support your summary.

## Study Design: MechaCar vs Competition

Write a short description of a statistical study that can quantify how the MechaCar performs against the competition. In your study design, think critically about what metrics would be of interest to a consumer: for a few examples, cost, city or highway fuel efficiency, horse power, maintenance cost, or safety rating.

In your description, address the following questions:

What metric or metrics are you going to test?

What is the null hypothesis or alternative hypothesis?

What statistical test would you use to test the hypothesis? And why?

What data is needed to run the statistical test?
