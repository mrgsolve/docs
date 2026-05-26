# Check input data set names against model parameters

Use this function to check names of input data sets against parameters
that have been assigned different tags. Assignment is made in the model
specification file. This is useful to alert the user to misspelled or
otherwise misspecified parameter names in input data sets. See
[`param_tags()`](https://mrgsolve.org/docs/reference/param_tags.md) for
information on associating tags with parameters.

## Usage

``` r
check_data_names(
  data,
  x,
  check_covariates = TRUE,
  check_inputs = TRUE,
  tags = NULL,
  mode = c("warn", "error", "inform"),
  silent = FALSE
)
```

## Arguments

- data:

  a data frame or other object with names to check.

- x:

  a model object.

- check_covariates:

  logical; if `TRUE`, check `data` for parameter names carrying the
  `covariates` tag.

- check_inputs:

  logical; if `TRUE`, check `data` for parameter names carrying the
  `input` tag.

- tags:

  a character vector of user-defined parameter tags to require in
  `data`; this may be a comma- or space-separated string (e.g.
  `"tag1,tag2"`).

- mode:

  the default is to `"warn"` the user when `data` is missing some
  expected column names; alternatively, use `"error"` to issue an error
  or `"inform"` to generate a message when `data` is missing some
  expected column names.

- silent:

  silences message on successful check.

## Value

A logical value is returned; `TRUE` if all expected parameters were
found and `FALSE` otherwise.

## Details

By default, `data` will be checked for parameters with the `covariates`
or `input` tags; these checks can be bypassed with the
`check_covariates` and `check_inputs` arguments. When a parameter name
is missing from `data` the user will be warned by default. Use
`mode = "error"` to generate an error instead of a warning and use
`mode = "inform"` to simply be informed. When the user has not tagged
any parameters for checking, there will either be a warning (default) or
an error (when `mode = "error"`).

It is an error to request a parameter tag via the `tags` argument when
that tag is not found in the model.

It is an error to call `check_data_names` when no parameters have been
tagged in the model specification file (see
[`param_tags()`](https://mrgsolve.org/docs/reference/param_tags.md)).

## See also

[`param_tags()`](https://mrgsolve.org/docs/reference/param_tags.md)

## Examples

``` r

mod <- mcode("ex-cdn", "$PARAM @input \n CL = 1, KA = 2", compile = FALSE)

param(mod)
#> 
#>  Model parameters (N=2):
#>  name value . name value
#>  CL   1     | KA   2    

# Coding mistake!
data <- expand.evd(amt = 100, cl = 2, KA = 5)

check_data_names(data, mod)
#> Warning: Could not find the following parameter names in `data`:
#> • CL (input)
#> ℹ Please check names in `data` against names in the parameter list.

try(check_data_names(data, mod, mode = "error"))
#> Error in check_data_names(data, mod, mode = "error") : 
#>   Could not find the following parameter names in `data`:
#> • CL (input)
#> ✖ Please check names in `data` against names in the parameter list.

check_data_names(data, mod, mode = "inform")
#> Could not find the following parameter names in `data`:
#> • CL (input)
```
