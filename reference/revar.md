# Get model random effect variances and covariances

Use this function to extract both OMEGA and SIGMA matrices from a model
object. Typical use is for display on the R console.

## Usage

``` r
revar(x, ...)

# S4 method for class 'mrgmod'
revar(x, ...)
```

## Arguments

- x:

  model object.

- ...:

  passed along.

## Value

A named list containing `omega` and `sigma` matrices.

## Examples

``` r
mod <- mrgsolve::house()
revar(mod)
#> $omega
#> $...
#>         [,1] [,2] [,3] [,4]
#> ECL:       0    0    0    0
#> EVC:       0    0    0    0
#> EKA:       0    0    0    0
#> EKOUT:     0    0    0    0
#> 
#> 
#> $sigma
#> $...
#>        [,1]
#> EXPO:     0
#> 
#> 
```
