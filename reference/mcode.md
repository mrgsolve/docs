# Write, compile, and load model code

This is a convenience function that ultimately calls
[`mread()`](https://mrgsolve.org/docs/reference/mread.md). Model code is
written to a file and read back in using
[`mread()`](https://mrgsolve.org/docs/reference/mread.md).

## Usage

``` r
mcode(model, code, project = getOption("mrgsolve.project", tempdir()), ...)

mcode_cache(
  model,
  code,
  project = getOption("mrgsolve.project", tempdir()),
  ...
)
```

## Arguments

- model:

  model name.

- code:

  character string specifying a `mrgsolve` model.

- project:

  project directory for the model.

- ...:

  passed to [`mread()`](https://mrgsolve.org/docs/reference/mread.md);
  see that help topic for other arguments that can be set.

## Details

Note that the arguments are in slightly different order than
[`mread()`](https://mrgsolve.org/docs/reference/mread.md). The default
`project` is [`tempdir()`](https://rdrr.io/r/base/tempfile.html).

See the [`mread()`](https://mrgsolve.org/docs/reference/mread.md) help
topic for discussion about caching compilation results with
`mcode_cache()`.

## See also

[`mread()`](https://mrgsolve.org/docs/reference/mread.md),
[`mread_cache()`](https://mrgsolve.org/docs/reference/mread.md)

## Examples

``` r
if (FALSE) { # \dontrun{ 
code <- '
$CMT DEPOT CENT
$PKMODEL ncmt=1, depot=TRUE
$MAIN
double CL = 1;
double V = 20;
double KA = 1;
'

mod <- mcode("example", code, compile = FALSE)
} # }
```
