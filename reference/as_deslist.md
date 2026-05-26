# Create a list of designs from a data frame

Create a list of designs from a data frame

## Usage

``` r
as_deslist(data, descol = "ID")
```

## Arguments

- data:

  input data set; see **Details**.

- descol:

  character column name to be used for design groups.

## Value

The function returns a list of `tgrid` objects, one for each unique
value found in `descol`.

## Details

The input data set must have a column with the same name as the value of
`descol`. Other column names should be `start` (the time of the first
observation), `end` (the time of the last observation), `delta` (the
time steps to take between `start` and `end`), and `add` (other, ad-hoc
times). Note that `add` might be a `list-column` to get a vector of
times for each time grid object.

## Examples

``` r
idata <- tibble::tibble(ID=1:4, end=seq(24,96,24), delta=6,
add=list(c(122,124,135),c(111), c(99),c(88)))

idata <- dplyr::mutate(idata, GRP = ID %%2)

idata
#> # A tibble: 4 × 5
#>      ID   end delta add         GRP
#>   <int> <dbl> <dbl> <list>    <dbl>
#> 1     1    24     6 <dbl [3]>     1
#> 2     2    48     6 <dbl [1]>     0
#> 3     3    72     6 <dbl [1]>     1
#> 4     4    96     6 <dbl [1]>     0

l <- as_deslist(idata,"GRP")

l
#> $GRP_0
#> start:  0  end:    48  delta:  6  offset: 0  min:    0   max:    111 
#> 
#> $GRP_1
#> start:  0  end:    24  delta:  6  offset: 0  min:    0   max:    135 
#> 
#> attr(,"descol")
#> [1] "GRP"

lapply(l,stime)
#> $GRP_0
#>  [1]   0   6  12  18  24  30  36  42  48 111
#> 
#> $GRP_1
#> [1]   0   6  12  18  24 122 124 135
#> 

lapply(as_deslist(idata, "ID"),stime)
#> $ID_1
#> [1]   0   6  12  18  24 122 124 135
#> 
#> $ID_2
#>  [1]   0   6  12  18  24  30  36  42  48 111
#> 
#> $ID_3
#>  [1]  0  6 12 18 24 30 36 42 48 54 60 66 72 99
#> 
#> $ID_4
#>  [1]  0  6 12 18 24 30 36 42 48 54 60 66 72 78 84 88 90 96
#> 
```
