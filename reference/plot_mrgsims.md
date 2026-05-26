# Generate a quick plot of simulated data

Generate a quick plot of simulated data

## Usage

``` r
# S4 method for class 'mrgsims,missing'
plot(x, limit = 16, ...)

# S4 method for class 'mrgsims,formula'
plot(
  x,
  y,
  limit = 16,
  show.grid = TRUE,
  outer = TRUE,
  type = "l",
  lwd = 2,
  ylab = "value",
  groups = ID,
  scales = list(y = list(relation = "free")),
  fixy = NULL,
  logy = NULL,
  logbr = 0,
  equispaced.log = FALSE,
  ...
)

# S4 method for class 'mrgsims,character'
plot(x, y, ...)
```

## Arguments

- x:

  mrgsims object.

- limit:

  limit the the number of panels to create.

- ...:

  other arguments passed to
  [`lattice::xyplot()`](https://rdrr.io/pkg/lattice/man/xyplot.html).

- y:

  formula used for plotting.

- show.grid:

  logical indicating whether or not to draw `panel.grid`.

- outer:

  passed to
  [`lattice::xyplot()`](https://rdrr.io/pkg/lattice/man/xyplot.html).

- type:

  passed to
  [`lattice::xyplot()`](https://rdrr.io/pkg/lattice/man/xyplot.html).

- lwd:

  passed to
  [`lattice::xyplot()`](https://rdrr.io/pkg/lattice/man/xyplot.html).

- ylab:

  passed to
  [`lattice::xyplot()`](https://rdrr.io/pkg/lattice/man/xyplot.html).

- groups:

  passed to
  [`lattice::xyplot()`](https://rdrr.io/pkg/lattice/man/xyplot.html).

- scales:

  passed to
  [`lattice::xyplot()`](https://rdrr.io/pkg/lattice/man/xyplot.html).

- fixy:

  make the y-axis scale the same for all variables; ignored if `scales`
  is not a list.

- logy:

  plot the y variables on log scale; ignored if `scales` is not a list.

- logbr:

  log scale breaks indicator; use `1` for breaks every log unit; use `3`
  for breaks every half log unit; use `0` for default breaks; ignored if
  `scales` is not a list.

- equispaced.log:

  see `scales` argument in
  [`lattice::xyplot()`](https://rdrr.io/pkg/lattice/man/xyplot.html);
  ignored if `scales` is not a list.

## Examples

``` r

mod <- mrgsolve::house(end=48, delta=0.2) %>% init(GUT=1000)

out <- mrgsim(mod)

plot(out)


plot(out, subset=time <= 24)


plot(out, GUT + CP ~ .)


plot(out, CP + RESP ~ time, col = "black", fixy = TRUE, lty = 2)


if (FALSE) { # \dontrun{
plot(out, "CP RESP, GUT")
} # }
```
