# MAAE

C1.
A problem of interest to health officials (and others) is to determine the effects of smoking during pregnancy on infant health. One measure of infant health is birth weight; a birth weight that is too low can put an infant at risk for contracting various illnesses. Since factors other than cigarette smoking that affect birth weight are likely to be correlated with smoking, we should take those factors into account. For example, higher income generally results in access to better prenatal care, as well as better nutrition for the mother. An equation that recognizes this is

$bwght = \beta_0 + \beta_1 cigs + \beta_2 faminc + u$

i. What is the most likely sign for $\beta_2$ ?

- the most likely sign for $\beta_2$ is positive, as stated, higher income generally results in access to better prenatal care,
  as well as better nutrition for the mother. 
    - prenatal care
    - food supplementary, etc.

ii. Do you think cigs and faminc are likely to be correlated? Explain why the correlation might be positive or negative.

- It could either be positive or negative depending on the mother's behavior.
- If one chooses to spend his/her income on cigs then faminc and cigs would be positively correlated,
    - the more the faminc, the more the cigs   
- but if one chooses to spend on prenatal care, better nutrition, then faminc and cigs would be negatively correlated.
    - the more the faminc, the less the cigs

iii. Now, estimate the equation with and without faminc, using the data in BWGHT. Report the results in equation form, including the sample size and R-squared. 
Discuss your results, focusing on whether adding faminc substantially changes the estimated effect of cigs on bwght.

![Ch3 c1 sub3](https://user-images.githubusercontent.com/20382285/196757721-cd509c8d-0b9a-49d7-a45d-d530776af77f.JPG)

equation without faminc :
$\ bwght = 119.7719 - 0.5137721 \beta_1$

equation with faminc :
$\ bwght = 116.9741 - 0.4634075 \beta_1 + 0.0927647 \beta_2$

- from observed data, we see that the $\triangle \beta_1$ reduces by $-0.5137721 - -0.4634075 = -0.0503646
- this determines that, faminc is negatively correlated to cigs:
  - by estimation, when a mother has faminc -> the less number of cigs being smoked

-----------------------------------------------------------------------------------------------------------------------------

C2.
Use the data in HPRICE1 to estimate the model

$price = \beta_0 + \beta_1 sqrft + \beta_2 bdrms + u$

where price is the house price measured in thousands of dollars.

i. Write out the results in equation form.

- $\ price = -19.315 + 0.1284362 \beta_1 + 15.19819 \beta_2$

ii. What is the estimated increase in price for a house with one more bedroom, holding square footage constant?

- $\ \hat{price} = (\triangle\beta_0 = 0 ) + (\triangle\beta_1 = 0 ) + 15.19819(\triangle\beta_2 = 1$)
- On average, estimated increase in price for a house with one more bedroom = $\beta_1$\
    = 15.19819 thousands of dollars

iii. What is the estimated increase in price for a house with an additional bedroom that is 140 square feet in size? Compare this to your answer in part (ii).

- $\ \hat{price} = (\triangle\beta_0 = 0 ) + 0.1284362(\triangle\beta_1 = 140 ) + 15.19819(\triangle\beta_2 = 1$)
- $\ \hat{price} = (0.1284362 * 140) + (15.19819 * 1)$
- $\ \hat{price} = 33.179258$ thousands of dollars (excluding $\beta_0$ since question is asking for estimated not predicted price)

iv. What percentage of the variation in price is explained by square footage and number of bedrooms?

- $\ R^2 = 0.6319 \approxeq 63.19$ % of variation in price is explained by square footage and number of bedrooms. 

v. The first house in the sample has $sqrft = 2438$ and $bdrms = 4$ . Find the predicted selling price for this house from the OLS regression line.

- $\ \hat{price} = -19.315 + 0.1284362(2438) + 15.19819(4)$
- $\ \hat{price} = -19.315 + 313.1274556 + 60.79276$
- $\ \hat{price} = 354.6052156$ thousands of dollars

vi. The actual selling price of the first house in the sample was $300,000 ( price = 300 ). Find the residual for this house. Does it suggest that the buyer underpaid or overpaid for the house?

- Residual = $Y_i - (\hat{Y} = 354.6052156)$
- Residual = $300 - 354.6052156$
- Residual = $-54.6052156$
    - It suggests that the buyer overpaid for the house by $\approxeq$ 54 thousands of dollars

-----------------------------------------------------------------------------------------------------------------------------

C3.
The file CEOSAL2 contains data on 177 chief executive officers and can be used to examine the effects of firm performance on CEO salary.

i. Estimate a model relating annual salary to firm sales and market value. Make the model of the constant elasticity variety for both independent variables. Write the results out in equation form.

- to achieve the model of the constant elasticity, must take log on all variables. 

![Ch3 c3 sub1](https://user-images.githubusercontent.com/20382285/196773084-31caf2ae-d948-4873-97ac-8a9cc9836115.JPG)

- normal equation:
  - $salary = 716.5762 + 0.0164994sales + 0.0252906mktval$
- elasticity eqn:
  - $log(salary) = 4.620917 + 0.1621283log(sales) + 0.106708log(mktval)$

ii. Add profits to the model from part (i). Why can this variable not be included in logarithmic form? Would you say that these firm performance variables explain most of the variation in CEO salaries?

- taking log on profits resulting in -> 9 missing values generated
- we tested and found out that these 9 missing values are the ones < 0 (implies that the values are in negative)
  - using this command : . counf if profit < 0 and the result returns 9
  - so the reason this variable(profits) can not be included in logarithmic form is because some values are negative.
- 

iii. Add the variable ceoten to the model in part (ii). What is the estimated percentage return for another year of CEO tenure, holding other factors fixed?

iv. Find the sample correlation coefficient between the variables log(mktval) and profits. Are these variables highly correlated? What does this say about the OLS estimators?
