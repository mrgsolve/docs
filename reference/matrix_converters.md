# Coerce R objects to block or diagonal matrices

These are simple functions that may be helpful to create the matrix
objects that mrgsolve expects. Functions are named based on whether they
create a diagonal matrix (`d`), a block matrix (`b`), or a a correlation
matrix (`c`).

## Usage

``` r
as_bmat(x, ...)

# S4 method for class 'list'
as_bmat(x, ...)

# S4 method for class 'numeric'
as_bmat(x, pat = "*", ...)

# S4 method for class 'data.frame'
as_bmat(x, pat = "*", cols = NULL, ...)

# S4 method for class 'ANY'
as_bmat(x, ...)

as_dmat(x, ...)

# S4 method for class 'list'
as_dmat(x, ...)

# S4 method for class 'ANY'
as_dmat(x, ...)

# S4 method for class 'numeric'
as_dmat(x, pat = "*", ...)

# S4 method for class 'data.frame'
as_dmat(x, pat = "*", cols = NULL, ...)

as_cmat(x, ...)
```

## Arguments

- x:

  data frame or list.

- ...:

  arguments passed to
  [`dmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md) or
  [`cmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md).

- pat:

  regular expression, character.

- cols:

  column names to use instead of `pat`.

## Value

A numeric matrix for list and numeric methods. For data.frames, a list
of matrices are returned.

## Details

Use `as_dmat()` to create a diagonal matrix, `as_bmat()` to create a
block matrix, and `as_cmat()` to create a block matrix where
off-diagonal elements are understood to be correlations rather than
covariances. `as_cmat()` uses `as_bmat()` to form the matrix and then
converts off-diagonal elements to covariances before returning.

The methods for `data.frame` will work down the rows of the data frame
and make the appropriate matrix from the data in each row. The result is
a list of matrices.

## See also

[`bmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md),
[`dmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md),
[`cmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md)

## Examples

``` r
df <- data.frame(
  OMEGA1.1 = c(1,2),
  OMEGA2.1 = c(11,22),
  OMEGA2.2 = c(3,4),
  SIGMA1.1 = 1,
  FOO=-1
)

as_bmat(df, "OMEGA")
#> [[1]]
#>      [,1] [,2]
#> [1,]    1   11
#> [2,]   11    3
#> 
#> [[2]]
#>      [,1] [,2]
#> [1,]    2   22
#> [2,]   22    4
#> 
as_dmat(df,"SIGMA")
#> [[1]]
#>      [,1]
#> [1,]    1
#> 
#> [[2]]
#>      [,1]
#> [1,]    1
#> 
as_dmat(df[1,],"OMEGA")
#> [[1]]
#>      [,1] [,2] [,3]
#> [1,]    1    0    0
#> [2,]    0   11    0
#> [3,]    0    0    3
#> 
```
