# Event objects for simulating PK and other interventions

An event object specifies dosing or other interventions that get
implemented during simulation. Event objects do similar things as
[data_set](https://mrgsolve.org/docs/reference/data_set.md), but simpler
and easier to create.

## Usage

``` r
ev(x, ...)

# S4 method for class 'mrgmod'
ev(x, object = NULL, ...)

# S4 method for class 'missing'
ev(
  time = 0,
  amt = 0,
  evid = 1,
  cmt = 1,
  ID = numeric(0),
  replicate = TRUE,
  until = NULL,
  tinf = NULL,
  realize_addl = FALSE,
  ...
)

# S4 method for class 'ev'
ev(x, realize_addl = FALSE, ...)
```

## Arguments

- x:

  a model object.

- ...:

  other items to be incorporated into the event object; see **Details**.

- object:

  an event object to be added to a model object.

- time:

  event time.

- amt:

  dose amount.

- evid:

  event ID.

- cmt:

  compartment number or name.

- ID:

  subject ID.

- replicate:

  logical; if `TRUE`, events will be replicated for each individual in
  `ID`.

- until:

  the expected maximum **observation** time for this regimen; doses will
  be scheduled up to, but not including, the `until` time; see
  **Examples**.

- tinf:

  infusion time; if greater than zero, then the `rate` item will be
  derived as `amt/tinf`.

- realize_addl:

  if `FALSE` (default), no change to `addl` doses. If `TRUE`, `addl`
  doses are made explicit with
  [`realize_addl()`](https://mrgsolve.org/docs/reference/realize_addl.md).

## Value

`ev()` returns an event object.

## Details

- Required items in events objects include `time`, `amt`, `evid` and
  `cmt`.

- If not supplied, `evid` is assumed to be 1.

- If not supplied, `cmt` is assumed to be 1.

- If not supplied, `time` is assumed to be 0.

- If `amt` is not supplied, an error will be generated.

- If `total` is supplied, then `addl` will be set to `total-1`.

- Other items can include `ii`, `ss`, and `addl` (see
  [data_set](https://mrgsolve.org/docs/reference/data_set.md) for
  details on all of these items).

- `ID` may be specified as a vector.

- If replicate is `TRUE` (default), then the events regimen is
  replicated for each `ID`; otherwise, the number of event rows must
  match the number of `ID`s entered.

## See also

[`evd()`](https://mrgsolve.org/docs/reference/evd.md),
[`ev_rep()`](https://mrgsolve.org/docs/reference/ev_rep.md),
[`ev_days()`](https://mrgsolve.org/docs/reference/ev_days.md),
[`ev_repeat()`](https://mrgsolve.org/docs/reference/ev_repeat.md),
[`ev_assign()`](https://mrgsolve.org/docs/reference/ev_assign.md),
[`ev_seq()`](https://mrgsolve.org/docs/reference/ev_seq.md),
[`mutate.ev()`](https://mrgsolve.org/docs/reference/ev_dplyr.md),
[`as.ev()`](https://mrgsolve.org/docs/reference/as.ev.md),
[`as.evd()`](https://mrgsolve.org/docs/reference/evd.md),
[ev_methods](https://mrgsolve.org/docs/reference/ev_methods.md).

## Examples

``` r
mod <- mrgsolve::house()

mod <- mod %>% ev(amt = 1000, time = 0, cmt = 1)

loading <- ev(time = 0, cmt = 1, amt = 1000)

maint <- ev(time = 12, cmt = 1, amt = 500, ii = 12, addl = 10)

c(loading, maint)
#> Events:
#>   time  amt cmt evid ii addl
#> 1    0 1000   1    1  0    0
#> 2   12  500   1    1 12   10

reduced_load <- dplyr::mutate(loading, amt = 750)

# Three additional doses in this case
e <- ev(amt = 100, ii = 4*7, until = 16*7)
e
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100 28    3   1    1
# Last dose is given at 84
realize_addl(e)
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100  0    0   1    1
#> 2   28 100  0    0   1    1
#> 3   56 100  0    0   1    1
#> 4   84 100  0    0   1    1

# Four additional doses with last at 112 in this case
e <- ev(amt = 100, ii = 4*7, until = 16*7 + 0.001)
realize_addl(e)
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100  0    0   1    1
#> 2   28 100  0    0   1    1
#> 3   56 100  0    0   1    1
#> 4   84 100  0    0   1    1
#> 5  112 100  0    0   1    1
```
