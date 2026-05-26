# Simulate from a model object with quicker turnaround

Use the function when you would usually use
[`mrgsim_d()`](https://mrgsolve.org/docs/reference/mrgsim_variants.md),
but you need a quicker turnaround time. The timing differences might be
difficult to detect for a single simulation run but could become
appreciable with repeated simulation. See **Details** for important
differences in how `mrgsim_q()` is invoked compared to
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md) and
[`mrgsim_d()`](https://mrgsolve.org/docs/reference/mrgsim_variants.md).
This function should always be used for benchmarking simulation time
with mrgsolve.

## Usage

``` r
mrgsim_q(
  x,
  data,
  recsort = 1,
  stime = numeric(0),
  output = "mrgsims",
  skip_init_calc = FALSE,
  simcall = 0,
  etasrc = "omega"
)
```

## Arguments

- x:

  a model object.

- data:

  a simulation data set.

- recsort:

  record sorting flag.

- stime:

  a numeric vector of observation times; these observation times will
  only be added to the output if there are no observation records in
  `data`.

- output:

  output data type; if
  `"mrgsims", then the default output object is returned; if `"df"\`
  then a data frame is returned.

- skip_init_calc:

  don't use `$MAIN` to calculate initial conditions.

- simcall:

  not used; only the default value of 0 is allowed.

- etasrc:

  source for ETA() values in the model; values can include: "omega",
  `"data"`, `"data.all"`, `"idata"`, or `"idata.all"`; see 'Details' in
  [`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md).

## Value

By default, an object of class `mrgsims`. Use `output = "df"` to return
a data frame.

## Details

`mrgsim_q()` mainly cuts some of the overhead from the simulation. So,
the primary efficiency gain from using `mrgsim_q()` comes when the
simulation executes very quickly. It is unlikely you will see a big
performance difference between `mrgsim_q()` and
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md) when the
model is difficult to solve or if there is a large input data set.

This function does not support the piped simulation workflow. All
arguments must be passed into the function except for `x`.

A data set is required for this simulation workflow. The data set can
have only dosing records or doses with observations. When the data set
only includes doses, a single numeric vector of observation times should
be passed in.

This simulation workflow does not support `Req` (request) functionality.
All compartments and captured variables will always be returned in the
simulation output.

This simulation workflow does not support carry-out functionality.

This simulation workflow does not accept arguments to be passed to
[`update()`](https://mrgsolve.org/docs/reference/update.md). This must
be done by a separate call to
[`update()`](https://mrgsolve.org/docs/reference/update.md).

This simulation workflow does not support use of event objects. If an
event object is needed, it should be converted to a data set prior to
the simulation run (see
[`as_data_set()`](https://mrgsolve.org/docs/reference/as_data_set.md) or
[`as.data.frame()`](https://rdrr.io/r/base/as.data.frame.html)).

This simulation workflow does not support idata sets or any feature
enabled by `idata` set use. Individual level parameters should be joined
onto the data set prior to simulation. Otherwise
[`mrgsim_i()`](https://mrgsolve.org/docs/reference/mrgsim_variants.md)
or
[`mrgsim_ei()`](https://mrgsolve.org/docs/reference/mrgsim_variants.md)
should be used.

By default, a mrgsims object is returned (as with
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md)). Use the
`output = "df"` argument to request a plain data.frame of simulated data
on return.

## See also

[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md),
[mrgsim_variants](https://mrgsolve.org/docs/reference/mrgsim_variants.md),
[`qsim()`](https://mrgsolve.org/docs/reference/qsim.md)

## Examples

``` r
mod <- mrgsolve::house()

data <- expand.ev(amt = c(100, 300, 1000))

out <- mrgsim_q(mod, data)

out
#> Model:  housemodel 
#> Dim:    1446 x 7 
#> Time:   0 to 120 
#> ID:     3 
#>     ID time    GUT  CENT  RESP    DV    CP
#> 1:   1 0.00   0.00  0.00 50.00 0.000 0.000
#> 2:   1 0.00 100.00  0.00 50.00 0.000 0.000
#> 3:   1 0.25  74.08 25.75 48.68 1.287 1.287
#> 4:   1 0.50  54.88 44.50 46.18 2.225 2.225
#> 5:   1 0.75  40.66 58.08 43.61 2.904 2.904
#> 6:   1 1.00  30.12 67.83 41.38 3.391 3.391
#> 7:   1 1.25  22.31 74.74 39.58 3.737 3.737
#> 8:   1 1.50  16.53 79.56 38.18 3.978 3.978
```
