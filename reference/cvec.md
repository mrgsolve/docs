# Create create character vectors

Create create character vectors

## Usage

``` r
cvec(x)

# S3 method for class 'character'
cvec(x)

s_(...)
```

## Arguments

- x:

  comma-separated quoted string (for `cvec`)

- ...:

  unquoted strings (for `ch`)

## Examples

``` r

cvec("A,B,C")
#> [1] "A" "B" "C"
s_(A,B,C)
#> [1] "A" "B" "C"
```
