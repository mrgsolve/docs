# Merge two lists

Merge two lists

## Usage

``` r
# S3 method for class 'list'
merge(x, y, ..., open = FALSE, warn = TRUE, context = "object", wild = "...")
```

## Arguments

- x:

  the original list

- y:

  the new list for merging

- ...:

  not used

- open:

  logical indicating whether or not new items should be allowed in the
  list upon merging

- warn:

  issue warning if nothing found to update

- context:

  description of usage context

- wild:

  wild-card name; see details

## Details

Wild-card names (`wild`) are always retained in `x` and are brought
along from `y` only when `open`.
