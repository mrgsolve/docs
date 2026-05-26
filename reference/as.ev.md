# Coerce an object to class ev

Use this function to convert a data frame to an event object.

## Usage

``` r
as.ev(x, ...)

# S4 method for class 'data.frame'
as.ev(x, keep_id = TRUE, clean = FALSE, ...)

# S4 method for class 'ev'
as.ev(x, ...)
```

## Arguments

- x:

  an object to coerce.

- ...:

  not used.

- keep_id:

  if `TRUE`, ID column is retained if it exists.

- clean:

  if `TRUE`, only dosing or ID information is retained in the result.

## Value

An object with class ev.

## Details

If `CMT` (or `cmt`) is missing from the input, it will be set to 1 in
the event object.

If `TIME` (or `time`) is missing from the input, it will be set to 0 in
the event object.

If `EVID` (or `evid`) is missing from the input, it will be set to 1 in
the event object.

## Examples

``` r
data <- data.frame(AMT = 100) 

as.ev(data)
#> Events:
#>   time amt cmt evid
#> 1    0 100   1    1

as.ev(data, clean = TRUE)
#> Events:
#>   amt cmt evid
#> 1 100   1    1
```
