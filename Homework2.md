# Econometrics Homework 2

## Name : 

1. Saranpong Daengdej
2. Pongphon Chongrungsakulroj
3. Qiaofang Chen
4. Ateeti Sarathiwatprapai

## Chapter 4 : Multiple Regression Analysis

### <strong>C6</strong> [Done]

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
### <strong>C8</strong> [Done]

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

v. If you do a simple regression of nettfa on inc, is the estimated coefficient on inc much different from the estimate in part (ii)? Why or why not?

<img width="635" alt="image" src="https://user-images.githubusercontent.com/116269829/197501293-024825b4-f85f-404e-b0e1-7fd9f4b02b4e.png">

- The coefficient on inc is .8206815, which is not much different from the estimate in part (ii). Because the correlation between inc and age is relatively low.
 <img width="267" alt="image" src="https://user-images.githubusercontent.com/116269829/197502692-d7d00d94-b11e-4d6e-b19e-ff409a5e5e25.png">



-------------------------------------------------------

### <strong>C11</strong> [Done]

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
### <strong>C2</strong> [Done]

i. Estimate the model\
$log(wage) = \beta_0 + \beta_1educ + \beta_2exper + \beta_3tenure + \beta_4married + \beta_5black + \beta_6south + \beta_7urban + u$\
and report the results in the usual form. Holding other factors fixed, what is the approximate difference in monthly salary between blacks and nonblacks? Is this difference statistically significant?

![image](https://user-images.githubusercontent.com/20382285/197349367-83213b17-3943-4202-87a0-a10731120ac4.png)

$log(wage) = 5.40 + 0.07educ + 0.01exper + 0.01tenure + 0.20married - 0.19black - 0.09south + 0.18urban$

$n = 935$, $R^2 = 0.2526$

- $\beta_5$ determines the difference in month log(salary) between black and nonblacks. In this case, black earns 18.835% less than the nonblacks in salary. 
- The absolute value of t statistic is 0.1883499/0.0376666 = 5, and p-value is 0.000, which means that the approximate difference is statistically significant.

ii. Add the variables $exper^2$ and $tenure^2$ to the equation and show that they are jointly insignificant at even 20% level.

![image](https://user-images.githubusercontent.com/20382285/197350063-92792d55-7b9b-48d9-aa68-51bc541bc36b.png)

- p-value of $F_{statistic}$ = 0.2260 which is greater that the critical level (20%)
  - 0.2260 > 0.200 $\therefore$ we conclude that exper2 and tenure2 are jointly statistically insignificant at even the 20% significance level.  

iii. Extend the original model to allow the return to education to depend on race and test whether the return to education does depend on race.

![image](https://user-images.githubusercontent.com/20382285/197350747-b4021de7-41d5-41e6-81ac-acf6d8afebeb.png)

![image](https://user-images.githubusercontent.com/20382285/197353762-f5c9980e-d566-4a20-956e-4479a02ce558.png)

- p-value of $F_{statistic} = 0.2626$ , which is greater than significance level even at 20%
- $\therefore$ we cannot reject the null hypothesis that the return to education does not depend on race.

iv. Again, start with the original model, but now allow wages to differ across four groups of people: married and black, married and nonblack, single and black, and single and nonblack. What is the estimated wage differential between married blacks and married nonblacks?

$log(wage) = \beta_0 + \beta_1educ + \beta_2exper + \beta_3tenure + \beta_4south + \beta_5urban + \beta_6marriedblack + \beta_7marriednonblack + \beta_8 singleblack + u$

![image](https://user-images.githubusercontent.com/20382285/197354078-745b1622-6691-4c12-b75e-dff3ba99cc41.png)

- $\hat{beta_6} - \hat{beta_7}$ = .0094484 - .1889147 = -.1794663 
- the estimated wage differential between married blacks and married nonblacks approximately 17.94%

--------------------------------------------------------
### <strong>C4</strong> [Done]

i. Consider the equation

$colgpa = \beta_0 + \beta_1hsize + \beta_2hsize^2 + \beta_3hsperc + \beta_4sat + \beta_5female + \beta_6athlete + u$

What are your expectations for the coefficients in this equation? Which ones are you unsure about?

- We are not sure about $\beta_1$ and $\beta_2$. 
- $\beta_3$ is expected to be negative since lower percentile means higher grade.
- $\beta_4$ is expected to be positive since it's SAT score should be positively related to GPA.
- $\beta_5$ is unclear.
- $\beta_6$ is expected to be negative because athelets are supposed to have less time to study than other students.

ii. Estimate the equation in part (i) and report the results in the usual form. What is the estimated GPA differential between athletes and nonathletes? Is it statistically significant?

<img width="633" alt="image" src="https://user-images.githubusercontent.com/116269829/197462984-a56e9a06-7c02-4e60-a6c7-150f4867a2f6.png">

$colgpa = 1.241 - 0.057hsize + 0.005hsize^2 - 0.013hsperc + 0.002sat + 0.155female + 0.169athlete$

$n = 4137$, $R^2 = 0.2925$

- The estimated GPA differential between athletes and nonathletes is 0.1693064.
- The t statistic for athletes is 4.00 and p-value is 0.000, so the estimated difference is statistically significant at 1% level.

iii. Drop sat from the model and reestimate the equation. Now, what is the estimated effect of being an athlete? Discuss why the estimate is different than that obtained in part (ii).  

<img width="629" alt="image" src="https://user-images.githubusercontent.com/116269829/197464103-90ab5329-e190-4323-aed9-6ad1bc1bd5a6.png">

- Now the estimated effect of being an athlete is only 0.0054487, which is much more smaller and not statistically significant. This happened because SAT can impact the result, but it's not a control variable in the new regression. Then the estimated result of athlete is confounded because of SAT. 

iv. In the model from part (i), allow the effect of being an athlete to differ by gender and test the null hypothesis that there is no ceteris paribus difference between women athletes and women nonathletes.

<img width="463" alt="image" src="https://user-images.githubusercontent.com/116269829/197471802-e9188ee8-6f2f-42cd-8dd0-4cb88cd56764.png">

<img width="644" alt="image" src="https://user-images.githubusercontent.com/116269829/197471832-40e69936-ef55-4c32-a726-a97c692b08e4.png">

<img width="311" alt="image" src="https://user-images.githubusercontent.com/116269829/197472065-bc37f02f-d9e8-4c0c-870a-495e98e4f86d.png">

- The F test indicates that we can reject the null hypothesis: $\beta_{female\textunderscore ath} = \beta_{female\textunderscore nonath}$ at 5% significance level since p-value is only 0.0372.

- Another way for this question is to use another variable male_nonath:

<img width="636" alt="image" src="https://user-images.githubusercontent.com/116269829/197476350-cdb805e8-0b97-459f-8df5-4b32774560ca.png">

- Then the coefficient of female_ath is the difference between women athletes and women nonathletes.
- The t statistic for the estimated difference is 2.08 and p-value is 0.037, so we can reject the null hypothesis at 5% significance level.

v. Does the effect of sat on colgpa differ by gender? Justify your answer.

<img width="635" alt="image" src="https://user-images.githubusercontent.com/116269829/197478780-23544aaf-98dd-4ca0-9333-b713857c1b0d.png">

- The coefficient(0.0000512) of female_sat is the estimated differnece colgpa on gender. The t statistics is only 0.40 and p-value is 0.692. So there is not enough evidence that the effect of sat on colgpa differ by gender.

--------------------------------------------------------
### <strong>C7</strong> [Done]

Use the data in WAGE1 for this exercise

![image](https://user-images.githubusercontent.com/20382285/197378305-d708fb5a-1ec0-436a-aaa4-3d82a535b5a0.png)

![image](https://user-images.githubusercontent.com/20382285/197358647-d775328c-7d2e-458c-a59e-e251ac5f82b3.png)

i . estimate the gender differential when $educ = 12.5$. Compare this with the estimated differential when $educ = 0$

- when $educ = 12.5$, the gender differential : -.2267886 + (-.0055645*12.5) = -.29634485 = 29.63% in wage
- when $educ = 0$, the gender differential : -.2267886 + (-.0055645*0) = -.2267886 = 22.68% in wage
- so the gender differential in wage is -.29634485 - -.2267886 = -.06955625 $\approx$ 6.95%

ii. Run the regression used to obtain (7.18), but with female·(educ − 12.5)replacing female∙educ. How do you interpret the coefficient on female now?

![image](https://user-images.githubusercontent.com/20382285/197380504-62e52be0-26e3-4d6f-85e9-abc92b88bf8c.png)

- $\hat{log(wage)} = \beta_0 + \delta_0female + \beta_1educ + \delta_1female*educ + other factors$
- $\hat{log(wage)} = \beta_0 + \delta_0female + \beta_1educ + \delta_1female*(educ-12.5) + other factors$
- $\hat{log(wage)} = \beta_0 + \delta_0female + \beta_1educ + \delta_1female*educ + \delta_1female12.5 + other factors$
- $\hat{log(wage)} = \beta_0 + female(\delta_0 + \delta_112.5) + \beta_1educ + \delta_1female*educ + other factors$
- $\theta_0 : (\delta_0 + \delta_112.5) = (-.2267886 + -.0055645(12.5)) = -.29634485$ is coefficient on female, which means the gender differential when $educ = 12.5$. 
- $\theta_0$ is equal to the result we get in i).

iii. Is the coefficient on female in part (ii) statistically significant? Comparethis with (7.18) and comment.


- t score on female in part ii) is -8.27, p-value is 0.000. So the coefficient is significantly significant. But in (7.18) the t score of $femal \cdot edu$ is only $-0.0056/0.0131 \approx -0.43$, which is because the coefficient is the gender differential when $educ = 0$ and it is not a reasonable condition. 

--------------------------------------------------------
### <strong>C16</strong>

i. In the entire sample, what percentage of the students attend a Catholic high school? What is the average of math12 in the entire sample?

![image](https://user-images.githubusercontent.com/20382285/197380838-16a941db-843d-4cbd-9950-6b670481abd3.png)

- .06083445 $\approx$ 6.08% attend a Catholic high school
- The average of math12 is 52.13

ii. Run a simple regression of math12 on cathhs and report the results in the usual way. Interpret what you have found.

![image](https://user-images.githubusercontent.com/20382285/197380886-bb082ebc-e312-4a7c-8fcf-b4680a8469d0.png)

- $math12 = \beta_0 + \beta_1cathhs + u$
- $math12 = 51.92299 + 3.462385cathhs + u$
- $n = 7430$, $R^2 = 0.0077$

$\hat{\beta_1} = 3.462385$ is the differential in math score of those who attends catholic and non-catholic high-school
  - cathhs = 1 : $\beta_0 + \beta_1$
  - cathhs = 0 : $\beta_0$

iii. Now add the variables lfaminc, motheduc, and fatheduc to the regression from part (ii). How many observations are used in the regression? What happens to the coefficient on cathhs, along with its statistical significance?

![image](https://user-images.githubusercontent.com/20382285/197384364-4c27c9b4-92c5-4a36-a43f-c1615030c0d7.png)

- number of observation(variables) used : 7430 
- the coefficient on cathhs reduces by 1.985155 
  - from 3.462385 - 1.47723 
  - its statistical significance has also reduced but still remains significant 
    - went from $t_{cathhs}$ : 7.57 -> 3.53 
  
iv. Return to the simple regression of math12 on cathhs, but restrict the regression to observations used in the multiple regression from part (iii). Do any important conclusions change?

- to restrict the regression with respect to the simple regression in part i.
  - We treat $H_0 : \beta_2 = \beta_3 = \beta_4 = 0$

![image](https://user-images.githubusercontent.com/20382285/197384104-5ecc3310-1d39-4077-b7f6-3caafcda62c6.png)

- p-value $f_{statistic}$ : 0.0000 implies that lfaminc, motheduc and fatheduc are jointly statistically significant.
- explanatory variables : lfaminc motheduc fatheduc are statistically important in regressing the math12 score. 
 
v. To the multiple regression in part (iii), add interactions between cathhs and each of the other explanatory variables. Are the interaction termsindividually or jointly significant?

![image](https://user-images.githubusercontent.com/20382285/197384808-61ad3e55-9b6c-4147-a058-c01a055b932d.png)

![image](https://user-images.githubusercontent.com/20382285/197384817-1b41c93d-c1b1-47b5-96b8-a372a4a0e7c8.png)

- The interaction are not jointly significant because p-value of F test is 0.3037.
- which means that these intereaction terms, when included, are not important in regressing the math12 score.  

vii. Compute the average partial effect of cathhs in the model estimated in part (v). How does it compare with the coefficients on cathhs in parts (iii) and (v)?

$APE = E(Y|Cathhs==1) - E(Y|Cathhs=0) = E(Y_1) - E(Y_0) = ATE$

$math12 = \beta_0 + \beta_1cathhs + \beta_2lfaminc + \beta_3 motheduc + \beta_4 fatheduc + \beta_5clfam + \beta_6cmotheduc + \beta_7cfatheduc$
- v) APE (Caths==1) : 
  - $\partial E(math12|cathhs==1)\over\partial{cathhs}$ = $\hat{\beta_1}$
  - $\hat{\beta_1}$ - 0 = 12.50966

- iii) APE (Caths==1) :
  - $\partial E(math12|cathhs==1)\over\partial{cathhs}$ = $\hat{\beta_1}$
  - $\hat{\beta_1}$ - 0 = 1.47723

- Difference of $\beta_1$ across 2 models : 12.50966 - 1.47723 = 11.03243

--------------------------------------------------------
