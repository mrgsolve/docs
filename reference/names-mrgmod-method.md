# Get all names from a model object

Get all names from a model object

## Usage

``` r
# S4 method for class 'mrgmod'
names(x)
```

## Arguments

- x:

  the model object

## Examples

``` r
mod <- mrgsolve::house()
names(mod)
#> $param
#>  [1] "CL"    "VC"    "KA"    "F1"    "D1"    "WTCL"  "WTVC"  "SEXCL" "SEXVC"
#> [10] "KIN"   "KOUT"  "IC50"  "WT"    "SEX"  
#> 
#> $init
#> [1] "GUT"  "CENT" "RESP"
#> 
#> $capture
#> [1] "DV" "CP"
#> 
#> $omega
#> [1] "..."
#> 
#> $sigma
#> [1] "..."
#> 
#> $omega_labels
#> $omega_labels[[1]]
#> [1] "ECL"   "EVC"   "EKA"   "EKOUT"
#> 
#> 
#> $sigma_labels
#> $sigma_labels[[1]]
#> [1] "EXPO"
#> 
#> 
```
