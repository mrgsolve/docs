# Request simulated output

Use this function to select, by name, either compartments or derived
variables that have been captured (see
[CAPTURE](https://mrgsolve.org/docs/reference/BLOCK_PARSE.md)) into the
simulated output.

## Usage

``` r
Req(x, ...)

req(x, ...)

# S3 method for class 'mrgmod'
req(x, ...)
```

## Arguments

- x:

  model object.

- ...:

  unquoted names of compartments or tabled items.

## Details

There is also a `Req` argument to
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md) that can be
set to accomplish the same thing as a call to `Req` in the pipeline.

Note the difference between `req` and `Req`: the former only selects
compartments to appear in output while the latter selects both
compartments and captured items. Also, when there are items explicitly
listed in `Req`, all other compartments or captured items not listed
there are ignored. But when compartments are selected with `req` all of
the captured items are returned. Remember that `req` is strictly for
compartments.

## Examples

``` r
mod <- mrgsolve::house()

mod %>% Req(CP,RESP) %>% ev(amt=1000) %>%  mrgsim()
#> Model:  housemodel 
#> Dim:    482 x 4 
#> Time:   0 to 120 
#> ID:     1 
#>     ID time  RESP    CP
#> 1:   1 0.00 50.00  0.00
#> 2:   1 0.00 50.00  0.00
#> 3:   1 0.25 42.29 12.87
#> 4:   1 0.50 32.69 22.25
#> 5:   1 0.75 25.29 29.04
#> 6:   1 1.00 20.05 33.91
#> 7:   1 1.25 16.45 37.37
#> 8:   1 1.50 14.01 39.78
```
