# Repeat a block of dosing events

Repeat a block of dosing events

## Usage

``` r
ev_repeat(x, n, wait = 0, as.ev = FALSE)
```

## Arguments

- x:

  event object or dosing data frame.

- n:

  number of times to repeat.

- wait:

  time to wait between repeats.

- as.ev:

  if `TRUE`, an event object is returned; otherwise a data.frame is
  returned.

## Value

See `as.ev` argument.

## Examples

``` r
e1 <- ev(amt = 100, ii = 24, addl = 20)
e4 <- ev_repeat(e1, n = 4, wait = 168)
mod <- mrgsolve::house()
out <- mrgsim(mod, events = e4, end = 3200)
plot(out, "CP")

```
