# Select items to carry into simulated output

When items named in this function are found in the input data set
(either [`data_set()`](https://mrgsolve.org/docs/reference/data_set.md)
or [`idata_set()`](https://mrgsolve.org/docs/reference/idata_set.md)),
they are copied into the simulated output. Special items like `evid` or
`amt` or the like are not copied from the data set per se, but they are
copied from `datarecord` objects that are created during the simulation.

## Usage

``` r
carry_out(x, ...)

carry.out(x, ...)
```

## Arguments

- x:

  model object.

- ...:

  unquoted names of data items to copy into the simulated output.

## Details

There is also a `carry_out` argument to
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md) that can be
set to accomplish the same thing as a call to `carry_out` in the
pipeline.

`carry.out` and `carry_out` both do the same thing; using the underscore
version is now preferred.

## Examples

``` r
mod <- mrgsolve::house()

e <- ev(amt = 100, ii = 6, addl = 3, WT = 70, dose = amt)

out <- mod %>% ev(e) %>% carry_out(amt, dose, WT) %>% mrgsim()

head(out)
#>   ID time amt dose WT       GUT     CENT     RESP       DV       CP
#> 1  1 0.00   0  100 70   0.00000  0.00000 50.00000 0.000000 0.000000
#> 2  1 0.00 100  100 70 100.00000  0.00000 50.00000 0.000000 0.000000
#> 3  1 0.25   0  100 70  74.08182 25.74883 48.68223 1.287441 1.287441
#> 4  1 0.50   0  100 70  54.88116 44.50417 46.18005 2.225208 2.225208
#> 5  1 0.75   0  100 70  40.65697 58.08258 43.61333 2.904129 2.904129
#> 6  1 1.00   0  100 70  30.11942 67.82976 41.37943 3.391488 3.391488
```
