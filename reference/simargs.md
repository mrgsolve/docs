# Access or clear arguments for calls to mrgsim()

As a model object navigates a pipeline prior to simulation, arguments
are collected to eventually be passed to
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md). `simargs()`
lets you intercept and possibly clear those arguments.

## Usage

``` r
simargs(x, which = NULL, clear = FALSE, ...)
```

## Arguments

- x:

  model object.

- which:

  character with length 1 naming a single arg to get.

- clear:

  logical indicating whether or not to clear `args` from the model
  object.

- ...:

  not used.

## Value

If `clear` is `TRUE`, the argument list is cleared and the model object
is returned. Otherwise, the argument list is returned.

## Examples

``` r
mod <- mrgsolve::house()
mod %>% Req(CP, RESP) %>% carry_out(evid, WT, FLAG) %>% simargs()
#> $carry_out
#> [1] "evid, WT, FLAG"
#> 
```
