# DSL preprocessing functions

These functions preprocess model code written in the mrgsolve DSL before
C++ compilation.

## Usage

``` r
convert_pow(x, block = "")

warn_int_div(x, block = "")

convert_fort_if(x)

convert_semicolons(x)
```

## Arguments

- x:

  character vector of source lines to process.

- block:

  model block name; included in warning messages when called during
  model parsing.

## Details

- `convert_pow()`: converts Fortran-style exponentiation (`**`) to C++
  `pow()` calls; runs by default unless turned off by environment
  variable; lines of code will pass through unaltered if `**` is not
  found.

- `warn_int_div()`: warns about literal integer division (e.g. `3/4`,
  `1/2`) that truncates toward zero in C++; returns `x` invisibly and is
  called for its side-effect warnings; runs by default unless turned off
  by environment variable.

- `convert_fort_if()`: converts Fortran `IF`/`THEN`/`ELSE`/`ENDIF`
  constructs and relational operators (`.GE.`, `.LE.`, etc.) to C++;
  runs only when the `nm-vars` plugin is invoked.

- `convert_semicolons()`: appends semicolons to statement lines that are
  missing them; lines ending with an operator (e.g., `+` or `/` or "=")
  will not be terminated with a semicolon; this preprocessor must be
  enlisted through the `semicolons` plugin and it only runs with
  `nm-vars`; the `semicolons` plugin is brought online when the
  `nm-like` composite plugin (`nm-vars`, `autodec`, `semicolons`) is
  invoked.

Processing is controlled by environment variables:

- `MRGSOLVE_CONVERT_POW` (default `TRUE`)

- `MRGSOLVE_CONVERT_FORT_IF` (default `TRUE`)

- `MRGSOLVE_WARN_INT_DIV` (default `TRUE`)

Set any variable to `FALSE` to disable the corresponding step when
processing a model file via
[`mread()`](https://mrgsolve.org/docs/reference/mread.md). Adding
`semicolons` must be opted into through the `semicolons` or `nm-like`
plugins.

## Examples

``` r
convert_pow("a**2")
#> [1] "pow(a, 2)"
convert_pow("(WT/70) ** THETA(3)")
#> [1] "pow(WT/70, THETA(3))"

code <- c("IF ( WT .GE.90) THEN", "  CL = CL * 0.8", "ENDIF")
cat(code, sep = "\n")
#> IF ( WT .GE.90) THEN
#>   CL = CL * 0.8
#> ENDIF
cat(convert_fort_if(code), sep = "\n")
#> if( WT >= 90) {
#>   CL = CL * 0.8
#> }

convert_semicolons("CL = THETA1")
#> [1] "CL = THETA1;"

code <- c("CL =", "THETA1 *", "(WT/70) *", "exp(ETA(1))")
cat(code, sep = "\n")
#> CL =
#> THETA1 *
#> (WT/70) *
#> exp(ETA(1))
cat(convert_semicolons(code), sep = "\n")
#> CL =
#> THETA1 *
#> (WT/70) *
#> exp(ETA(1));

warn_int_div("THETA(1) * pow(WT/70, 3/4)")
#> Warning: Integer division: '3/4' truncates toward zero; use 3.0/4.0 for real division
warn_int_div("3.0/4")
```
