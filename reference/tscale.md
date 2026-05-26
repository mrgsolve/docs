# Re-scale time in the simulated output

Re-scale time in the simulated output

## Usage

``` r
tscale(x, value = 1, ...)
```

## Arguments

- x:

  model object.

- value:

  value by which time will be scaled.

- ...:

  not used.

## Details

There is also a `tscale` argument to
[`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md) that can be
set to accomplish the same thing as a call to `tscale` in the pipeline.

## Examples

``` r
# The model is in hours:
mod <- mrgsolve::house()

# The output is in days:
mod %>% tscale(1/24) %>% mrgsim()
#> Model:  housemodel 
#> Dim:    481 x 7 
#> Time:   0 to 5 
#> ID:     1 
#>     ID    time GUT CENT RESP DV CP
#> 1:   1 0.00000   0    0   50  0  0
#> 2:   1 0.01042   0    0   50  0  0
#> 3:   1 0.02083   0    0   50  0  0
#> 4:   1 0.03125   0    0   50  0  0
#> 5:   1 0.04167   0    0   50  0  0
#> 6:   1 0.05208   0    0   50  0  0
#> 7:   1 0.06250   0    0   50  0  0
#> 8:   1 0.07292   0    0   50  0  0
```
