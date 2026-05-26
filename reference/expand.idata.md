# Create template data sets for simulation

These functions expand all combinations of arguments using
[`expand.grid()`](https://rdrr.io/r/base/expand.grid.html).
`expand.idata()` generates an `idata` set; the others generate a full
data set. The result always has only one row for one individual. Use
`expand.evd()` or `evd_expand()` to render NMTRAN names (e.g. `AMT` or
`CMT`) in upper case.

## Usage

``` r
expand.idata(...)

expand.ev(...)

expand.evd(...)

ev_expand(...)

evd_expand(...)
```

## Arguments

- ...:

  passed to [`expand.grid()`](https://rdrr.io/r/base/expand.grid.html).

## Value

A data frame containing one row for each combination of the items passed
in `...`. The result always has ID set to the row number.

## Details

An ID column is added as if not supplied by the user. In the output data
frame, ID is always re-written as the row number.

For `expand.ev()`, defaults also added include `cmt = 1`, `time = 0`,
`evid = 1`. If `total` is included, then `addl` is derived as `total-1`.
If `tinf` is included, then an infusion rate is derived for row where
`tinf` is greater than zero.

`ev_expand()` is a synonym for `expand.ev()` and `evd_expand()` is a
synonym for `expand.evd()`.

## Examples

``` r
idata <- expand.idata(CL = c(1,2,3), VC = c(10,20,30))

doses <- expand.ev(amt = c(300,100), ii = c(12,24), cmt = 1)

infusion <- expand.ev(amt = 100, tinf = 2)
```
