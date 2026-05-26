# Return parameter tags

Use this function if you added the `@covariates` or `@input` attributes
or specified a user-defined tag (via `@tag`) in one or more parameter
blocks and need to extract that information. Also, using the `$INPUT`
block to declare parameters will automatically add the `input` tag (via
`@input`). Once these attributes / tags are added, you can use
[`check_data_names()`](https://mrgsolve.org/docs/reference/check_data_names.md)
to reconcile names of input data sets against tagged model parameters.

## Usage

``` r
param_tags(x)
```

## Arguments

- x:

  mrgsolve model object.

## Value

A data frame listing parameter names and their tags.

## Model specification

Note: it is good practice to tag parameters where appropriate with
`input` or `covariates` as these will automatically be expected on input
data when you call
[`check_data_names()`](https://mrgsolve.org/docs/reference/check_data_names.md).
User-defined tags are also possible, but you will need to alert
[`check_data_names()`](https://mrgsolve.org/docs/reference/check_data_names.md)
to look for them.

**Model Specification Examples**

You can use the `$INPUT` block to add the `input` tag on these
parameters

    $INPUT
    STUDY = 101, WT = 70, DVID = 1

Tag some covariates in the model

    $PARAM @covariates
    WT = 70, SEX = 1, EGFR = 110

A user-defined tag

    $PARAM @tag flags
    FFLAG = 1, DFLAG = 0

## See also

[`check_data_names()`](https://mrgsolve.org/docs/reference/check_data_names.md)

## Examples

``` r
mod <- mrgsolve::house()

param_tags(mod)
#>   name        tag
#> 1   WT covariates
#> 2  SEX covariates
```
