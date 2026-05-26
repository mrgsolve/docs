# Validate and prepare idata data sets for simulation

This function is called by
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md) and friends
to check and prepare input data sets for simulation. Users may also call
this function to pre-validate data when the same data set is used for
repeated simulation.

## Usage

``` r
valid_idata_set(x, m, verbose = FALSE, quiet = FALSE)
```

## Arguments

- x:

  data.frame or matrix.

- m:

  a model object.

- verbose:

  logical.

- quiet:

  if `TRUE`, messages will be suppressed.

## Value

A numeric matrix with class `valid_idata_set`.

## Details

An error will be issued when

- non-numeric data is found in columns sharing names with model
  parameters

- a column is found that is internally classed, including columns that
  inherit from `integer64` (see
  [`is.object()`](https://rdrr.io/r/base/is.object.html))

## See also

[`valid_data_set()`](https://mrgsolve.org/docs/reference/valid_data_set.md),
[`idata_set()`](https://mrgsolve.org/docs/reference/idata_set.md),
[`data_set()`](https://mrgsolve.org/docs/reference/data_set.md)
