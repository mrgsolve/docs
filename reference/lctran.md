# Change the case of nmtran-like data items

Previous data set requirements included lower case names for data items
like `AMT` and `EVID`. Lower case is no longer required. However, it is
still a requirement that nmtran like data column names are either all
lower case or all upper case.

## Usage

``` r
lctran(data, ...)

# S3 method for class 'data.frame'
lctran(data, warn = TRUE, ...)

# S3 method for class 'ev'
lctran(data, ...)

uctran(data, ...)

# S3 method for class 'data.frame'
uctran(data, warn = TRUE, ...)

# S3 method for class 'ev'
uctran(data, ...)
```

## Arguments

- data:

  a data set with nmtran-like format or an event object.

- ...:

  for potential future use.

- warn:

  if `TRUE`, a warning will be issued when there are both upper and
  lower case versions of any nmtran-like column in the data frame.

## Value

A data frame or event object, with column names possibly converted to
upper or lower case.

## Details

Columns that will be renamed with lower or upper case versions:

- `AMT / amt`

- `II / ii`

- `SS / ss`

- `CMT / cmt`

- `ADDL / addl`

- `RATE / rate`

- `EVID / evid`

- `TIME / time`

If both lower and upper case versions of the name are present in the
data frame, no changes will be made.

## Examples

``` r
data <- data.frame(TIME = 0, AMT = 5, II = 24, addl = 2, WT = 80)
lctran(data)
#>   time amt ii addl WT
#> 1    0   5 24    2 80

data <- data.frame(TIME = 0, AMT = 5, II = 24, addl = 2, wt = 80)
uctran(data)
#>   TIME AMT II ADDL wt
#> 1    0   5 24    2 80

ev <- evd(amt = 100, evid = 3)
uctran(ev)
#> Events Data:
#>   time amt cmt evid
#> 1    0 100   1    3

# warning
data <- data.frame(TIME = 1, time = 2, CMT = 5)
lctran(data)
#> Warning: There are both upper and lower case versions of some nmtran names in the data set
#>   TIME time cmt
#> 1    1    2   5
```
