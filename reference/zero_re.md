# Zero out random effects in a model object

Sets all elements of the OMEGA or SIGMA matrix to zero.

## Usage

``` r
zero_re(.x, ...)

# S4 method for class 'mrgmod'
zero_re(.x, ...)
```

## Arguments

- .x:

  a model object.

- ...:

  which matrix to zero out; pass `omega` to just zero out `omega`,
  `sigma` to just zero out `sigma`; passing nothing will zero out both.

## Value

An updated object with elements of OMEGA and/or SIGMA set to zero.

## Examples

``` r
mod <- house()
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
mod <- zero_re(mod)
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

if (FALSE) { # \dontrun{
mod <- modlib("popex", compile = FALSE)
mod <- zero_re(mod, omega)
revar(mod)
} # }
```
