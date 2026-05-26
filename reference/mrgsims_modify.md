# Methods for modifying mrgsims objects

These functions modify the simulated data in an mrgsims object and
return the modified object. Contrast with the functions in
[mrgsims_dplyr](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md).

## Usage

``` r
mutate_sims(.data, ...)

select_sims(.data, ...)

filter_sims(.data, ...)
```

## Arguments

- .data:

  a mrgsims object.

- ...:

  other arguments passed to the `dplyr` functions.

## See also

[mrgsims_dplyr](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)

## Examples

``` r

out <- mrgsim(house(), events = ev(amt = 100))

filter_sims(out, time > 2)
#> Model:  housemodel 
#> Dim:    472 x 7 
#> Time:   2.25 to 120 
#> ID:     1 
#>     ID time   GUT  CENT  RESP    DV    CP
#> 1:   1 2.25 6.721 86.23 35.84 4.312 4.312
#> 2:   1 2.50 4.979 86.89 35.46 4.345 4.345
#> 3:   1 2.75 3.688 87.09 35.22 4.355 4.355
#> 4:   1 3.00 2.732 86.96 35.07 4.348 4.348
#> 5:   1 3.25 2.024 86.59 34.99 4.329 4.329
#> 6:   1 3.50 1.500 86.03 34.97 4.302 4.302
#> 7:   1 3.75 1.111 85.35 34.98 4.267 4.267
#> 8:   1 4.00 0.823 84.57 35.03 4.229 4.229

mutate_sims(out, label = "abc")
#> Model:  housemodel 
#> Dim:    482 x 8 
#> Time:   0 to 120 
#> ID:     1 
#>     ID time    GUT  CENT  RESP    DV    CP label
#> 1:   1 0.00   0.00  0.00 50.00 0.000 0.000   abc
#> 2:   1 0.00 100.00  0.00 50.00 0.000 0.000   abc
#> 3:   1 0.25  74.08 25.75 48.68 1.287 1.287   abc
#> 4:   1 0.50  54.88 44.50 46.18 2.225 2.225   abc
#> 5:   1 0.75  40.66 58.08 43.61 2.904 2.904   abc
#> 6:   1 1.00  30.12 67.83 41.38 3.391 3.391   abc
#> 7:   1 1.25  22.31 74.74 39.58 3.737 3.737   abc
#> 8:   1 1.50  16.53 79.56 38.18 3.978 3.978   abc

select_sims(out, RESP, CP)
#> Model:  housemodel 
#> Dim:    482 x 4 
#> Time:   0 to 120 
#> ID:     1 
#>     ID time  RESP    CP
#> 1:   1 0.00 50.00 0.000
#> 2:   1 0.00 50.00 0.000
#> 3:   1 0.25 48.68 1.287
#> 4:   1 0.50 46.18 2.225
#> 5:   1 0.75 43.61 2.904
#> 6:   1 1.00 41.38 3.391
#> 7:   1 1.25 39.58 3.737
#> 8:   1 1.50 38.18 3.978
```
