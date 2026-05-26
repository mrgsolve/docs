# Scrape options from a code block

Scrape options from a code block

## Usage

``` r
scrape_opts(
  x,
  envir = list(),
  def = list(),
  all = TRUE,
  marker = "=",
  allow_multiple = FALSE,
  narrow = TRUE
)
```

## Arguments

- x:

  data

- envir:

  environment from `$ENV`

- def:

  default values

- all:

  return all options, even those that are not in `def`

- marker:

  assignment operator; used to locate lines with options

- allow_multiple:

  if `TRUE`, the list with replicate names will be reduced

- narrow:

  logical; if `TRUE`, only get options on lines starting with `>>`

## Value

list with elements `x` (the data without options) and named options as
specified in the block.
