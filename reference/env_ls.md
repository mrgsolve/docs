# List objects in the model environment

Each model keeps an internal environment that allows the user to carry
any `R` object along. Objects are coded in `$ENV`.

## Usage

``` r
env_ls(x, ...)
```

## Arguments

- x:

  a model object.

- ...:

  passed to [`ls()`](https://rdrr.io/r/base/ls.html).
