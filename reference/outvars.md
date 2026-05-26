# Show names of current output variables

Outputs can include model compartments or variables defined in the model
that have been marked to `capture` in simulated output.

## Usage

``` r
outvars(x, unlist = FALSE)
```

## Arguments

- x:

  model object.

- unlist:

  if `TRUE` then a character vector (rather than list) is returned.

## Value

When `unlist` is `FALSE` (default) : a named list, with `cmt` showing
names of output compartments and `capture` giving names of output
variables in capture. When `unlist` is `TRUE`, then a single, unnamed
character vector of outvar names is returned.

## Examples

``` r
mod <- mrgsolve::house()
outvars(mod)
#> $cmt
#> [1] "GUT"  "CENT" "RESP"
#> 
#> $capture
#> [1] "DV" "CP"
#> 
```
