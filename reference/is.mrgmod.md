# Check if an object is a model object

The function checks to see if the object is either `mrgmod` or
`packmod`.

## Usage

``` r
is.mrgmod(x)
```

## Arguments

- x:

  any object

## Value

`TRUE` if the object inherits from either `mrgmod` or `packmod` class.

## Examples

``` r
mod <- mrgsolve::house()
is.mrgmod(mod)
#> [1] TRUE
```
