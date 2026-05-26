# Create matrices from vector input

These functions are simple utilities for creating diagonal, block or
correlation matrices.

## Usage

``` r
bmat(..., correlation = FALSE, digits = -1)

cmat(..., digits = -1)

dmat(...)
```

## Arguments

- ...:

  matrix data.

- correlation:

  logical; if `TRUE`, off-diagonal elements are assumed to be
  correlations and converted to covariances.

- digits:

  if greater than zero, matrix is passed to
  [`signif()`](https://rdrr.io/r/base/Round.html) (along with digits)
  prior to returning.

## Value

A matrix.

## Details

`bmat()` makes a block matrix. `cmat()` makes a correlation matrix.
`dmat()` makes a diagonal matrix.

## See also

[`as_bmat()`](https://mrgsolve.org/docs/reference/matrix_converters.md),
[`as_dmat()`](https://mrgsolve.org/docs/reference/matrix_converters.md)

## Examples

``` r

dmat(1,2,3)/10
#>      [,1] [,2] [,3]
#> [1,]  0.1  0.0  0.0
#> [2,]  0.0  0.2  0.0
#> [3,]  0.0  0.0  0.3

bmat(0.5,0.01,0.2)
#>      [,1] [,2]
#> [1,] 0.50 0.01
#> [2,] 0.01 0.20

cmat(0.5, 0.87,0.2)
#>           [,1]      [,2]
#> [1,] 0.5000000 0.2751182
#> [2,] 0.2751182 0.2000000
```
