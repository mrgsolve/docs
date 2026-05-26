# Replicate a list of events into a data set

Replicate a list of events into a data set

## Usage

``` r
ev_assign(l, idata, evgroup, join = FALSE)

assign_ev(...)
```

## Arguments

- l:

  list of event objects.

- idata:

  an idata set (one ID per row).

- evgroup:

  the character name of the column in `idata` that specifies event
  object to implement.

- join:

  if `TRUE`, join `idata` to the data set before returning.

- ...:

  used to pass arguments from `assign_ev()`. to `ev_assign()`.

## Details

`ev_assign()` connects events in a list passed in as the `l` argument to
values in the data set identified in the `evgroup` argument. For making
assignments, the unique values in the `evgroup` column are first sorted
so that the first sorted unique value in `evgroup` is assigned to the
first event in `l`, the second sorted value in `evgroup` column is
assigned to the second event in `l`, and so on. This is a change from
previous behavior, which did not sort the unique values in `evgroup`
prior to making the assignments.

## Examples

``` r
ev1 <- ev(amt = 100)
ev2 <- ev(amt = 300, rate = 100, ii = 12, addl = 10)

idata <- data.frame(ID = seq(10)) 
idata$arm <- 1+(idata$ID %%2)

ev_assign(list(ev1, ev2), idata, "arm", join = TRUE)
#>    time amt cmt evid rate ii addl ID arm
#> 1     0 300   1    1  100 12   10  1   2
#> 2     0 100   1    1    0  0    0  2   1
#> 3     0 300   1    1  100 12   10  3   2
#> 4     0 100   1    1    0  0    0  4   1
#> 5     0 300   1    1  100 12   10  5   2
#> 6     0 100   1    1    0  0    0  6   1
#> 7     0 300   1    1  100 12   10  7   2
#> 8     0 100   1    1    0  0    0  8   1
#> 9     0 300   1    1  100 12   10  9   2
#> 10    0 100   1    1    0  0    0 10   1
```
