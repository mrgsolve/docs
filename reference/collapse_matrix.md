# Collapse the matrices of a matlist object

This function is called by
[`collapse_omega()`](https://mrgsolve.org/docs/reference/collapse_matrices.md)
and
[`collapse_sigma()`](https://mrgsolve.org/docs/reference/collapse_matrices.md)
to convert multiple matrix blocks into a single matrix block. This
"collapsing" of the matrix list is irreversible.

## Usage

``` r
collapse_matrix(x, range = NULL, name = NULL)
```

## Arguments

- x:

  an object that inherits from `matlist`; this object is most frequently
  extracted from a model object using
  [`omat()`](https://mrgsolve.org/docs/reference/omega.md) or
  [`smat()`](https://mrgsolve.org/docs/reference/sigma.md) for `OMEGA`
  and `SIGMA`, respectively.

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

An update `matlist` object (either `omegalist` or `sigmalist`).

## See also

[`collapse_omega()`](https://mrgsolve.org/docs/reference/collapse_matrices.md),
[`collapse_sigma()`](https://mrgsolve.org/docs/reference/collapse_matrices.md),
[`omat()`](https://mrgsolve.org/docs/reference/omega.md),
[`smat()`](https://mrgsolve.org/docs/reference/sigma.md)

## Examples

``` r
omega <- omat(list(dmat(1, 2), dmat(3, 4, 5)))
omega
#> $...
#>     [,1] [,2]
#> 1:     1    0
#> 2:     0    2
#> 
#> $...
#>     [,1] [,2] [,3]
#> 3:     3    0    0
#> 4:     0    4    0
#> 5:     0    0    5
#> 
collapse_matrix(omega)
#> $...
#>     [,1] [,2] [,3] [,4] [,5]
#> 1:     1    0    0    0    0
#> 2:     0    2    0    0    0
#> 3:     0    0    3    0    0
#> 4:     0    0    0    4    0
#> 5:     0    0    0    0    5
#> 
```
