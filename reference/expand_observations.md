# Insert observations into a data set

Insert observations into a data set

## Usage

``` r
expand_observations(data, times, unique = FALSE, obs_pos = -1L)
```

## Arguments

- data:

  a data set or event object.

- times:

  a vector of observation times.

- unique:

  `logical`; if `TRUE` then values for `time` are dropped if they are
  found anywhere in `data`.

- obs_pos:

  determines sorting order for observations; use `-1` (default) to put
  observations first; otherwise, use large integer to ensure
  observations are placed after doses.

## Value

A data frame with additional rows for added observation records.

## Details

Non-numeric columns will be dropped with a warning.

## Examples

``` r
data <- expand.ev(amt = c(100, 200, 300))

expand_observations(data, times = seq(0, 48, 2))
#>    ID time amt cmt evid
#> 1   1    0   0   0    0
#> 2   1    0 100   1    1
#> 3   1    2   0   0    0
#> 4   1    4   0   0    0
#> 5   1    6   0   0    0
#> 6   1    8   0   0    0
#> 7   1   10   0   0    0
#> 8   1   12   0   0    0
#> 9   1   14   0   0    0
#> 10  1   16   0   0    0
#> 11  1   18   0   0    0
#> 12  1   20   0   0    0
#> 13  1   22   0   0    0
#> 14  1   24   0   0    0
#> 15  1   26   0   0    0
#> 16  1   28   0   0    0
#> 17  1   30   0   0    0
#> 18  1   32   0   0    0
#> 19  1   34   0   0    0
#> 20  1   36   0   0    0
#> 21  1   38   0   0    0
#> 22  1   40   0   0    0
#> 23  1   42   0   0    0
#> 24  1   44   0   0    0
#> 25  1   46   0   0    0
#> 26  1   48   0   0    0
#> 27  2    0   0   0    0
#> 28  2    0 200   1    1
#> 29  2    2   0   0    0
#> 30  2    4   0   0    0
#> 31  2    6   0   0    0
#> 32  2    8   0   0    0
#> 33  2   10   0   0    0
#> 34  2   12   0   0    0
#> 35  2   14   0   0    0
#> 36  2   16   0   0    0
#> 37  2   18   0   0    0
#> 38  2   20   0   0    0
#> 39  2   22   0   0    0
#> 40  2   24   0   0    0
#> 41  2   26   0   0    0
#> 42  2   28   0   0    0
#> 43  2   30   0   0    0
#> 44  2   32   0   0    0
#> 45  2   34   0   0    0
#> 46  2   36   0   0    0
#> 47  2   38   0   0    0
#> 48  2   40   0   0    0
#> 49  2   42   0   0    0
#> 50  2   44   0   0    0
#> 51  2   46   0   0    0
#> 52  2   48   0   0    0
#> 53  3    0   0   0    0
#> 54  3    0 300   1    1
#> 55  3    2   0   0    0
#> 56  3    4   0   0    0
#> 57  3    6   0   0    0
#> 58  3    8   0   0    0
#> 59  3   10   0   0    0
#> 60  3   12   0   0    0
#> 61  3   14   0   0    0
#> 62  3   16   0   0    0
#> 63  3   18   0   0    0
#> 64  3   20   0   0    0
#> 65  3   22   0   0    0
#> 66  3   24   0   0    0
#> 67  3   26   0   0    0
#> 68  3   28   0   0    0
#> 69  3   30   0   0    0
#> 70  3   32   0   0    0
#> 71  3   34   0   0    0
#> 72  3   36   0   0    0
#> 73  3   38   0   0    0
#> 74  3   40   0   0    0
#> 75  3   42   0   0    0
#> 76  3   44   0   0    0
#> 77  3   46   0   0    0
#> 78  3   48   0   0    0
```
