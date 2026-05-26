# Create a simtime object

simtime objects allow the user to specify simulation start and end
times, along with the simulation time step.

## Usage

``` r
tgrid(
  start = 0,
  end = 24,
  delta = 1,
  add = numeric(0),
  .offset = 0,
  .scale = 1,
  ...
)

# S4 method for class 'tgrid'
stime(x, ...)

# S4 method for class 'tgrids'
stime(x, ...)

# S4 method for class 'numeric'
stime(x, ...)

# S4 method for class 'tgrid'
show(object)

# S4 method for class 'tgrids'
show(object)

# S4 method for class 'mrgmod'
stime(x, ...)
```

## Arguments

- start:

  simulation start time.

- end:

  simulation end time.

- delta:

  simulation time step.

- add:

  addition simulation times.

- .offset:

  the resulting set of times will be adjusted by this amount.

- .scale:

  the resulting set of times will be scaled by this factor.

- ...:

  not used.

- x:

  tgrid object.

- object:

  passed to show

## Examples

``` r
peak <- tgrid(0, 6, 0.2)
sparse <- tgrid(0, 24, 4)

day1 <- c(peak, sparse)

design <- c(day1, day1+72, day1+240)

if (FALSE) { # \dontrun{
mod <- mrgsolve::house()

out <- mod %>% ev(amt=1000, ii=24, addl=10) %>% mrgsim(tgrid=design)

plot(out, CP ~ time, type = 'b')
} # }
```
