# Select parameter values from a model object

The `$` and `[[` operators get the value of a single parameter in the
model. The `[` gets several values, returning a named list.

## Usage

``` r
# S4 method for class 'mrgmod'
x$name

# S4 method for class 'mrgmod'
x[[i, exact = TRUE]]

# S4 method for class 'mrgmod'
x[i]
```

## Arguments

- x:

  mrgmod object

- name:

  parameter to take

- i:

  an element to select

- exact:

  not used
