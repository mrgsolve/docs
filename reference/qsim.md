# Basic, simple simulation from model object

This is just a lighter version of
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md), with fewer
options but with better efficiency in certain cases. See **Details**.

## Usage

``` r
qsim(
  x,
  data,
  idata = no_idata_set(),
  obsonly = FALSE,
  tgrid = NULL,
  recsort = 1,
  tad = FALSE,
  Req = NULL,
  outvars = Req,
  skip_init_calc = FALSE,
  output = "mrgsims"
)
```

## Arguments

- x:

  the model object.

- data:

  can be either event object or data set.

- idata:

  a matrix or data frame of model parameters, one parameter per row (see
  [`idata_set()`](https://mrgsolve.org/docs/reference/idata_set.md)).

- obsonly:

  if `TRUE`, dosing records are not included in the output.

- tgrid:

  a tgrid object; or a numeric vector of simulation times or another
  object with an `stime` method.

- recsort:

  record sorting flag. Default value is 1. Possible values are 1,2,3,4:
  1 and 2 put doses in a data set after padded observations at the same
  time; 3 and 4 put those doses before padded observations at the same
  time. 2 and 4 will put doses scheduled through `addl` after
  observations at the same time; 1 and 3 put doses scheduled through
  `addl` before observations at the same time. `recsort` will not change
  the order of your input data set if both doses and observations are
  given.

- tad:

  when `TRUE` a column is added to simulated output is added showing the
  time since the last dose. Only data records with `evid == 1` will be
  considered doses for the purposes of `tad` calculation. The `tad` can
  be properly calculated with a dosing lag time in the model as long as
  the dosing lag time (specified in `$MAIN`) is always appropriate for
  any subsequent doses scheduled through `addl`. This will always be
  true if the lag time doesn't change over time. But it might (possibly)
  not hold if the lag time changes prior to the last dose in the `addl`
  sequence. This known limitation shouldn't affect `tad` calculation in
  most common dosing lag time implementations.

- Req:

  synonym for `outvars`.

- outvars:

  output items to request; if missing, then only captured items will be
  returned in the output.

- skip_init_calc:

  don't use `$MAIN` to calculate initial conditions.

- output:

  output data type; the default is `mrgsims`, which returns the default
  output object; other options include `df` (for data.frame) or
  `matrix`.

## Details

`qsim()` mainly cuts some of the overhead from the simulation. So, the
primary efficiency gain from using `qsim()` comes when the simulation
executes very quickly. It is unlikely you will see a big performance
difference between `qsim()` and
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md) when the
model is difficult to solve or if there is a large input data set.

There is no pipeline interface for this function; all configuration
options (see **Arguments**) must be passed as formal arguments to the
function. You can't `carry_out`, `Request` specific columns, or pass
items in for update. Some other limitations, but only
convenience-related. See **Arguments** for available options.
Specifically, there is no `...` argument for this function. Use the
[`update()`](https://mrgsolve.org/docs/reference/update.md) method to
update the model object.

## See also

[`mrgsim_q()`](https://mrgsolve.org/docs/reference/mrgsim_q.md),
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md),
[mrgsim_variants](https://mrgsolve.org/docs/reference/mrgsim_variants.md)

## Examples

``` r

mod <- mrgsolve::house()

dose <- ev(amt = 100)

out <- qsim(mod,dose)
```
