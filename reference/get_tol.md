# Extract rtol and atol information from a model object

Extract rtol and atol information from a model object

## Usage

``` r
get_tol(x)

get_tol_list(x)
```

## Arguments

- x:

  a model object.

## Value

A data frame (`get_tol()`) or a named list (`get_tol_list()`).

## See also

[`reset_tol()`](https://mrgsolve.org/docs/reference/reset_tol.md),
[`custom_tol()`](https://mrgsolve.org/docs/reference/custom_tol.md),
[`use_custom_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md),
[`use_scalar_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md)

## Examples

``` r
mod <- house()
get_tol(mod)
#>    cmt custom_rtol custom_atol scalar_rtol scalar_atol
#> 1  GUT          NA          NA       1e-08       1e-08
#> 2 CENT          NA          NA       1e-08       1e-08
#> 3 RESP          NA          NA       1e-08       1e-08
get_tol_list(mod)
#> $custom_rtol
#> $custom_rtol$GUT
#> [1] NA
#> 
#> $custom_rtol$CENT
#> [1] NA
#> 
#> $custom_rtol$RESP
#> [1] NA
#> 
#> 
#> $custom_atol
#> $custom_atol$GUT
#> [1] NA
#> 
#> $custom_atol$CENT
#> [1] NA
#> 
#> $custom_atol$RESP
#> [1] NA
#> 
#> 
#> $scalar_rtol
#> $scalar_rtol$GUT
#> [1] 1e-08
#> 
#> $scalar_rtol$CENT
#> [1] 1e-08
#> 
#> $scalar_rtol$RESP
#> [1] 1e-08
#> 
#> 
#> $scalar_atol
#> $scalar_atol$GUT
#> [1] 1e-08
#> 
#> $scalar_atol$CENT
#> [1] 1e-08
#> 
#> $scalar_atol$RESP
#> [1] 1e-08
#> 
#> 
```
