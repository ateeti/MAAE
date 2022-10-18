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

$\ R^2 = {SSE / SST} = 1 - {(SSR/SST)} $

where:

  $\ SSE = \sum{(Yi - \hat{Y})^2}$\
  $\ SSR = \sum{(\hat{Yi} - \bar{Y})^2}$
    
    Using SSR/SST:
    
    . di 236190226/635065396
       = .37191481

$R^2 = 37.19 %$ price could be explained my this model\
Adjusted $R^2 = 1 - (SSR/d.f.) / (SST/d.f.)$

## Finding ROOT MSE

    . di 398875170/69
    5780799.6

. di (398875170/69)^(1/2)
2404.3293

. **when mpg ∆ by 1 unit, price will change by -87.95838

. ** partialling out all other xs

. ** by FWT

. ** If mpg increase by 5 unit, and headroom reduce 20 inch, weight increase by 50kg, and the length reduce by 6 inch, what\ would be the impact on the price of this car ?

. di (-87.958385) + (-20-490.9667) + (504.335045) + (-6-94.49651)
10163.273

. di (-87.958385) + (20-490.9667) + (504.335045) + (6-94.49651)
-10609.353

. * di (-87.95838*5) + (-20-490.9667) + (504.335045) + (-6-94.49651) // correct\

. predict price_hat
(option xb assumed; fitted values)\

. br

. predict e, residual

. br
