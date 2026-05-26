# Replicate an event object

An event sequence can be replicated a certain number of times in a
certain number of IDs.

## Usage

``` r
ev_rep(x, ID = 1, n = NULL, wait = 0, as.ev = FALSE, id = NULL)
```

## Arguments

- x:

  event object.

- ID:

  numeric vector if IDs.

- n:

  passed to
  [`ev_repeat()`](https://mrgsolve.org/docs/reference/ev_repeat.md).

- wait:

  passed to
  [`ev_repeat()`](https://mrgsolve.org/docs/reference/ev_repeat.md).

- as.ev:

  if `TRUE` an event object is returned.

- id:

  deprecated; use `ID` instead.

## Value

A single data.frame or event object as determined by the value of
[`as.ev()`](https://mrgsolve.org/docs/reference/as.ev.md).

## See also

[`ev_repeat()`](https://mrgsolve.org/docs/reference/ev_repeat.md)

## Examples

``` r

e1 <- c(ev(amt=100), ev(amt=200, ii=24, addl=2, time=72))

ev_rep(e1, 1:5)
#>    ID time amt cmt evid ii addl
#> 1   1    0 100   1    1  0    0
#> 2   1   72 200   1    1 24    2
#> 3   2    0 100   1    1  0    0
#> 4   2   72 200   1    1 24    2
#> 5   3    0 100   1    1  0    0
#> 6   3   72 200   1    1 24    2
#> 7   4    0 100   1    1  0    0
#> 8   4   72 200   1    1 24    2
#> 9   5    0 100   1    1  0    0
#> 10  5   72 200   1    1 24    2
```
