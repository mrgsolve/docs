# Operations for ev objects

Operations for ev objects

## Usage

``` r
# S4 method for class 'ev,ev'
e1 + e2

e1 %then% e2

# S4 method for class 'ev,ev'
e1 %then% e2

# S4 method for class 'ev'
c(x, ..., recursive = TRUE)
```

## Arguments

- e1:

  object on left hand side of operator (lhs)

- e2:

  object on right hand side of operator (rhs)

- x:

  an ev object

- ...:

  other ev objects to collect

- recursive:

  not used

## Details

All operations involving
[`mrgmod`](https://mrgsolve.org/docs/reference/mrgmod-class.md) objects
have been deprecated.
