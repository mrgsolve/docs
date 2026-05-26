# Parse model specification text

Parse model specification text

## Usage

``` r
modelparse(
  txt,
  split = FALSE,
  drop_blank = TRUE,
  comment_re = c("//", "##"),
  keep_mapping = FALSE
)

modelparse_rmd(txt, split = FALSE, drop_blank = TRUE, comment_re = "//")
```

## Arguments

- txt:

  model specification text.

- split:

  logical; if `TRUE`, `txt` will be split on `\n` before processing.

- drop_blank:

  logical; `TRUE` if blank lines will be dropped.

- comment_re:

  regular expression to identify comments.

- keep_mapping:

  if `TRUE`, parse information will be retained as attributes on the
  parsed model code.

## See also

[`modelsplit()`](https://mrgsolve.org/docs/reference/modelsplit.md) and
[`modelunsplit()`](https://mrgsolve.org/docs/reference/modelsplit.md)
for a non-destructive split/reassemble alternative.

## Examples

``` r
file <- file.path(modlib(), "pk1.cpp")

code <- readLines(file)

modelparse(code)
#> $PARAM
#> [1] "@annotated @input"                            
#> [2] "CL   :  1 : Clearance (volume/time)"          
#> [3] "V    : 20 : Central volume (volume)"          
#> [4] "KA   :  1 : Absorption rate constant (1/time)"
#> 
#> $CMT
#> [1] "@annotated"                       "EV   : Extravascular compartment"
#> [3] "CENT : Central compartment"      
#> 
#> $GLOBAL
#> [1] "#define CP (CENT/V)"
#> 
#> $PKMODEL
#> [1] "advan = 2"
#> 
#> $CAPTURE
#> [1] "@annotated"                             
#> [2] "CP : Plasma concentration (mass/volume)"
#> 
```
