# Return the location of the model shared object

This is also the directory where the model is built, which could be the
value of [`tempdir()`](https://rdrr.io/r/base/tempfile.html).

## Usage

``` r
soloc(x, short = FALSE)
```

## Arguments

- x:

  model object.

- short:

  logical; if `TRUE`, `soloc`s will be rendered with a short path name.

## Value

A string containing the full path to the model shared object.

## Examples

``` r
mod <- mrgsolve::house()
soloc(mod)
#> [1] "/private/var/folders/zv/v6tkdhrn1_bb1ndrc0c0j31w0000gp/T/Rtmp0CTHgW/temp_libpath161f33c47ec9b/mrgsolve/libs"
```
