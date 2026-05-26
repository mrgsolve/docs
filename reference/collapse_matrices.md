# Collapse OMEGA or SIGMA matrix lists

If multiple `OMEGA` (or `SIGMA`) blocks were written into the model,
these can be collapsed into a single matrix. This will not change the
functionality of the model, but will alter how `OMEGA` (or `SIGMA`) are
updated, usually making it easier. This "collapsing" of the matrix list
is irreversible.

## Usage

``` r
collapse_omega(x, range = NULL, name = NULL)

collapse_sigma(x, range = NULL, name = NULL)
```

## Arguments

- x:

  a model object.

- range:

  numeric vector of length 2 specifying the range of matrices to
  collapse in case there are more than 2. The second element may be `NA`
  to indicate the length of the list of matrices.

- name:

  a new name for the collapsed matrix; note that this is the matrix
  name, not the labels which alias `ETA(n)` or `EPS(n)`; specifying a
  name will only alter how this matrix is potentially updated in the
  future.

## Value

A model object with updated `OMEGA` or `SIGMA` matrix lists.

## See also

[`collapse_matrix()`](https://mrgsolve.org/docs/reference/collapse_matrix.md)

## Examples

``` r
code <- '
$OMEGA 1 2 3
$OMEGA 4 5
$OMEGA 6 7 8 9
'

mod <- mcode("collapse-example", code, compile = FALSE)
revar(mod)
#> $omega
#> $...
#>     [,1] [,2] [,3]
#> 1:     1    0    0
#> 2:     0    2    0
#> 3:     0    0    3
#> 
#> $...
#>     [,1] [,2]
#> 4:     4    0
#> 5:     0    5
#> 
#> $...
#>     [,1] [,2] [,3] [,4]
#> 6:     6    0    0    0
#> 7:     0    7    0    0
#> 8:     0    0    8    0
#> 9:     0    0    0    9
#> 
#> 
#> $sigma
#> No matrices found
#> 
collapse_omega(mod) %>% omat()
#> $...
#>     [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9]
#> 1:     1    0    0    0    0    0    0    0    0
#> 2:     0    2    0    0    0    0    0    0    0
#> 3:     0    0    3    0    0    0    0    0    0
#> 4:     0    0    0    4    0    0    0    0    0
#> 5:     0    0    0    0    5    0    0    0    0
#> 6:     0    0    0    0    0    6    0    0    0
#> 7:     0    0    0    0    0    0    7    0    0
#> 8:     0    0    0    0    0    0    0    8    0
#> 9:     0    0    0    0    0    0    0    0    9
#> 
collapse_omega(mod, range = c(2,3), name = "new_matrix") %>% omat()
#> $...
#>     [,1] [,2] [,3]
#> 1:     1    0    0
#> 2:     0    2    0
#> 3:     0    0    3
#> 
#> $new_matrix
#>     [,1] [,2] [,3] [,4] [,5] [,6]
#> 4:     4    0    0    0    0    0
#> 5:     0    5    0    0    0    0
#> 6:     0    0    6    0    0    0
#> 7:     0    0    0    7    0    0
#> 8:     0    0    0    0    8    0
#> 9:     0    0    0    0    0    9
#> 
collapse_omega(mod, range = c(2,NA), name = "new_matrix") %>% omat()
#> $...
#>     [,1] [,2] [,3]
#> 1:     1    0    0
#> 2:     0    2    0
#> 3:     0    0    3
#> 
#> $new_matrix
#>     [,1] [,2] [,3] [,4] [,5] [,6]
#> 4:     4    0    0    0    0    0
#> 5:     0    5    0    0    0    0
#> 6:     0    0    6    0    0    0
#> 7:     0    0    0    7    0    0
#> 8:     0    0    0    0    8    0
#> 9:     0    0    0    0    0    9
#> 
```
