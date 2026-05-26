# Get the compartment number from a compartment name

Get the compartment number from a compartment name

## Usage

``` r
cmtn(x, ...)

# S4 method for class 'mrgmod'
cmtn(x, tag, ...)
```

## Arguments

- x:

  model object.

- ...:

  not used.

- tag:

  compartment name.

## Examples

``` r
mod <- mrgsolve::house()
cmtn(mod, "CENT")
#> [1] 2
```
