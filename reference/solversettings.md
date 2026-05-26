# Optional inputs for lsoda

These are settings for the differential equation solver (`lsoda`) that
can be accessed via the R interface. The code listing below is taken
directly from the `lsoda` source code.

## Details

The following items can be set

- `hmax` (`HMAX` below); decrease `hmax` when you want to limit how big
  of a step the solver can take when integrating from one time to the
  next time. However be aware that smaller `hmax` will result in longer
  run times.

- `hmin` (`HMIN` below); don't fiddle with this unless you know what
  you're doing.

- `ixpr` (`IXPR` below)

- `maxsteps` (`MXSTEP` below); increase this number when the solver has
  a long interval between two integration times (e.g. when observation
  records are far apart).

- `mxhnil` (`MXHNIL below`); don't usually modify this one

- `atol` - the absolute solver tolerance; decrease this number (e.g. to
  1E-10 or 1E-20 or 1E-50) when the value in a compartment can get
  extremely small; without this extra (lower) tolerance, the value can
  get so low that the number can randomly become negative. However be
  aware that more precision here will result in longer run times.

- `rtol` - the relative solver tolerances; decrease this number when you
  want a more precise solution. However be aware that more precision
  here will result in longer run times.

## See also

[`aboutsolver`](https://mrgsolve.org/docs/reference/aboutsolver.md),
[`update`](https://mrgsolve.org/docs/reference/update.md)
