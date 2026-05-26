# Methods for numericlist

These methods can be used to coerce `param` and `init` objects into
common `R` data structures, extract elements from `numericlist`s, or get
attributes from `numericlist`s.

## Usage

``` r
# S4 method for class 'numericlist'
as.list(x, ...)

# S4 method for class 'numericlist'
as.numeric(x)

# S4 method for class 'numericlist'
as.data.frame(x, row.names = NULL, optional = FALSE, ...)

# S4 method for class 'numericlist'
length(x)

# S4 method for class 'numericlist'
names(x)

# S4 method for class 'numericlist'
x$name

# S4 method for class 'numericlist'
x[[i, ..., exact = TRUE]]

# S4 method for class 'numericlist'
x[i, j, ..., drop = TRUE]
```

## Arguments

- x:

  object

- ...:

  passed along to other methods

- row.names:

  passed to [`as.data.frame`](https://rdrr.io/r/base/as.data.frame.html)

- optional:

  passed to [`as.data.frame`](https://rdrr.io/r/base/as.data.frame.html)

- name:

  column to take

- i:

  elements to keep

- exact:

  not used

- j:

  not used

- drop:

  not used
