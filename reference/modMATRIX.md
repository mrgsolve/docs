# Create a matrix

Create a matrix

## Usage

``` r
modMATRIX(
  x,
  use = TRUE,
  block = FALSE,
  correlation = FALSE,
  digits = -1,
  context = "matlist",
  ...
)
```

## Arguments

- x:

  data for building the matrix. Data in `x` are assumed to be
  on-diagonal elements if `block` is `FALSE` and lower-triangular
  elements if `block` is `TRUE`

- use:

  logical; if FALSE, all matrix elements are set to 0

- block:

  logical; if TRUE, try to make a block matrix; diagonal otherwise

- correlation:

  logical; if TRUE, off diagonal elements are assumed to be correlations
  and converted to covariances; if correlation is TRUE, then block is
  set to TRUE

- digits:

  if value of this argument is greater than zero, the matrix is passed
  to signif (along with digits) prior to returning

- context:

  the working context

- ...:

  passed along

## Examples

``` r
modMATRIX("1 2.2 333")
#>      [,1] [,2] [,3]
#> [1,]    1  0.0    0
#> [2,]    0  2.2    0
#> [3,]    0  0.0  333
modMATRIX("1 1.1 2.2", block=TRUE)
#>      [,1] [,2]
#> [1,]  1.0  1.1
#> [2,]  1.1  2.2
modMATRIX("23 234 234 5234", use=FALSE)
#>      [,1] [,2] [,3] [,4]
#> [1,]    0    0    0    0
#> [2,]    0    0    0    0
#> [3,]    0    0    0    0
#> [4,]    0    0    0    0

ans <- modMATRIX("1.1 0.657 2.2", correlation=TRUE, block=TRUE)
ans
#>          [,1]     [,2]
#> [1,] 1.100000 1.022052
#> [2,] 1.022052 2.200000
cov2cor(ans)
#>       [,1]  [,2]
#> [1,] 1.000 0.657
#> [2,] 0.657 1.000
```
