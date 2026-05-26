# Update the model object

After the model object is created, update various attributes.

## Usage

``` r
# S4 method for class 'mrgmod'
update(object, ..., merge = TRUE, open = FALSE, data = NULL, strict = TRUE)

# S4 method for class 'omegalist'
update(object, y, ...)

# S4 method for class 'sigmalist'
update(object, y, ...)

# S4 method for class 'parameter_list'
update(object, .y, ...)
```

## Arguments

- object:

  a model object.

- ...:

  named items to update.

- merge:

  logical indicating to merge (rather than replace) new and existing
  attributes.

- open:

  logical; used only when merge is `TRUE` and parameter list or initial
  conditions list is being updated; if `FALSE`, no new items will be
  added; if `TRUE`, the parameter list may expand.

- data:

  a list of items to update; this list is combined with any items passed
  in via `...`.

- strict:

  if `TRUE`, a warning will be issued when there is an attempt to update
  a non-existent item.

- y:

  another object involved in update

- .y:

  data to update

## Value

The updated model object is returned.

## Details

Slots that can be updated:

- verbose

- debug

- preclean

- mindt

- digits

- atol - absolute solver tolerance; see
  [`solversettings`](https://mrgsolve.org/docs/reference/solversettings.md)

- rtol - relative solver tolerance; see
  [`solversettings`](https://mrgsolve.org/docs/reference/solversettings.md)

- ss_rtol - relative tolerance when finding steady state

- ss_atol - absolute tolerance when finding steady state

- ixpr - see `IXPR` in
  [`solversettings`](https://mrgsolve.org/docs/reference/solversettings.md)

- mxhnil - see `MXHNIL` in
  [`solversettings`](https://mrgsolve.org/docs/reference/solversettings.md)

- hmin - see `HMIN` in
  [`solversettings`](https://mrgsolve.org/docs/reference/solversettings.md)

- hmax - see `HMAX` in
  [`solversettings`](https://mrgsolve.org/docs/reference/solversettings.md)

- maxsteps - see `MXSTEP` in
  [`solversettings`](https://mrgsolve.org/docs/reference/solversettings.md)

- start, end, delta, add

- tscale

- request

- param

- init

- omega

- sigma

- outvars

## See also

`update`,
[`mrgmod-class`](https://mrgsolve.org/docs/reference/mrgmod-class.md),
[`within`](https://mrgsolve.org/docs/reference/within.md)

## Examples

``` r
if (FALSE) { # \dontrun{
 mod <- house()

 mod <- update(mod, end = 120, delta = 4, param = list(CL = 19.1))
} # }
 
```
