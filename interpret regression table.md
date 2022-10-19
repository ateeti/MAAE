# MAAE_lecture10

![lecture 10](https://user-images.githubusercontent.com/20382285/196508065-57c5c2e8-7567-4d13-974f-d6ea4e668a00.JPG)

## Finding F score

$\ F = {SSE /d.f. \over SSR /d.f.}$
    
    Numerator: (model,SS) / (model,df)
    
    . di 236190226/4
        = 59047557
    
    Denomenator: (residual,SS) / (residual,df)
    
    . di 398875170/69
        = 5780799.6
        
    Numerator / Denomenator :
        
    . di (236190226/4)/(398875170/69)
        = 10.214427
        
## Finding R-squared 

* $\ R^2 = {SSE / SST} = 1 - {(SSR/SST)} $

where:

  * $\ SSE = \sum{(Yi - \hat{Y})^2}$
  * $\ SSR = \sum{(\hat{Yi} - \bar{Y})^2}$
    
        Using SSE/SST:
    
        . di 236190226/635065396
           = .37191481
       
        Using 1 - {(SSR/SST)}:
    
        . di 1 - (398875170/635065396)
            = .37191481

$R^2 = 37.19 %$ price could be explained my this model\
Adjusted $R^2 = 1 - [ (SSR/d.f.) / (SST/d.f.) ]$

    Using Adjusted R-squared:
    
    . di 1 - [(398875170/69) / (635065396/73)]
        = .33550407

## Finding MS

![lecture 10](https://user-images.githubusercontent.com/20382285/196508065-57c5c2e8-7567-4d13-974f-d6ea4e668a00.JPG)

MS: are the Mean Squares, the Sum of Squares divided by their respective d.f.

For example : 

we know that $\ SS_{explained} (SSE) = 236190226$ and its d.f. = 4

    236,190,226 / 4 = 59,047,556.5
 
we know that $\ SS_{residuals} (SSR) = 236190226$ and its d.f. = 4

    398,875,170 / 69 = 5,780,799.5652173913043478260869565

## Finding ROOT_MSE
  
  * $\ ROOT MSE = \sqrt{\sigma^2} = \sqrt{ \sum{ \hat{\epsilon_i} } \over {n-number(parameter)}  }$
  * $\ \sum{ \hat{\epsilon_i} } = \sum{ \hat{u}_i } = SSR $

Using $\sqrt{SSR \over n-number(parameter)} = \sqrt{SSR \over n-5} $
    
    . di (398875170/69)^(1/2)
        = 2404.3293
        
    or just use MS of SSR and square root it
    
$MSE = \sqrt{MS_{residuals}}$

# Bottom part of the table

![lecture 10](https://user-images.githubusercontent.com/20382285/196508065-57c5c2e8-7567-4d13-974f-d6ea4e668a00.JPG)

## To interpret coefficient values:

$\ Y_i = \beta_0 + \beta_1 mpg_{1i} + \beta_2 headroom_{2i} + \beta_3 weight_{3i} + \beta_4 length_{4i} + \epsilon_i$

Consider $\beta_1$ :

        . when mpg ∆ by 1 unit, price will change by -87.95838
        . partialling out all other xs
        . by FWT
       
If mpg increase by 5 unit, and headroom reduce 20 inch, weight increase by 50kg,\
and the length reduce by 6 inch, what would be the impact on the price of this car ?

        by regression model:
        . di (-87.95838*5) + (-20*-490.9667) + (50*4.335045) + (-6*-94.49651)
            = 10163.273
        
        by intuition:
        . di (-87.95838*5) + (20*-490.9667) + (50*4.335045) + (6*-94.49651)
            = -10609.353
            
## Finding t

$\ t = {{\hat{\beta_i} - \beta_i} \over \sqrt{Var(\hat{\beta_i})}}$ where $\ \sqrt{Var(\hat{\beta_i})} = std. error $

-------------------------------------------------------------
Suppose:

$\ H_0 : \beta_1 = 0 $\
$\ H_1 : \beta_1 \neq 0$

by $H_0$ , then $\ t = {{\hat{\beta_1} - 0} \over \sqrt{Var(\hat{\beta_1})}}$

From table : we know that

* $\hat{\beta_1} = -87.95838$ , 
* $std.err(mpg) = 83.5927$

$\ t = {{-87.95838} \over {83.5927}} = -1.05$
-------------------------------------------------------------

$\ H_0 : \beta_2 = 0 $\
$\ H_1 : \beta_2 \neq 0$

by $H_0$ , then $\ t = {{\hat{\beta_2} - 0} \over \sqrt{Var(\hat{\beta_2})}}$

From table : we know that

* $\hat{\beta_2} = -490.9667$ , 
* $std.err(headroom) = 388.48927$

$\ t = {{-490.9667} \over {388.48927}} = -1.26$

-------------------------------------------------------------

$\ H_0 : \beta_3 = 0 $\
$\ H_1 : \beta_3 \neq 0$

by $H_0$ , then $\ t = {{\hat{\beta_3} - 0} \over \sqrt{Var(\hat{\beta_3})}}$

From table : we know that

* $\hat{\beta_3} = 4.335045$ , 
* $std.err(weight) = 1.162745$

$\ t = {{4.335045} \over {1.162745}} = 3.73$
