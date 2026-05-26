# Methods for working with matrix-list objects

Methods for working with matrix-list objects

## Usage

``` r
# S4 method for class 'matlist'
as.list(x, detailed = FALSE, ...)

# S4 method for class 'matlist'
as.matrix(x, ...)

# S3 method for class 'matlist'
names(x)

# S3 method for class 'matlist'
length(x)

# S4 method for class 'matlist'
labels(object, ...)

# S4 method for class 'matlist'
dim(x)

# S4 method for class 'matlist'
nrow(x)

# S4 method for class 'matlist'
show(object)
```

## Arguments

- x:

  a matlist object.

- detailed:

  if `TRUE`, then a simple list of matrices is returned; otherwise, then
  entire `matlist` object data is returned along with the name of the
  `class` (e.g. either `omegalist` or `sigmalist`) as well as the
  `names` of the matrices.

- ...:

  passed through to other methods.

- object:

  passed to showmatlist
