# Methods for working with the model compartment list

Calling `init()` with the model object as the first argument will return
the model initial conditions as a
[numericlist](https://mrgsolve.org/docs/reference/numericlist.md)
object. See
[numericlist](https://mrgsolve.org/docs/reference/numericlist.md) for
methods to deal with `cmt_list` objects.

## Usage

``` r
init(.x, ...)

# S4 method for class 'mrgmod'
init(.x, .y = list(), ..., .pat = "*")

# S4 method for class 'mrgsims'
init(.x, ...)

# S4 method for class 'missing'
init(.x, ...)

# S4 method for class 'list'
init(.x, ...)

# S4 method for class 'ANY'
init(.x, ...)
```

## Arguments

- .x:

  the model object.

- ...:

  `name = value` assignments to update the initial conditions list.

- .y:

  list to be merged into parameter list.

- .pat:

  a regular expression (character) to be applied as a filter when
  printing compartments to the screen.

## Value

An object of class `cmt_list` (see
[numericlist](https://mrgsolve.org/docs/reference/numericlist.md)).

## Details

Can be used to either get a compartment list object from a `mrgmod`
model object or to update the compartment initial conditions in a model
object. For both uses, the return value is a `cmt_list` object. For the
former use, `init()` is usually called to print the compartment initial
conditions to the screen, but the `cmt_list` object can also be coerced
to a list or numeric R object.

## Examples

``` r
## example("init")
mod <- mrgsolve::house()

init(mod)
#> 
#>  Model initial conditions (N=3):
#>  name       value . name       value
#>  CENT (2)   0     | RESP (3)   50   
#>  GUT (1)    0     | . ...      .    

init(mod, .pat="^C") ## may be useful for large models
#> 
#>  Model initial conditions (N=3):
#>  name       value . name    value
#>  CENT (2)   0     | . ...   .    

class(init(mod))
#> [1] "cmt_list"
#> attr(,"package")
#> [1] "mrgsolve"

init(mod)$CENT
#> [1] 0

as.list(init(mod))
#> $GUT
#> [1] 0
#> 
#> $CENT
#> [1] 0
#> 
#> $RESP
#> [1] 50
#> 

as.data.frame(init(mod))
#>   GUT CENT RESP
#> 1   0    0   50

```
