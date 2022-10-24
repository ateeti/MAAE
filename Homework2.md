# Econometrics Homework 2

## Name : 

1. Saranpong Daengdej
2. Pongphon Chongrungsakulroj
3. Qiaofang Chen
4. Ateeti Sarathiwatprapai

## Chapter 4 : Multiple Regression Analysis

<strong>C6</strong> [Done]

Use the data in WAGE2 for this exercise.

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
  - $\therefore$ we can not reject the null hypothesis.
- $\theta_2 \pm c_{0.025} * se(\theta_2) = .0019537 \pm 1.96(.0047434)$
  - upper : .01125076
  - lower : -.00734336

* since 0 is inside the C.I. which implies that there is not enough evidence to reject the null hypothesis.
-------------------------------------------------------
<strong>C8</strong> [Done]

The data set 401KSUBS contains information on net financial wealth (nettfa),age of the survey respondent (age), annual family income (inc), family size(fsize), and participation in certain pension plans for people in the UnitedStates. The wealth and income variables are both recorded in thousands ofdollars. For this question, use only the data for single-person households (so $fsize = 1$)

i. How many single-person households are there in the data set?

<img width="172" alt="image" src="https://user-images.githubusercontent.com/116269829/197110058-2aa726e1-c342-4736-8a2e-04e347d7e2b8.png">

- There are 2017 single-person households in the datas set.

ii. Use OLS to estimate the model

$nettfa = \beta_0 + \beta_1inc + \beta_2age + u$

Interpret the slope coefficients. Are there any surprises in the slope estimates?

 <img width="634" alt="image" src="https://user-images.githubusercontent.com/116269829/197328981-a6e78091-dd5d-4a0d-90db-4df0477f6bc1.png">

- $\beta_1$ is .7993167, which means given 1 unit increase in annual family income, the net financial wealth will increase by around 0.8 unit.
- $\beta_2$ is .8426563 , which means given 1 unit increase in age, the net financial wealth will increase by 0.84 unit.
Both of the coefficients are statistically significant since their p-value are both 0.000. But the numbers are expected to be larger since age and income are supposed to have higher impact on net financial wealth.

iii. Does the intercept from the regression in part (ii) have an interesting meaning? Explain.

 <img width="587" alt="image" src="https://user-images.githubusercontent.com/116269829/197330265-41046934-cc9b-4cd5-92e3-f11a5e8ce66b.png">

- The intercept is not meaningful since both income and age are bounded. The minimum income in the data is 10 and minimum age is 25. It doesn't make sense if both income and age are 0. 

iv. Find the p-value for the test $H_0 : \beta_2 = 1$ against $H_1 : \beta_2 < 1$. Do you reject at the 1% significance level?

- The t test for $\beta_2$ is $T_{\hat{\beta_2}} = \frac{{{\hat{\beta_2}} - 1}}{ se(\hat{\beta_2})} =  \frac{{0.8426563 - 1}}{ 0.0920169} \approx -1.71$

  <img width="272" alt="image" src="https://user-images.githubusercontent.com/116269829/197332007-9edff877-f96a-4a59-b5b0-035a138da60c.png">
 
- The p-value with d.f. = n - k -1 = 2017 - 2 - 1 = 2014 is 0.0437, which is larger than 1%.
- So we cannot reject the null hypothesis at 1% significance level.

-------------------------------------------------------

<strong>C11</strong> [Done]

Use the data in HTV to answer this question.

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
  - $educ = \beta_0 + (\theta_1 + \beta_2)motheduc + \beta_2 fatheduc + \beta_3 abil + \beta_4 abil2$
  - $educ = \beta_0 + \theta_1 motheduc + \beta_2 motheduc + \beta_2 fatheduc + \beta_3 abil + \beta_4 abil2$
  - $educ = \beta_0 + \theta_1 motheduc + \beta_2 (motheduc + fatheduc) + \beta_3 abil + \beta_4 abil2$
- gen wi = motheduc + fatheduc
- reg educ motheduc wi abil abil2
- $t_{statistic} = { { \hat{\theta_1}} \over se(\hat{\theta_1})}$ = ${ { \hat{\beta_1} - \hat{\beta_2}} \over se(\hat{\theta_1})}$ = ${ {.1901261 - .1089387 } \over .0419431}$ = $1.9356557$
- p-value = 0.053 as shown below

![image](https://user-images.githubusercontent.com/20382285/197259253-b215bfea-4eea-4f99-9a9e-f8ed86f5859a.png)

iii. Add the two college tuition variables to the regression from part (i) and determine whether they are jointly statistically significant.

![image](https://user-images.githubusercontent.com/20382285/197265072-7e0588be-4759-46a1-a518-2a0c2511f376.png)

- p-value : 0.4322 $\therefore$ the tuition variables are jointly insignificant at any reasonable significance level.

iv. What is the correlation between tuit 17 and tuit 18? Explain why using the average of the tuition over the two years might be preferred to adding each separately. What happens when you do use the average?

![image](https://user-images.githubusercontent.com/20382285/197333154-64d3c716-a961-46e8-9ed6-ff525175778a.png)

- correlation between tuit17 & tuit18 : 0.9808, which means there's only a little change in tuition fee from age 17 to age 18.

![image](https://user-images.githubusercontent.com/20382285/197338823-6f99f9a6-1125-438a-9971-ad6e97ab6457.png)

The result shows that the t test for average tuition is $t_{avg tuit} = 1.29$, which is much more significant than both $t_{tuit17}(0.25)$ and $t_{tuit18}(0.00)$. To use the average tuition can increase the statistical significance. 

v. Do the findings for the average tuition variable in part (iv) make sense when interpreted causally? What might be going on?

- The coefficient of average tuition doesn't make much sense when interpreted causally. Because we only have two controled variables in this model, they are highest grades of parients and measure of ability. To analyse causality of tuition and educ, we need more controled variables such as teaching quality of the colleges to get stronger evidence. 

--------------------------------------------------------

## Chapter 7 : Multiple Regression Analysis with Qualitative Information
<strong>C2</strong>

i. Estimate the model\
$log(wage) = \beta_0 + \beta_1educ + \beta_2exper + \beta_3tenure + \beta_4married + \beta_5black + \beta_6south + \beta_7urban + u$\
and report the results in the usual form. Holding other factors fixed, what is the approximate difference in monthly salary between blacks and nonblacks? Is this difference statistically significant?

![image](https://user-images.githubusercontent.com/20382285/197349367-83213b17-3943-4202-87a0-a10731120ac4.png)

- $\beta_5$ determines the difference in month log(salary) between black and nonblacks. In this case, black earns 18.835% less than the nonblacks in salary. 

ii. Add the variables $exper^2$ and $tenure^2$ to the equation and show that they are jointly insignificant at even 20% level.

![image](https://user-images.githubusercontent.com/20382285/197350063-92792d55-7b9b-48d9-aa68-51bc541bc36b.png)

- p-value of $F_{statistic}$ = 0.2260 which is greater that the critical level (20%)
  - 0.2260 > 0.200 $\therefore$ we conclude that exper2 and tenure2 are jointly statistically insignificant at even the 20% significance level.  

iii. Extend the original model to allow the return to education to depend on race and test whether the return to education does depend on race.

![image](https://user-images.githubusercontent.com/20382285/197350747-b4021de7-41d5-41e6-81ac-acf6d8afebeb.png)

![image](https://user-images.githubusercontent.com/20382285/197353762-f5c9980e-d566-4a20-956e-4479a02ce558.png)

- p-value of $F_{statistic} = 0.2626$ , which is greater than significance level even at 20%
- $\therefore$ we can say that education does not depend on race.  

iv. Again, start with the original model, but now allow wages to differ across four groups of people: married and black, married and nonblack, single and black, and single and nonblack. What is the estimated wage differential between married blacks and married nonblacks?

$log(wage) = \beta_0 + \beta_1educ + \beta_2exper + \beta_3tenure + \beta_4south + \beta_5urban + \beta_6marriedblack + \beta_7marriednonblack + \beta_8 singleblack + u$

![image](https://user-images.githubusercontent.com/20382285/197354078-745b1622-6691-4c12-b75e-dff3ba99cc41.png)

- $\hat{beta_6} - \hat{beta_7}$ = .0094484 - .1889147 = -.1794663 
- the estimated wage differential between married blacks and married nonblacks approximately 17.94%

--------------------------------------------------------
<strong>C4</strong>

i. Consider the equation

$colgpa = \beta_0 + \beta_1hsize + \beta_2hsize^2 + \beta_3hsperc + \beta_4sat + \beta_5female + \beta_6athlete + u$

What are your expectations for the coefficients in this equation? Which ones are you unsure about?

- We are not sure about $\beta_1$ and $\beta_2$. 
- $\beta_3$ is expected to be negative since lower percentile means higher grade.
- $\beta_4$ is expected to be positive since it's SAT score should be positively related to GPA.
- $\beta_5$ is unclear.
- $\beta_6$ is expected to be negative because athelets are supposed to have less time to study than other students.

ii. Estimate the equation in part (i) and report the results in the usual form. What is the estimated GPA differential between athletes and nonathletes? Is it statistically significant?



--------------------------------------------------------
<strong>C7</strong>

Use the data in WAGE1 for this exercise

![image](https://user-images.githubusercontent.com/20382285/197378305-d708fb5a-1ec0-436a-aaa4-3d82a535b5a0.png)

![image](https://user-images.githubusercontent.com/20382285/197358647-d775328c-7d2e-458c-a59e-e251ac5f82b3.png)

i . estimate the gender differential when $educ = 12.5$. Compare this with the estimated differential when $educ = 0$

- when $educ = 12.5$, the gender differential : -.2267886 + (-.0055645*12.5) = -.29634485 = 29.63% in wage
- when $educ = 0$, the gender differential : -.2267886 + (-.0055645*0) = -.2267886 = 22.68% in wage
- so the gender differential in wage is -.29634485 - -.2267886 = -.06955625 $\approxeq$ 6.95%

ii. Run the regression used to obtain (7.18), but with female·(educ − 12.5)replacing female∙educ. How do you interpret the coefficient on female now?

- $\hat{log(wage)} = \beta_0 + \delta_0female + \beta_1educ + \delta_1female*educ + other factors$
- $\hat{log(wage)} = \beta_0 + \delta_0female + \beta_1educ + \delta_1female*(educ-12.5) + other factors$
- $\hat{log(wage)} = \beta_0 + \delta_0female + \beta_1educ + \delta_1female*educ + \delta_1female12.5 + other factors$
- $\hat{log(wage)} = \beta_0 + female(\delta_0 + \delta_112.5) + \beta_1educ + \delta_1female*educ + other factors$
- $\theta_0 : (\delta_0 + \delta_112.5) = (-.2267886 + -.0055645(12.5)) = -.29634485$

iii. Is the coefficient on female in part (ii) statistically significant? Comparethis with (7.18) and comment.

![image](https://user-images.githubusercontent.com/20382285/197380504-62e52be0-26e3-4d6f-85e9-abc92b88bf8c.png)

- t score on female in part ii : -8.27, which is very significant. 

--------------------------------------------------------
<strong>C16</strong>

i. In the entire sample, what percentage of the students attend a Catholic high school? What is the average of math12 in the entire sample?

![image](https://user-images.githubusercontent.com/20382285/197380838-16a941db-843d-4cbd-9950-6b670481abd3.png)

- .06083445 $\approxeq$ 60.8% attend a Catholic high school

ii. Run a simple regression of math12 on cathhs and report the results in the usual way. Interpret what you have found.

![image](https://user-images.githubusercontent.com/20382285/197380886-bb082ebc-e312-4a7c-8fcf-b4680a8469d0.png)

- $math12 = \beta_0 + \beta_1cathhs + u$
- $math12 = 51.92299 + 3.462385cathhs + u$

$\hat{\beta_1} = 3.462385$ is the differential in math score of those who attends catholic and non-catholic high-school
  - cathhs = 1 : $\beta_0 + \beta_1$
  - cathhs = 0 : $\beta_0$

iii. Now add the variables lfaminc, motheduc, and fatheduc to the regression from part (ii). How many observations are used in the regression? What happens to the coefficient on cathhs, along with its statistical significance?

![image](https://user-images.githubusercontent.com/20382285/197384364-4c27c9b4-92c5-4a36-a43f-c1615030c0d7.png)

- number of observation(variables) used : 7430 
- the coefficient on cathhs reduces by 1.985155 
  - from 3.462385 -> 1.47723 
  - its statistical significance has also reduced but still remains significant 
    - went from $t_{cathhs}$ : 7.57 -> 3.53 
  
iv. Return to the simple regression of math12 on cathhs, but restrict the regression to observations used in the multiple regression from part (iii). Do any important conclusions change?

- to restrict the regression with respect to the simple regression in part i.
  - We treat $H_0 : \beta_2 = \beta_3 = \beta_4 = 0$

![image](https://user-images.githubusercontent.com/20382285/197384104-5ecc3310-1d39-4077-b7f6-3caafcda62c6.png)

- p-value $f_{statistic}$ : 0.0000 implies that ifaminc, motheduc and fatheduc are jointly statistically significant.
 
v. To the multiple regression in part (iii), add interactions between cathhs and each of the other explanatory variables. Are the interaction termsindividually or jointly significant?

![image](https://user-images.githubusercontent.com/20382285/197384808-61ad3e55-9b6c-4147-a058-c01a055b932d.png)

![image](https://user-images.githubusercontent.com/20382285/197384817-1b41c93d-c1b1-47b5-96b8-a372a4a0e7c8.png)

-..

vii. Compute the average partial effect of cathhs in the model estimated in part (v). How does it compare with the coefficients on cathhs in parts (iii) and (v)?

$math12 = \beta_0 + \beta_1cathhs + \beta_2lfaminc + \beta_3 motheduc + \beta_4 fatheduc + \beta_5clfam + \beta_6cmotheduc + \beta_7cfatheduc$
- average partial effect of cathhs is when 
  - cathhs == 1 : $\beta_0 + \beta_1 + \beta_5 + \beta_6 + \beta_7$

--------------------------------------------------------
