# Validate and prepare data sets for simulation

This function is called by
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md) and friends
to check and prepare input data sets for simulation. Users may also call
this function to pre-validate data when the same data set is used for
repeated simulation.

## Usage

``` r
valid_data_set(x, m = NULL, verbose = FALSE, quiet = FALSE)

valid_data_set.matrix(x, verbose = FALSE)
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

A matrix with non-numeric columns dropped; if x is a data.frame with
character `cmt` column comprised of valid compartment names and `m` is a
model object, the `cmt` column will be converted to the corresponding
compartment number.

## Details

An error will be issued when

- non-numeric data is found in columns sharing names with model
  parameters

- non-numeric data is found in reserved data items related to dosing
  (see `mrgsolve:::GLOBALS$CARRY_TRAN`)

- a column is found that is "internally classed", including columns that
  inherit from `integer64` (see
  [`is.object()`](https://rdrr.io/r/base/is.object.html))

## See also

[`valid_idata_set()`](https://mrgsolve.org/docs/reference/valid_idata_set.md),
[`idata_set()`](https://mrgsolve.org/docs/reference/idata_set.md),
[`data_set()`](https://mrgsolve.org/docs/reference/data_set.md)

## Examples

``` r

mod <- mrgsolve::house()

data(exTheoph)

d <- valid_data_set(exTheoph, mod)
```
