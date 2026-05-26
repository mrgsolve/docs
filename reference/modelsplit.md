# Split and reassemble model specification text

`modelsplit()` parses model specification text into a named list of code
blocks, retaining enough information to reconstruct the original text.
`modelunsplit()` takes the list returned by `modelsplit()` and puts the
blocks back together into a character vector of model code.

## Usage

``` r
modelsplit(x)

modelunsplit(x)
```

## Arguments

- x:

  for `modelsplit()`, model specification text (character vector or
  single string); for `modelunsplit()`, a list returned by
  `modelsplit()`.

## Value

`modelsplit()` returns a named list of character vectors, one element
per block. `modelunsplit()` returns a character vector of model code.

## See also

[`modelparse()`](https://mrgsolve.org/docs/reference/modelparse.md) that
drops blank lines and comments by default.
