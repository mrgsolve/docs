# Reset all model tolerances

These functions reset both scalar and customized values for both
relative and absolute tolerances. All functions reset tolerances to a
single, common `rtol` or `atol`. The functions do *not* change which
tolerance configuration is used for simulation (e.g., scalar or
customized); see
[`use_custom_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md)
and
[`use_scalar_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md)
to make that change in the model object.

## Usage

``` r
reset_tol(x, rtol = NULL, atol = NULL)

reset_rtol(x, rtol = NULL)

reset_atol(x, atol = NULL)
```

## Arguments

- x:

  a model object.

- rtol:

  global relative tolerance for both scalar and customized
  configurations; if not supplied, the current model's scalar `rtol`
  value is used.

- atol:

  global absolute tolerance for both scalar and customized
  configurations; if not supplied, the current model's scalar `atol`
  value is used.

## Value

An updated model object.

## See also

[`custom_tol()`](https://mrgsolve.org/docs/reference/custom_tol.md),
[`use_custom_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md),
[`use_scalar_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md),
[`get_tol()`](https://mrgsolve.org/docs/reference/get_tol.md)

## Examples

``` r
mod <- house()
mod <- reset_tol(mod, rtol = 1e-6, atol = 1e-10)
mod
#> 
#> 
#> --------------  source: housemodel.cpp  --------------
#> 
#>   project: /private/var/fol...solve/project
#>   shared object: mrgsolve 
#> 
#>   time:          start: 0 end: 120 delta: 0.25
#>                  add: <none>
#>   compartments:  GUT CENT RESP [3]
#>   parameters:    CL VC KA F1 D1 WTCL WTVC SEXCL SEXVC
#>                  KIN KOUT IC50 WT SEX [14]
#>   captures:      DV CP [2]
#>   omega:         4x4 
#>   sigma:         1x1 
#> 
#>   solver:        rtol: 1e-06 atol: 1e-10 itol: 1 (scalar)
#> ------------------------------------------------------
```
