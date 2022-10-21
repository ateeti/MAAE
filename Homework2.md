# Econometrics Homework 2

## Name : 

1. Saranpong Daengdej
2. Pongphon Chongrungsakulroj
3. (Qiaofang)Prudence Chen
4. Ateeti Sarathiwatprapai

## Chapter 4 : Multiple Regression Analysis

<strong>C6</strong> Use the data in WAGE2 for this exercise.

i. Consider the standard wage equation $\ log(wage) = \beta_0 + \beta_1 educ + \beta_2 exper + \beta_3 tenure + u$
* $H_0 : \beta_2 = \beta_3$
* $H_1 : \beta_2 \neq \beta_3$

ii. Test the null hypothesis in part (i) against a two-sided alternative, at the 5% significance level, by constructing a 95% confidence interval. What do you conclude?

![image](https://user-images.githubusercontent.com/20382285/197211300-6da77bd8-095f-454b-a412-249c4c6a3ed8.png)

Key idea is that we want to find the $t_{statistic} = {\hat{\beta_2} - \hat{\beta_3} \over se( \hat{\beta_2} - \hat{\beta_3} )}$\
and we know the difference in the coefficients is $\hat{\beta_2} - \hat{\beta_3} = .0153285 -.0133748 = 0.0019537$\
The only problem is that we do not know the value of $se(\hat{\beta_2} - \hat{\beta_3})$

- let us define $\theta_2 : \beta_2 - \beta_3$
- the t statistic in terms of $\hat{\theta_2}$ is $t = \hat{\theta_2}/se(\hat{\theta_2})$
  - we want to find $se(\theta_2)$ 
- because $\theta_2 : \beta_2 - \beta_3$, we can also write $\beta_2 = \theta_2 + \beta_3$. Plugging this into the equation and rearrange gives this equation

  - $log(wage) = \beta_0 + \beta_1 educ + (\theta_2 + \beta_3)exper + \beta_3 tenure + u$
  - $log(wage) = \beta_0 + \beta_1 educ + \theta_2 exper + \beta_3(exper + tenure) + u$
  
- now define a new variable name wi = exper + tenure, and regress it in stata
  - $log(wage) = \beta_0 + \beta_1 educ + \theta_2 exper + \beta_3 wi + u$
  - reg lwage educ expert wi\
![image](https://user-images.githubusercontent.com/20382285/197210584-e3b6bc40-59be-452c-a988-af0624503bd9.png)
    - and we get se( $\theta_2$ ) = .0047434
    
- finally, we then calculate $t_{statistic} = {(.0153285 - .0133748) \over .0047434} = .41187756$
  - Also, since $t_{statistic} = .41187756 < critical-value = 1.96$ 
  - $\therefore$ we can not reject the null
- $\theta_2 \pm c * se(\theta_2) = .0019537 \pm 1.96(.0047434)$
  - upper : .01125076
  - lower : -.00734336

* since 0 is inside the C.I. which implies that there is not enough evidence to reject the null hypothesis.
-------------------------------------------------------
<strong>C8</strong> The data set 401KSUBS contains information on net financial wealth (nettfa),age of the survey respondent (age), annual family income (inc), family size(fsize), and participation in certain pension plans for people in the UnitedStates. The wealth and income variables are both recorded in thousands ofdollars. For this question, use only the data for single-person households (so $fsize = 1$)

i. How many single-person households are there in the data set?

<img width="172" alt="image" src="https://user-images.githubusercontent.com/116269829/197110058-2aa726e1-c342-4736-8a2e-04e347d7e2b8.png">

- There are 2017 single-person households in the datas set.

ii. Use OLS to estimate the model

$nettfa = \beta_0 + \beta_1inc + \beta_2age + u$

Interpret the slope coefficients. Are there any surprises in the slope estimates?

-

iii. Does the intercept from the regression in part (ii) have an interesting meaning? Explain.

-

iv. Find the p-value for the test $H_0 : \beta_2 = 1$ against $H_1 : \beta_2 < 1$. Do you reject at the 1% significance level?

-------------------------------------------------------

C11. Use the data in HTV to answer this question.

i. Estimate the regression model

$educ = \beta_0 + \beta_1 motheduc + \beta_2 fatheduc + \beta_3 abil + \beta_4 abil^2 + u$

by OLS and report the results in the usual form. Test the null hypothesis that educ is linearly related to abil against the alternative that the relationship is       quadratic.

![image](https://user-images.githubusercontent.com/20382285/197214595-9c81a060-1b9b-4cc1-84d6-d77566015dd8.png)

- testing that educ is linearly related to abil 
  - $H_0 : \beta_4 = 0$
  - $educ = \beta_0 + \beta_1 motheduc + \beta_2 fatheduc + \beta_3 abil + \beta_4 abil2$
  - $t_{statistic} = { { \hat{\beta_4} - 0 } \over se(\hat{\beta_4})}$ = $.050599 \over .0083039$ = $6.0934019$
    - very high value $\therefore$ reject $H_0 : \beta_4 = 0$

ii.Using the equation in part (i), test $H_0 : \beta_1 = \beta_2$ against a two-sided alternative. What is the p-value of the test?

- let's define $\theta_1 = \beta_1 - \beta_2$
- We can rewrite it as $\beta_1 = \theta_1 + \beta_2$


