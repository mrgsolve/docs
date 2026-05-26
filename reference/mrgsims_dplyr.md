# Methods for handling output with dplyr verbs

These methods modify the data in a mrgsims object and return a data
frame. Contrast with the functions in
[mrgsims_modify](https://mrgsolve.org/docs/reference/mrgsims_modify.md).

## Usage

``` r
# S3 method for class 'mrgsims'
pull(.data, ...)

# S3 method for class 'mrgsims'
filter(.data, ...)

# S3 method for class 'mrgsims'
group_by(.data, ..., .add = FALSE)

# S3 method for class 'mrgsims'
distinct(.data, ..., .keep_all = FALSE)

# S3 method for class 'mrgsims'
mutate(.data, ...)

# S3 method for class 'each'
summarise(...)

# S3 method for class 'mrgsims'
summarise(.data, ...)

# S3 method for class 'mrgsims'
do(.data, ..., .dots)

# S3 method for class 'mrgsims'
select(.data, ...)

# S3 method for class 'mrgsims'
slice(.data, ...)

as_data_frame.mrgsims(x, ...)

# S3 method for class 'mrgsims'
as_tibble(x, ...)

as.tbl.mrgsims(x, ...)
```

## Arguments

- .data:

  an mrgsims object; passed to various `dplyr` functions.

- ...:

  passed to other methods.

- .add:

  passed to
  [`dplyr::group_by()`](https://dplyr.tidyverse.org/reference/group_by.html).

- .keep_all:

  passed to
  [`dplyr::distinct()`](https://dplyr.tidyverse.org/reference/distinct.html).

- .dots:

  passed to various `dplyr` functions.

- x:

  mrgsims object.

## Details

For the `select_sims` function, the dots `...` must be either
compartment names or variables in `$CAPTURE`. An error will be generated
if no valid names are selected or the names for selection are not found
in the simulated output.

## See also

[mrgsims_modify](https://mrgsolve.org/docs/reference/mrgsims_modify.md)

## Examples

``` r

out <- mrgsim(house(), events = ev(amt = 100), end = 5, delta=1)

dplyr::filter(out, time==2)
#> # A tibble: 1 × 7
#>      ID  time   GUT  CENT  RESP    DV    CP
#>   <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
#> 1     1     2  9.07  85.0  36.4  4.25  4.25

dplyr::mutate(out, label = "abc")
#> # A tibble: 7 × 8
#>      ID  time     GUT  CENT  RESP    DV    CP label
#>   <dbl> <dbl>   <dbl> <dbl> <dbl> <dbl> <dbl> <chr>
#> 1     1     0   0       0    50    0     0    abc  
#> 2     1     0 100       0    50    0     0    abc  
#> 3     1     1  30.1    67.8  41.4  3.39  3.39 abc  
#> 4     1     2   9.07   85.0  36.4  4.25  4.25 abc  
#> 5     1     3   2.73   87.0  35.1  4.35  4.35 abc  
#> 6     1     4   0.823  84.6  35.0  4.23  4.23 abc  
#> 7     1     5   0.248  81.0  35.4  4.05  4.05 abc  

dplyr::select(out, time, RESP, CP)
#> # A tibble: 7 × 3
#>    time  RESP    CP
#>   <dbl> <dbl> <dbl>
#> 1     0  50    0   
#> 2     0  50    0   
#> 3     1  41.4  3.39
#> 4     2  36.4  4.25
#> 5     3  35.1  4.35
#> 6     4  35.0  4.23
#> 7     5  35.4  4.05
```
