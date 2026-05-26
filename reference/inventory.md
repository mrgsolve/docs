# Check whether all required parameters needed in a model are present in an object

This function has largely been superseded by
[`check_data_names()`](https://mrgsolve.org/docs/reference/check_data_names.md).

## Usage

``` r
inventory(x, obj, ..., .strict = FALSE)
```

## Arguments

- x:

  model object.

- obj:

  data.frame to pass to
  [`idata_set()`](https://mrgsolve.org/docs/reference/idata_set.md) or
  [`data_set()`](https://mrgsolve.org/docs/reference/data_set.md).

- ...:

  capture dplyr-style parameter requirements.

- .strict:

  whether to stop execution if all requirements are present (`TRUE`) or
  just warn (`FALSE`); see **Details**.

## Value

`x` is returned invisibly.

## Details

If parameter requirements are not explicitly stated, the requirement
defaults to all parameter names in `x`. Note that, by default, the
inventory is not `.strict` unless the user explicitly states the
parameter requirement. That is, if parameter requirements are explicitly
stated, `.strict` will be set to `TRUE` if a value `.strict` was not
passed in the call.

## See also

[`check_data_names()`](https://mrgsolve.org/docs/reference/check_data_names.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  inventory(mod, idata, CL:V) # parameters defined, inclusively, CL through Volume 
  inventory(mod, idata, everything()) # all parameters
  inventory(mod, idata, contains("OCC")) # all parameters containing OCC
  inventory(mod, idata, -F) # all parameters except F
} # }
```
