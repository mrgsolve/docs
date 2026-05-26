# Prepare data.frame for input to mrgsim()

Prepare data.frame for input to mrgsim()

## Usage

``` r
numerics_only(x, quiet = FALSE, convert_lgl = FALSE)
```

## Arguments

- x:

  a input data set.

- quiet:

  logical indicating whether or not warnings should be printed.

- convert_lgl:

  if `TRUE`, convert logical columns with
  [`as.integer()`](https://rdrr.io/r/base/integer.html).
