# S4 class for mrgsolve model object

S4 class for mrgsolve model object

## Slots

- `model`:

  model name `<character>`

- `modfile`:

  source model specification file name `<character>`

- `package`:

  the shared object file name `character>`

- `project`:

  working directory; must be writeable with no spaces `<character>`

- `start`:

  simulation start time `<numeric>`

- `end`:

  simulation end time `<numeric>`

- `delta`:

  simulation time interval `<numeric>`

- `add`:

  additional simulation times `<numeric-vector>`

- `param`:

  `<parameter_list>`

- `fixed`:

  a `<parameter_list>` of fixed value parameters; these are not
  updatable from `R`

- `init`:

  `<cmt_list>`

- `digits`:

  significant digits in simulated output; negative integer means ignore
  `<numeric>`

- `hmin`:

  passed to
  [`dlsoda`](https://mrgsolve.org/docs/reference/solversettings.md)
  `<numeric>`

- `hmax`:

  passed to
  [`dlsoda`](https://mrgsolve.org/docs/reference/solversettings.md)
  `<numeric>`

- `mxhnil`:

  passed to
  [`dlsoda`](https://mrgsolve.org/docs/reference/solversettings.md)
  `<numeric>`

- `ixpr`:

  passed to
  [`dlsoda`](https://mrgsolve.org/docs/reference/solversettings.md)
  `<numeric>`

- `itol`:

  passed to
  [`dlsoda`](https://mrgsolve.org/docs/reference/solversettings.md)
  `<int>`; `itol=1` indicates scalar values for `atol` and `rtol`;
  `itol=4` indicates customized tolerances for each compartment

- `atol`:

  passed to
  [`dlsoda`](https://mrgsolve.org/docs/reference/solversettings.md)
  `<numeric>`

- `rtol`:

  passed to
  [`dlsoda`](https://mrgsolve.org/docs/reference/solversettings.md)
  `<numeric>`

- `vec_rtol`:

  a vector of `rtol` to be used when `itol=4` `<numeric>`

- `vec_atol`:

  a vector of `atol` to be used when `itol=4` `<numeric>`

- `ss_rtol`:

  relative tolerance to use when finding PK steady state `<numeric>`

- `ss_atol`:

  absolute tolerance to use when finding PK steady state `<numeric>`

- `maxsteps`:

  passed to
  [`dlsoda`](https://mrgsolve.org/docs/reference/solversettings.md)
  `<numeric>`

- `preclean`:

  passed to R CMD SHLIB during compilation `<logical>`

- `verbose`:

  print run information to screen `<logical>`

- `quiet`:

  print various information to screen `<logical>`

- `debug`:

  not used

- `tscale`:

  used to scale time in simulated output `<numeric>`

- `omega`:

  [`matlist`](https://mrgsolve.org/docs/reference/matlist.md) for
  simulating individual-level random effects

- `sigma`:

  [`matlist`](https://mrgsolve.org/docs/reference/matlist.md) for
  simulating residual error variates

- `args`:

  `<list>` of arguments to be passed to
  [`mrgsim`](https://mrgsolve.org/docs/reference/mrgsim.md)

- `advan`:

  either 2, 4, or 13 `<numeric>`

- `trans`:

  either 1, 2, 4, or 11 `<numeric>`

- `request`:

  vector of compartments to request `<character>`

- `soloc`:

  directory path for storing the model shared object `<character>`

- `code`:

  a character vector of the model code

- `capture`:

  a character vector of variables that are captured from the simulation
  `<character>`

- `mindt`:

  minimum time between simulation records `<numeric>`

- `envir`:

  internal model environment `<environment>`

- `shlib`:

  a list of data related to build outcome `<list>`

- `funs`:

  symbol names for model functions in the shared object

- `annot`:

  model annotations `<list>`

- `plugin`:

  model plugins `<character>`

- `Icap`:

  capture indices to recover in the simulation `<integer>`

- `capL`:

  labels for `Icap`; `<character>`

- `Icmt`:

  compartment indices to recover in the simulation `<integer>`

- `cmtL`:

  labels for `Icmt`; `<character>`

- `ss_cmt`:

  compartments numbers to be considered when advancing the system to
  steady state `<integer>`

## Notes

- Spaces in paths (`project` and `soloc`) are prohibited.

## See also

[`update`](https://mrgsolve.org/docs/reference/update.md),
[`solversettings`](https://mrgsolve.org/docs/reference/solversettings.md)
