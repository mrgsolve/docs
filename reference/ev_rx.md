# Create intervention objects from Rx input

See details below for Rx specification. Actual parsing is done by
`parse_rx()`; this function can be used to debug Rx inputs.

## Usage

``` r
ev_rx(x, y, ...)

# S4 method for class 'mrgmod,character'
ev_rx(x, y, ...)

# S4 method for class 'character,missing'
ev_rx(x, df = FALSE, ...)

parse_rx(x)
```

## Arguments

- x:

  a model object or `character` Rx input.

- y:

  `character` Rx input; see details.

- ...:

  not used at this time.

- df:

  if `TRUE` then a data frame is returned.

## Value

The method dispatched on model object (`mrgmod`) returns another model
object. The `character` method returns an event object. The `parse_rx`
function return a list named with arguments for the event object
constructor [`ev()`](https://mrgsolve.org/docs/reference/ev.md).

## Rx specification

- The dose is found at the start of the string by sequential digits;
  this may be integer, decimal, or specified in scientific notation

- Use `in` to identify the dosing compartment number; must be integer

- Use `q` to identify the dosing interval; must be integer or decimal
  number (but not scientific notation)

- Use `over` to indicate an infusion and its duration; integer or
  decimal number

- Use `x` to indicate total number of doses; must be integer

- Use `then` or `,` to separate dosing periods

- Use `after` to insert a lag in the start of a period; integer or
  decimal number (but not scientific notation)

- Use `&` to implement multiple doses at the same time

## Examples

``` r
# example("ev_rx")

ev_rx("100")
#> Events:
#>   time amt cmt evid
#> 1    0 100   1    1

ev_rx("100 in 2")
#> Events:
#>   time amt cmt evid
#> 1    0 100   2    1

ev_rx("100 q12 x 3")
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100 12    2   1    1

ev_rx("100 over 2")
#> Events:
#>   time amt rate cmt evid
#> 1    0 100   50   1    1

ev_rx("100 q 24 x 3 then 50 q12 x 2")
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100 24    2   1    1
#> 2   72  50 12    1   1    1

ev_rx("100 then 50 q 24 after 12")
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100  0    0   1    1
#> 2   12  50 24    0   1    1

ev_rx("100.2E-2 q4")
#> Events:
#>   time   amt ii cmt evid
#> 1    0 1.002  4   1    1

ev_rx("100 over 2.23")
#> Events:
#>   time amt     rate cmt evid
#> 1    0 100 44.84305   1    1

ev_rx("100 q 12 x 3")
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100 12    2   1    1

ev_rx("100 in 1 & 200 in 2") 
#> Events:
#>   time amt cmt evid
#> 1    0 100   1    1
#> 2    0 200   2    1

parse_rx("100 mg q 24 then 200 mg q12")
#> [[1]]
#> [[1]]$time
#> [1] 0
#> 
#> [[1]]$cmt
#> [1] 1
#> 
#> [[1]]$amt
#> [1] 100
#> 
#> [[1]]$ii
#> [1] 24
#> 
#> 
#> [[2]]
#> [[2]]$time
#> [1] 0
#> 
#> [[2]]$cmt
#> [1] 1
#> 
#> [[2]]$amt
#> [1] 200
#> 
#> [[2]]$ii
#> [1] 12
#> 
#> 
```
