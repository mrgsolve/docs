# Create a simulation data set from ev objects or data frames

The goal is to take a series of event objects or data frames and combine
them into a single data frame that can be passed to
[`data_set()`](https://mrgsolve.org/docs/reference/data_set.md).

## Usage

``` r
as_data_set(x, ...)

# S4 method for class 'ev'
as_data_set(x, ...)

# S4 method for class 'data.frame'
as_data_set(x, ...)
```

## Arguments

- x:

  an ev object or data frame.

- ...:

  additional ev objects or data frames.

## Value

A data frame suitable for passing into
[`data_set()`](https://mrgsolve.org/docs/reference/data_set.md). The
columns will appear in a standardized order.

## Details

Each event object or data frame is added to the data frame as an `ID` or
set of `ID`s that are distinct from the `ID`s in the other event
objects. Note that including `ID` argument to the
[`ev()`](https://mrgsolve.org/docs/reference/ev.md) call where
`length(ID)` is greater than one will render that set of events for all
of `ID`s that are requested.

When determining the case for output names, the `case` attribute for the
first `ev` object passed will be used to set the case for the output
data.frame. In the event `x` is a data frame, the case of special column
names (like `amt/AMT` or `cmt/CMT`) in the first data frame will be
assessed and the case in the output data frame will be determined based
on the relative numbers of lower or upper names.

To get a data frame with one row (event) per `ID`, look at
[`expand.ev()`](https://mrgsolve.org/docs/reference/expand.idata.md).

## See also

[`expand.ev()`](https://mrgsolve.org/docs/reference/expand.idata.md),
[`expand.evd()`](https://mrgsolve.org/docs/reference/expand.idata.md),
[`ev()`](https://mrgsolve.org/docs/reference/ev.md),
[`evd()`](https://mrgsolve.org/docs/reference/evd.md),
[`uctran()`](https://mrgsolve.org/docs/reference/lctran.md),
[`lctran()`](https://mrgsolve.org/docs/reference/lctran.md)

## Examples

``` r
a <- ev(amt = c(100,200), cmt=1, ID = seq(3))
b <- ev(amt = 300, time = 24, ID = seq(2))
c <- ev(amt = 1000, ii = 8, addl = 10, ID = seq(3))

as_data_set(a, b, c)
#>    ID time  amt ii addl cmt evid
#> 1   1    0  100  0    0   1    1
#> 2   1    0  200  0    0   1    1
#> 3   2    0  100  0    0   1    1
#> 4   2    0  200  0    0   1    1
#> 5   3    0  100  0    0   1    1
#> 6   3    0  200  0    0   1    1
#> 7   4   24  300  0    0   1    1
#> 8   5   24  300  0    0   1    1
#> 9   6    0 1000  8   10   1    1
#> 10  7    0 1000  8   10   1    1
#> 11  8    0 1000  8   10   1    1

d <- evd(amt = 500)

as_data_set(d, a)
#>   ID TIME AMT CMT EVID
#> 1  1    0 500   1    1
#> 2  2    0 100   1    1
#> 3  2    0 200   1    1
#> 4  3    0 100   1    1
#> 5  3    0 200   1    1
#> 6  4    0 100   1    1
#> 7  4    0 200   1    1

# Output will have upper case nmtran names
as_data_set(
  data.frame(AMT = 100, ID = 1:2), 
  data.frame(amt = 200, rate = 5, cmt = 2)
)
#>   ID TIME AMT RATE CMT EVID
#> 1  1    0 100    0   1    1
#> 2  2    0 100    0   1    1
#> 3  3    0 200    5   2    1

# Instead of this, use expand.ev
as_data_set(ev(amt = 100), ev(amt = 200), ev(amt = 300))
#>   ID time amt cmt evid
#> 1  1    0 100   1    1
#> 2  2    0 200   1    1
#> 3  3    0 300   1    1
```
