# Various methods for event objects

Various methods for event objects

## Usage

``` r
# S3 method for class 'ev'
names(x)

# S3 method for class 'ev'
dim(x)

# S3 method for class 'ev'
as.matrix(x, ...)

# S3 method for class 'ev'
as.data.frame(x, row.names = NULL, optional = FALSE, add_ID = NULL, ...)

# S4 method for class 'ev'
show(object)
```

## Arguments

- x:

  an events object

- ...:

  passed to various methods

- row.names:

  passed to [`as.data.frame`](https://rdrr.io/r/base/as.data.frame.html)

- optional:

  passed to [`as.data.frame`](https://rdrr.io/r/base/as.data.frame.html)

- add_ID:

  numeric ID of length 1 used to add `ID` column only if one doesn't
  already exist

- object:

  used for `show`

## Examples

``` r

e <- ev(amt = 100)

names(e)
#> [1] "time" "amt"  "cmt"  "evid"

as.data.frame(e)
#>   time amt cmt evid
#> 1    0 100   1    1

dim(e)
#> [1] 1 4

nrow(e)
#> [1] 1
```
