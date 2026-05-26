# Coerce a model object to list

Coerce a model object to list

## Usage

``` r
# S4 method for class 'mrgmod'
as.list(x, deep = FALSE, ...)
```

## Arguments

- x:

  a model object.

- deep:

  if `TRUE`, extra information is returned in the output list (see
  **Details**).

- ...:

  not used.

## Value

A named list containing formatted contents from `x`.

## Details

If `deep` is `TRUE`, then the values for `trans`, `advan`, and `mindt`
are returned as well as a summary of internal model functions (with a
call to `mrgsolve:::funset()`).

## Slots

- `npar`: number of parameters

- `neq`: number of compartments or differential equations

- `pars`: names of model parameters

- `covariates`: names of parameters identified as covariates

- `cmt`: names of model compartments

- `param`: the parameter list

- `init`: initial condition list

- `omega`: `$OMEGA` matrices, as a `matlist` object

- `sigma`: `$SIGMA` matrices, as a `matlist` object

- `fixed`: named list of `$FIXED` values

- `model`: model name

- `project`: model project directory

- `soloc`: directory where the model is being built

- `sodll`: complete path to the model shared object

- `cfile`: path for the model source code file

- `shlib`: list of compilation information

- `start`: simulation start time

- `end`: simulation end time

- `delta`: simulation time step

- `add`: additional simulation times

- `capture`: names of captured data items

- `request`: compartments requested upon simulation

- `cmti`: named indices for current output compartments

- `capturei`: named indices for current output capture

- `random`: names and labels of `$OMEGA` and `$SIGMA`

- `code`: model source code from `cfile`

- `details`: model details data frame

- `nm_import`: a character vector listing the names of nonmem output
  files that were read to import estimates from a completed nonmem run

- `cpp_variables`: a data frame listing variables internal to the model
  cpp file

- `atol`: see
  [solversettings](https://mrgsolve.org/docs/reference/solversettings.md)

- `rtol`: see
  [solversettings](https://mrgsolve.org/docs/reference/solversettings.md)

- `ss_atol`: absolute tolerance to use when advancing to PK steady state

- `ss_rtol`: relative tolerance to use when advancing to PK steady state

- `custom_atol`: absolute tolerances, one for each compartment

- `custom_rtol`: relative tolerances, one for each compartment

- `maxsteps`: see
  [solversettings](https://mrgsolve.org/docs/reference/solversettings.md)

- `hmin`: see
  [solversettings](https://mrgsolve.org/docs/reference/solversettings.md)

- `hmax`: see
  [solversettings](https://mrgsolve.org/docs/reference/solversettings.md)

- `itol`: 1 (use scalar values) or 4 (use customized values)

- `itol_type`: either "scalar" (`itol = 1`) or "custom" (`itol = 4`)

- `envir`: the model environment

- `plugins`: plugins invoked in the model

- `digits`: number of digits to request in simulated data

- `tscale`: multiplicative scalar for time in results only

- `mindt`: simulation output time below which there model will assume to
  have not advanced

- `preclean`: logical indicating to clean up compilation artifacts prior
  to compiling

- `debug`: print debugging information during simulation run

- `verbose`: print extra information during setup for model run

## Examples

``` r
mod <- mrgsolve::house()
l <- as.list(mod)
```
