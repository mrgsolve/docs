# Get the times at which the model will be evaluated

Get the times at which the model will be evaluated

## Usage

``` r
stime(x, ...)
```

## Arguments

- x:

  a model object or a mrgsims object.

- ...:

  not used.

## Value

A sorted vector of unique simulation times from the time grid in the
model object.

## Details

Simulation times include the sequence of times created from `start`,
`end`, and `delta` and the vector of times found in `add`.

Making `end` negative (e.g. -1) will omit the `start-end-delta`
sequence. Negative values are discarded from the result.

## Examples

``` r
## example("stime", package="mrgsolve")

mod <- mrgsolve::house(end = 12, delta = 2, add = c(11,13,15))

stime(mod)
#>  [1]  0  2  4  6  8 10 11 12 13 15

update(mod, end = -1) %>% stime()
#> [1] 11 13 15
```
