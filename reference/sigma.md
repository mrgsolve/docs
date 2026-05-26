# Manipulate SIGMA matrices

The primary function is `smat()` which can be used to both get the
`$SIGMA` matrices out of a model object and to update `$SIGMA` matrices
in a model object.

## Usage

``` r
smat(.x, ...)

# S4 method for class 'missing'
smat(.x, ...)

# S4 method for class 'matrix'
smat(.x, ..., labels = list())

# S4 method for class 'list'
smat(.x, ...)

# S4 method for class 'sigmalist'
smat(.x, ...)

# S4 method for class 'mrgmod'
smat(.x, ..., make = FALSE, open = FALSE)

# S4 method for class 'NULL'
smat(.x, ...)

# S4 method for class 'mrgsims'
smat(.x, make = FALSE, ...)
```

## Arguments

- .x:

  a matrix, list of matrices or `matlist` object.

- ...:

  passed to other functions, including
  [`modMATRIX()`](https://mrgsolve.org/docs/reference/modMATRIX.md).

- labels:

  character vector of names for `$SIGMA` elements; must be equal to
  number of rows/columns in the matrix.

- make:

  logical; if `TRUE`, matrix list is rendered into a single matrix.

- open:

  passed to
  [`merge.list()`](https://mrgsolve.org/docs/reference/merge.md).

- x:

  `matlist` object.

## See also

[`dmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md),
[`bmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md),
[`cmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md)

## Examples

``` r
## example("sigma")
mat1 <- matrix(1)
mat2 <- diag(c(1,2))
mat3 <- matrix(c(0.1, 0.002, 0.002, 0.5), 2,2)
mat4 <- dmat(0.1, 0.2, 0.3, 0.4)

smat(mat1)
#> $...
#>     [,1]
#> 1:     1
#> 
smat(mat1, mat2, mat3)
#> $...
#>     [,1]
#> 1:     1
#> 
#> $...
#>     [,1] [,2]
#> 2:     1    0
#> 3:     0    2
#> 
#> $...
#>      [,1]  [,2]
#> 4:  0.100 0.002
#> 5:  0.002 0.500
#> 
smat(A=mat1, B=mat2, C=mat3)
#> $A
#>     [,1]
#> 1:     1
#> 
#> $B
#>     [,1] [,2]
#> 2:     1    0
#> 3:     0    2
#> 
#> $C
#>      [,1]  [,2]
#> 4:  0.100 0.002
#> 5:  0.002 0.500
#> 

mod <- mrgsolve::house() %>% smat(mat1)

smat(mod)
#> $...
#>        [,1]
#> EXPO:     1
#> 
smat(mod, make=TRUE)
#>      [,1]
#> [1,]    1
```
