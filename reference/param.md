# Create and work with parameter objects

See [numericlist](https://mrgsolve.org/docs/reference/numericlist.md)
for methods to deal with `parameter_list` objects.

## Usage

``` r
param(.x, ...)

# S4 method for class 'mrgmod'
param(.x, .y = NULL, ..., .pat = "*", .strict = FALSE)

# S4 method for class 'mrgsims'
param(.x, ...)

# S4 method for class 'missing'
param(..., .strict = TRUE)

# S4 method for class 'list'
param(.x, ...)

# S4 method for class 'ANY'
param(.x, ...)

allparam(.x)
```

## Arguments

- .x:

  the model object.

- ...:

  passed along or name/value pairs to update the parameters in a model
  object; when passing new values this way, all values must be numeric
  and all all names must exist in the parameter list for `.x`.

- .y:

  an object to be merged into parameter list; non-`NULL` values must be
  named `list`, `data.frame`, `numeric` vector, or `parameter_list`
  object; named items that do not exist in the parameter list are
  allowed and will be silently ignored; use the `.strict` argument to
  require that all names in `.y` exist already in the parameter list.

- .pat:

  a regular expression (character) to be applied as a filter for which
  parameters to show when printing.

- .strict:

  if `TRUE`, all names to be updated must be found in the parameter
  list.

## Value

An object of class `parameter_list` (see
[numericlist](https://mrgsolve.org/docs/reference/numericlist.md)).

## Details

Can be used to either get a parameter list object from a `mrgmod` model
object or to update the parameters in a model object. For both uses, the
return value is a `parameter_list` object. For the former use, `param()`
is usually called to print the parameters to the screen, but the
`parameter_list` object can also be coerced to a list or numeric R
object.

Use `allparam()` to get a `parameter_list` object including both model
parameters and data items listed in `$FIXED`.

The update to parameters can be permissive (candidates with names that
don't exist in the parameter list are silently ignored) or strict (all
candidates must already exist in the parameter list). When passing
candidate values via `...`, the update is strict and an error is
generated if you pass a name that isn't found in the parameter list.
When candidate values are passed as a named object via `.y`, then the
update is permissive. Any permissive update can be made strict (error if
foreign names are found in the candidates) by passing `.strict = TRUE`.

An alternative is to assess the incoming names using
[`inventory()`](https://mrgsolve.org/docs/reference/inventory.md).

## See also

[`inventory()`](https://mrgsolve.org/docs/reference/inventory.md)

## Examples

``` r
## example("param")

mod <- house()

param(mod)
#> 
#>  Model parameters (N=14):
#>  name value . name  value
#>  CL   1     | SEX   0    
#>  D1   2     | SEXCL 0.7  
#>  F1   1     | SEXVC 0.85 
#>  IC50 10    | VC    20   
#>  KA   1.2   | WT    70   
#>  KIN  100   | WTCL  0.75 
#>  KOUT 2     | WTVC  1    

param(mod, .pat="^(C|F)") ## may be useful when large number of parameters
#> 
#>  Model parameters (N=14):
#>  name value . name value
#>  CL   1     | F1   1    

class(param(mod))
#> [1] "parameter_list"
#> attr(,"package")
#> [1] "mrgsolve"

param(mod)$KA
#> [1] 1.2

param(mod)[["KA"]]
#> [1] 1.2

as.list(param(mod))
#> $CL
#> [1] 1
#> 
#> $VC
#> [1] 20
#> 
#> $KA
#> [1] 1.2
#> 
#> $F1
#> [1] 1
#> 
#> $D1
#> [1] 2
#> 
#> $WTCL
#> [1] 0.75
#> 
#> $WTVC
#> [1] 1
#> 
#> $SEXCL
#> [1] 0.7
#> 
#> $SEXVC
#> [1] 0.85
#> 
#> $KIN
#> [1] 100
#> 
#> $KOUT
#> [1] 2
#> 
#> $IC50
#> [1] 10
#> 
#> $WT
#> [1] 70
#> 
#> $SEX
#> [1] 0
#> 

as.data.frame(param(mod))
#>   CL VC  KA F1 D1 WTCL WTVC SEXCL SEXVC KIN KOUT IC50 WT SEX
#> 1  1 20 1.2  1  2 0.75    1   0.7  0.85 100    2   10 70   0

mod <- param(mod, CL = 1.2)

new_values <- list(CL = 1.3, VC = 20.5)

mod <- param(mod, new_values)

```
