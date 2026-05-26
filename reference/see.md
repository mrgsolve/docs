# Print model code to the console

This is a simple way to display the model code on the R console using
the model object. The `raw` argument will return the model code as a
character vector.

## Usage

``` r
see(x, ...)

# S4 method for class 'mrgmod'
see(x, raw = FALSE, ...)
```

## Arguments

- x:

  model object.

- ...:

  not used.

- raw:

  return the raw code.

## Value

`NULL` is returned invisibly when `raw` is `FALSE`; when `raw` is set to
`TRUE`, the model code is returned as a character vector.
