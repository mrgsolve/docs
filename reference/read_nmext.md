# Extract estimates from NONMEM ext file

This function retrieves NONMEM estimates for use in the mrgsolve model
when `$NMEXT` is invoked. See
[`nmext()`](https://mrgsolve.org/docs/reference/nmext.md).

## Usage

``` r
read_nmext(
  run = NA_real_,
  project = getwd(),
  file = paste0(run, ".ext"),
  path = NULL,
  read_fun = c("data.table", "read.table"),
  index = "last"
)
```

## Arguments

- run:

  a run number or run identifier.

- project:

  the NONMEM project directory.

- file:

  the `ext` file name.

- path:

  full path and file name for `ext` file.

- read_fun:

  function to read the `ext` file;
  [`data.table::fread()`](https://rdrr.io/pkg/data.table/man/fread.html)
  will be used if available; otherwise
  [`utils::read.table()`](https://rdrr.io/r/utils/read.table.html) is
  used.

- index:

  selects the table number whose results will be returned; use value
  "last" to select the last table in the `.ext` file; or pass an integer
  specifying the table number; in case there is exactly one table in the
  `.ext` file, pass the value "single" to bypass parsing the file to
  look for sub tables (this might be useful when BAYES analysis was
  performed as the only estimation method and there are 10000s of
  posterior samples in the file).

## Value

A list with param, omega, and sigma in a format ready to be used to
update a model object.

## Examples

``` r
project <- system.file("nonmem", package = "mrgsolve")

est <- read_nmext(1005, project = project)

est$param
#> $THETA1
#> [1] 9.50789
#> 
#> $THETA2
#> [1] 22.791
#> 
#> $THETA3
#> [1] 0.0714337
#> 
#> $THETA4
#> [1] 3.47451
#> 
#> $THETA5
#> [1] 113.277
#> 
#> $THETA6
#> [1] 1.02435
#> 
#> $THETA7
#> [1] 1.19212
#> 

est$omega
#>            [,1]       [,2]       [,3]
#> [1,]  0.2138790  0.1207700 -0.0116278
#> [2,]  0.1207700  0.0945105 -0.0372064
#> [3,] -0.0116278 -0.0372064  0.0465631

est$sigma
#>           [,1]     [,2]
#> [1,] 0.0491707 0.000000
#> [2,] 0.0000000 0.201769

est <- read_nmext(2005, project = project, index = 3)
```
