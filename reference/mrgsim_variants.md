# mrgsim variant functions

These functions are called by
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md) and have
explicit input requirements written into the function name. The
motivation behind these variants is to give the user a clear workflow
with specific, required inputs as indicated by the function name. Use
[`mrgsim_q()`](https://mrgsolve.org/docs/reference/mrgsim_q.md) instead
to benchmark mrgsolve or to do repeated quick simulation for tasks like
parameter optimization, sensitivity analyses, or optimal design.

## Usage

``` r
mrgsim_e(x, events, idata = NULL, data = NULL, ...)

mrgsim_d(x, data, idata = NULL, events = NULL, ...)

mrgsim_ei(x, events, idata, data = NULL, ...)

mrgsim_di(x, data, idata, events = NULL, ...)

mrgsim_i(x, idata, data = NULL, events = NULL, ...)

mrgsim_0(x, idata = NULL, data = NULL, events = NULL, ...)
```

## Arguments

- x:

  the model object.

- events:

  an event object.

- idata:

  a matrix or data frame of model parameters, one parameter per row (see
  [`idata_set()`](https://mrgsolve.org/docs/reference/idata_set.md)).

- data:

  NMTRAN-like data set (see
  [`data_set()`](https://mrgsolve.org/docs/reference/data_set.md)).

- ...:

  passed to [`update()`](https://mrgsolve.org/docs/reference/update.md)
  and [`do_mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md).

## Details

**Important**: all of these functions require that `data`, `idata`,
and/or `events` be pass directly to the functions. They will not
recognize these inputs from a pipeline.

- `mrgsim_e` simulate using an event object

- `mrgsim_ei` simulate using an event object and `idata_set`

- `mrgsim_d` simulate using a `data_set`

- `mrgsim_di` simulate using a `data_set` and `idata_set`

- `mrgsim_i` simulate using a `idata_set`

- `mrgsim_0` simulate using just the model

- `mrgsim_q` simulate from a data set with quicker turnaround (see
  [`mrgsim_q()`](https://mrgsolve.org/docs/reference/mrgsim_q.md))

## See also

[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md),
[`mrgsim_q()`](https://mrgsolve.org/docs/reference/mrgsim_q.md),
[`qsim()`](https://mrgsolve.org/docs/reference/qsim.md)
