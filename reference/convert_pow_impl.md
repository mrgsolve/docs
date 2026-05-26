# Convert Fortran-style exponentiation to C++ pow()

Translates `base**exponent` to `pow(base, exponent)` in each element of
`code`, handling arbitrarily nested expressions. Numeric literals are
preserved exactly as written. A trailing semicolon is preserved if
present.

## Usage

``` r
convert_pow_impl(code, block)
```

## Arguments

- code:

  Character vector of source lines.

- block:

  Name of the model block, included in the warning message.

## Value

Character vector with `**` replaced by `pow()`.
