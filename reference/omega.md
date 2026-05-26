# Manipulate OMEGA matrices

The primary function is `omat()` that can be used to both get the
`$OMEGA` matrices out of a model object and to update `$OMEGA` matrices
in a model object.

## Usage

``` r
omat(.x, ...)

# S4 method for class 'missing'
omat(.x, ...)

# S4 method for class 'matrix'
omat(.x, ..., labels = list())

# S4 method for class 'NULL'
omat(.x, ...)

# S4 method for class 'list'
omat(.x, ...)

# S4 method for class 'omegalist'
omat(.x, ...)

# S4 method for class 'mrgmod'
omat(.x, ..., make = FALSE, open = FALSE)

# S4 method for class 'mrgsims'
omat(.x, make = FALSE, ...)
```

## Arguments

- .x:

  a matrix, list of matrices or `matlist` object.

- ...:

  passed to other functions, including
  [`modMATRIX()`](https://mrgsolve.org/docs/reference/modMATRIX.md).

- labels:

  character vector of names for `$OMEGA` elements; must be equal to
  number of rows/columns in the matrix.

- make:

  logical; if `TRUE`, matrix list is rendered into a single matrix.

- open:

  passed to
  [`merge.list()`](https://mrgsolve.org/docs/reference/merge.md).

- x:

  `matlist` object.

## See also

[`smat()`](https://mrgsolve.org/docs/reference/sigma.md),
[`dmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md),
[`bmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md),
[`cmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md)

## Examples

``` r
# example("omega")
mat1 <- matrix(1)
mat2 <- diag(c(1,2,3))
mat3 <- matrix(c(0.1, 0.002, 0.002, 0.5), 2,2)
mat4 <- dmat(0.1, 0.2, 0.3, 0.4)

omat(mat1)
#> $...
#>     [,1]
#> 1:     1
#> 
omat(mat1, mat2, mat3)
#> $...
#>     [,1]
#> 1:     1
#> 
#> $...
#>     [,1] [,2] [,3]
#> 2:     1    0    0
#> 3:     0    2    0
#> 4:     0    0    3
#> 
#> $...
#>      [,1]  [,2]
#> 5:  0.100 0.002
#> 6:  0.002 0.500
#> 
omat(A = mat1, B = mat2, C = mat3)
#> $A
#>     [,1]
#> 1:     1
#> 
#> $B
#>     [,1] [,2] [,3]
#> 2:     1    0    0
#> 3:     0    2    0
#> 4:     0    0    3
#> 
#> $C
#>      [,1]  [,2]
#> 5:  0.100 0.002
#> 6:  0.002 0.500
#> 

mod <- mrgsolve::house() %>% omat(mat4)

omat(mod)
#> $...
#>         [,1] [,2] [,3] [,4]
#> ECL:     0.1  0.0  0.0  0.0
#> EVC:     0.0  0.2  0.0  0.0
#> EKA:     0.0  0.0  0.3  0.0
#> EKOUT:   0.0  0.0  0.0  0.4
#> 
omat(mod, make = TRUE)
#>      [,1] [,2] [,3] [,4]
#> [1,]  0.1  0.0  0.0  0.0
#> [2,]  0.0  0.2  0.0  0.0
#> [3,]  0.0  0.0  0.3  0.0
#> [4,]  0.0  0.0  0.0  0.4
as.matrix(omat(mod))
#>      [,1] [,2] [,3] [,4]
#> [1,]  0.1  0.0  0.0  0.0
#> [2,]  0.0  0.2  0.0  0.0
#> [3,]  0.0  0.0  0.3  0.0
#> [4,]  0.0  0.0  0.0  0.4
```
