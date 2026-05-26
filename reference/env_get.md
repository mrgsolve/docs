# Return model environment or objects from the model environment

Call `env_get()` passing either a model object or simulated output and
name an object to retrieve from the model object environment.
`env_get_obj()` is an alias to `env_get()`. Call `env_get_env()` to
return the environment itself. Methods for `mrgmod` and `mrgsims` both
interact with the same environment (see **Examples**).

## Usage

``` r
env_get(x, ...)

# S3 method for class 'mrgmod'
env_get(x, what, ...)

# S3 method for class 'mrgsims'
env_get(x, ...)

env_get_obj(x, ...)

env_get_env(x, ...)

# S3 method for class 'mrgmod'
env_get_env(x, ...)

# S3 method for class 'mrgsims'
env_get_env(x, ...)
```

## Arguments

- x:

  a model object (class `mrgmod`) or simulated output (class `mrgsims`).

- ...:

  passed [`base::get()`](https://rdrr.io/r/base/get.html).

- what:

  the name of an object to return.

## Examples

``` r
mod <- house(end = 1)

# Just for the example
assign("let", letters[1:3], env_get_env(mod))

out <- mrgsim(mod)

env_get(out, "let")
#> [1] "a" "b" "c"

env_get(mod, "let")
#> [1] "a" "b" "c"

env_get_obj(out, "let")
#> [1] "a" "b" "c"

env_get_env(mod)
#> <environment: 0x7765100b0>

# It's the same environment in out that is in mod
env_get_env(out)
#> <environment: 0x7765100b0>
```
