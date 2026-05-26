# Warn about literal integer division in model code

Scans each element of `code` and issues an R warning for every instance
of literal integer division found (e.g. `3/4`, `1/2`). Integer division
in C++ truncates toward zero, so `3/4` evaluates to `0` and `7/3`
evaluates to `2`, which is rarely intended.

## Usage

``` r
warn_int_div_impl(code, block)
```

## Arguments

- code:

  Character vector of source lines.

- block:

  Name of the model block, included in the warning message.

## Value

`code` unchanged (called for its side-effect warnings).
