# Make addl doses explicit in an event object or data set

When doses are scheduled with `ii` and `addl`, the object is expanded to
include one record for every dose. In the result, no record with have
`ii` or `addl` set to non-zero value.

## Usage

``` r
realize_addl(x, ...)

# S3 method for class 'data.frame'
realize_addl(
  x,
  warn = FALSE,
  mark_new = FALSE,
  fill = c("inherit", "na", "locf"),
  ...
)

# S3 method for class 'ev'
realize_addl(x, ...)
```

## Arguments

- x:

  a `data_set` data frame or an event object (see **Details**).

- ...:

  not used.

- warn:

  if `TRUE` a warning is issued if no `ADDL` or `addl` column is found.

- mark_new:

  if `TRUE`, a flag is added to indicate new columns.

- fill:

  specifies how to handle non-dose related data columns in new data set
  records; this option is critical when handling data sets with
  time-varying, non-dose-related data items; see **Details**.

## Value

A data.frame or event object, consistent with the type of `x`. The `ii`
and `addl` columns will all be set to zero. The result is always
ungrouped.

## Details

If no `addl` column is found the data frame is returned and a warning is
issued if `warn` is true. If `ii`, `time`, or `evid` are missing, an
error is generated.

If a grouped data.frame (via
[`dplyr::group_by()`](https://dplyr.tidyverse.org/reference/group_by.html))
is passed, it will be ungrouped.

Use caution when passing in data that has non-dose-related data columns
that vary within a subject and pay special attention to the `fill`
argument. By definition, `realize_addl()` will add new rows to your data
frame and it is not obvious how the non-dose-related data should be
handled in these new rows. When `inherit` is chosen, the new records
have non-dose-related data that is identical to the originating dose
record. This should be fine when these data items are not varying with
time, but will present a problem when the data are varying with time.
When `locf` is chosen, the missing data are filled in with `NA` and an
last observation carry forward operation is applied to **every** column
in the data set. This may not be what you want if you already had
missing values in the input data set and want to preserve that
missingness. When `na` is chosen, the missing data are filled in with
`NA` and no `locf` operation is applied. But note that these missing
values may be problematic for a mrgsolve simulation run. If you have any
time-varying columns or missing data in your data set, be sure to check
that the output from this function is what you were expecting.

## Examples

``` r
e <- ev(amt = 100, ii = 12, addl = 3)

realize_addl(e)
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100  0    0   1    1
#> 2   12 100  0    0   1    1
#> 3   24 100  0    0   1    1
#> 4   36 100  0    0   1    1

a <- ev(amt = 100, ii = 12, addl = 2, WT = 69)
b <- ev(amt = 200, ii = 24, addl = 2, WT = 70)
c <- ev(amt =  50, ii =  6, addl = 2, WT = 71) 

e <- ev_seq(a,b,c)
realize_addl(e, mark_new = TRUE)
#> Events:
#>   time amt ii addl cmt evid WT .addl_row_
#> 1    0 100  0    0   1    1 69          0
#> 2   12 100  0    0   1    1 69          1
#> 3   24 100  0    0   1    1 69          1
#> 4   36 200  0    0   1    1 70          0
#> 5   60 200  0    0   1    1 70          1
#> 6   84 200  0    0   1    1 70          1
#> 7  108  50  0    0   1    1 71          0
#> 8  114  50  0    0   1    1 71          1
#> 9  120  50  0    0   1    1 71          1
```
