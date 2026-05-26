# Create an event object with data-like names

This function calls [`ev()`](https://mrgsolve.org/docs/reference/ev.md)
to create an event object and then sets the case attribute so that it
renders nmtran data names in upper case. An object created with `evd()`
can be used in the same way as an object created with
[`ev()`](https://mrgsolve.org/docs/reference/ev.md).

## Usage

``` r
evd(x, ...)

# S4 method for class 'mrgmod'
evd(x, ...)

# S4 method for class 'missing'
evd(x, ...)

# S4 method for class 'ev'
evd(x, ...)

as.evd(x)
```

## Arguments

- x:

  an event object.

- ...:

  arguments passed to
  [`ev()`](https://mrgsolve.org/docs/reference/ev.md).

## Details

Note that `evd` isn't a separate class; it is just an `ev` object with a
specific `case` attribute. See examples which illustrate the difference.

## See also

[`ev()`](https://mrgsolve.org/docs/reference/ev.md),
[`lctran()`](https://mrgsolve.org/docs/reference/lctran.md),
[`uctran()`](https://mrgsolve.org/docs/reference/lctran.md)

## Examples

``` r
a <- evd(amt = 100)
b <- ev(amt = 300)
a
#> Events Data:
#>   time amt cmt evid
#> 1    0 100   1    1
as.data.frame(a)
#>   TIME AMT CMT EVID
#> 1    0 100   1    1
as_data_set(a, b)
#>   ID TIME AMT CMT EVID
#> 1  1    0 100   1    1
#> 2  2    0 300   1    1
as_data_set(b, a)
#>   ID time amt cmt evid
#> 1  1    0 300   1    1
#> 2  2    0 100   1    1
as.data.frame(seq(a, b))
#>   TIME AMT II ADDL CMT EVID
#> 1    0 100  0    0   1    1
#> 2    0 300  0    0   1    1
```
