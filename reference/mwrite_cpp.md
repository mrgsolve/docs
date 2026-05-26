# Write a model to native mrgsolve format

Model code is written to a file in native mrgsolve format. This can be
useful for (1) breaking connection to NONMEM modeling outputs that are
imported by `$NMXML` or `$NMEXT` and (2) saving model updates (e.g., an
updated parameter list). Models can be read back using
[`mread()`](https://mrgsolve.org/docs/reference/mread.md).

## Usage

``` r
mwrite_cpp(x, file, update = TRUE)
```

## Arguments

- x:

  a model object.

- file:

  output file name; if non-character (e.g., `NULL`), no output will be
  written to file.

- update:

  `TRUE` if model settings should be written into the cpp file in a
  `$SET` block.

## Value

A list containing data that was written out to the cpp file, with added
item `file`, is returned invisibly.

## Details

See important details in
[`mwrite_yaml()`](https://mrgsolve.org/docs/reference/mwrite_yaml.md).

## See also

[`mwrite_yaml()`](https://mrgsolve.org/docs/reference/mwrite_yaml.md),
[`yaml_to_cpp()`](https://mrgsolve.org/docs/reference/mread_yaml.md)

## Examples

``` r
temp <- tempfile(fileext = ".mod")

mod <- modlib("pk1", compile = FALSE)

x <- mwrite_cpp(mod, file = temp)

mod <- mread(x$file, compile = FALSE)

mod
#> 
#> 
#> -----------  source: file1623fc982548.mod  -----------
#> 
#>   project: /private/var/fol.../T/RtmpwTsssJ
#>   shared object: file1623fc982548.mod-so-1623f64643f0b <not loaded>
#> 
#>   time:          start: 0 end: 24 delta: 1
#>                  add: <none>
#>   compartments:  EV CENT [2]
#>   parameters:    CL V KA [3]
#>   captures:      CP [1]
#>   omega:         0x0 
#>   sigma:         0x0 
#> 
#>   solver:        rtol: 1e-08 atol: 1e-08 itol: 1 (scalar)
#> ------------------------------------------------------
```
