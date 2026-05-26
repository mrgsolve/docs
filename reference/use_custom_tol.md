# Set up a model object to use either scalar or custom tolerances

Call `use_custom_tol()` to use custom relative and absolute tolerances
in a model; call `use_scalar_tol()` to revert to the traditional
configuration where a single `rtol` and `atol` are applied to all
compartments.

## Usage

``` r
use_custom_tol(x)

use_scalar_tol(x)
```

## Arguments

- x:

  a model object.

## Value

An updated model object.

## Details

If customized tolerances have not been initialized yet, they will be,
assigning the current `rtol` or `atol` for every compartment. These
default values can be updated using
[`custom_rtol()`](https://mrgsolve.org/docs/reference/custom_tol.md),
[`custom_atol()`](https://mrgsolve.org/docs/reference/custom_tol.md), or
[`custom_tol()`](https://mrgsolve.org/docs/reference/custom_tol.md).

## See also

[`custom_tol()`](https://mrgsolve.org/docs/reference/custom_tol.md),
[`reset_tol()`](https://mrgsolve.org/docs/reference/reset_tol.md),
[`get_tol()`](https://mrgsolve.org/docs/reference/get_tol.md)

## Examples

``` r
mod <- house()

mod <- use_custom_tol(mod)
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
#>   solver:        rtol: -- atol: -- itol: 4 (custom)
#> ------------------------------------------------------

mod <- use_scalar_tol(mod)
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
#>   solver:        rtol: 1e-08 atol: 1e-08 itol: 1 (scalar)
#> ------------------------------------------------------
```
