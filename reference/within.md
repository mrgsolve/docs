# Update parameters, initials, and settings within a model object

The main use case for using within rather than
[update](https://mrgsolve.org/docs/reference/update.md) or
[param](https://mrgsolve.org/docs/reference/param.md) or
[init](https://mrgsolve.org/docs/reference/init.md) is when you want to
update to a new value that is calculated from the existing value. See
the example in details

## Usage

``` r
# S3 method for class 'mrgmod'
within(data, expr, ...)
```

## Arguments

- data:

  an object with class mrgmod

- expr:

  expressions evaluated in an environment containing various model
  object components, including parameters, initial conditions, and
  others (see details)

- ...:

  not used

## Details

Other model object slots that can be updated: `start`, `end`, `delta`,
`add`, `rtol`, `atol`, `hmax`, `maxsteps`. These are include for
convenience, but we expect that most of the time these will get updated
through the update method.

## See also

[update](https://mrgsolve.org/docs/reference/update.md)

## Examples

``` r
mod <- mrgsolve::house()

mod2 <- within(mod, {CL <- CL * 1.5})

mod$CL
#> [1] 1
mod2$CL
#> [1] 1.5
```
