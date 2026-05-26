# Load the model shared object

Once the model is compiled, the model object can be used to re-load the
model shared object (the compiled code underlying the mode) when the
simulation is to be done in a different R process.

## Usage

``` r
loadso(x, ...)

# S3 method for class 'mrgmod'
loadso(x, ...)
```

## Arguments

- x:

  a model object.

- ...:

  not used.

## Value

The model object (invisibly).

## Details

The `loadso` function most frequently needs to be used when
parallelizing simulations across worker nodes. The model can be run
after calling `loadso`, without requiring that it is re-compiled on
worker nodes. It is likely required that the model is built (and the
shared object stored) in a local directory off of the working R
directory (see the second example).

## Examples

``` r
if (FALSE) { # \dontrun{ 
  mod <- mread("pk1", modlib())
  loadso(mod)
  
  mod2 <- mread("pk2", modlib(), soloc = "build")
  loadso(mod2)
} # }
```
