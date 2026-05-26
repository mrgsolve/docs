# Re-evaluate the code in the ENV block

The `$ENV` block is a block of R code that can realize any sort of R
object that might be used in running a model.

## Usage

``` r
env_eval(x, seed = NULL)
```

## Arguments

- x:

  a model object.

- seed:

  passed to [`set.seed()`](https://rdrr.io/r/base/Random.html) if a
  numeric value is supplied.

## See also

[`env_get()`](https://mrgsolve.org/docs/reference/env_get.md),
[`env_get_env()`](https://mrgsolve.org/docs/reference/env_get.md),
[`env_ls()`](https://mrgsolve.org/docs/reference/env_ls.md)
