# Customize tolerances for specific compartments

These functions update the relative or absolute tolerance values only
for the custom tolerance configuration.

## Usage

``` r
custom_tol(.x, .rtol = NULL, .atol = NULL)

custom_rtol(.x, .rtol = list(), .default = NULL, .use = TRUE, ...)

custom_atol(.x, .atol = list(), .default = NULL, .use = TRUE, ...)
```

## Arguments

- .x:

  a model object.

- .rtol:

  a named numeric list or vector, where names reference selected model
  compartments and relative tolerances for those compartments;
  `custom_tol()` also accepts the name of an object in the model
  environment to be used.

- .atol:

  a named numeric list or vector, where names reference selected model
  compartments and absolute tolerances for those compartments;
  `custom_tol()` also accepts the name of an object in the model
  environment to be used.

- .default:

  the default tolerance value to use for compartments not listed in
  `.rtol`, `.atol`, or `...`; if not supplied, the current scalar value
  in `.x` will be used.

- .use:

  `logical`; if `TRUE`, then a call to
  [`use_custom_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md)
  will be made prior to return; if `FALSE`, a call to
  [`use_scalar_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md)
  will be made; under expected use, the value for this argument is kept
  `TRUE`, so that whenever tolerances are customized, they will be used
  in the next simulation run.

- ...:

  `name`/`value` pairs, where `name` references a model compartment and
  `value` is a new, numeric value to use for `rtol` or `atol`.

## Value

An updated model object.

## Details

New tolerance values can be supplied by either a named, numeric vector
or list via `.rtol` and `.atol` or via `...` or by both. If duplicate
compartment names are found in `...` and either `.rtol` or `.atol`, the
value passed via `...` will take precedence.

The `custom_tol()` function provides a mechanism for coding customized
tolerances into the model file itself. Simply create named numeric lists
or vectors for customized `rtol` or `atol` in a `$ENV` block. On loading
the model, call `custom_tol()` and supply the names of those objects as
`.rtol` and `.atol`.

## See also

[`reset_tol()`](https://mrgsolve.org/docs/reference/reset_tol.md),
[`use_custom_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md),
[`use_scalar_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md),
[`get_tol()`](https://mrgsolve.org/docs/reference/get_tol.md)

## Examples

``` r
mod <- house()
mod <- custom_rtol(mod, GUT = 1e-2, CENT = 1e-3)

new_tolerances <- c(GUT = 1e-4, RESP = 1e-5)
mod <- custom_rtol(mod, new_tolerances, RESP = 1e-6)
```
