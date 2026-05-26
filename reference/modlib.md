# Internal model library

Pre-coded models are included in the mrgsolve installation; these can be
compiled and loaded with `modlib()`. These models are usually most
useful for exploratory simulation or learning mrgsolve. Production
simulation work is typically accomplished by a custom-coded model.

## Usage

``` r
modlib(model = NULL, ..., list = FALSE)
```

## Arguments

- model:

  `character` name of a model in the library.

- ...:

  passed to
  [`mread_cache()`](https://mrgsolve.org/docs/reference/mread.md).

- list:

  logical; if `TRUE`, a list of available models is returned.

## Details

See
[modlib_details](https://mrgsolve.org/docs/reference/modlib_details.md),
[modlib_pk](https://mrgsolve.org/docs/reference/modlib_pk.md),
[modlib_pkpd](https://mrgsolve.org/docs/reference/modlib_pkpd.md),
[modlib_tmdd](https://mrgsolve.org/docs/reference/modlib_tmdd.md),
[modlib_viral](https://mrgsolve.org/docs/reference/modlib_viral.md) for
details.

Call `modlib("<modelname>")` to compile and load a mode from the
library.

Call `modlib(list=TRUE)` to list available models. Once the model is
loaded (see examples below), call `as.list(mod)$code` to extract model
code and equations.

## Examples

``` r
if (FALSE) { # \dontrun{
mod <- mread("pk1cmt", modlib())
mod <- mread("pk2cmt", modlib()) 
mod <- mread("pk3cmt", modlib()) 
mod <- mread("pk1",    modlib())
mod <- mread("pk2",    modlib())
mod <- mread("pk3",    modlib())
mod <- mread("popex",  modlib())
mod <- mread("irm1",   modlib()) 
mod <- mread("irm2",   modlib()) 
mod <- mread("irm3",   modlib()) 
mod <- mread("irm4",   modlib())
mod <- mread("emax",   modlib())
mod <- mread("effect", modlib())
mod <- mread("tmdd",   modlib())
mod <- mread("viral1", modlib())
mod <- mread("viral2", modlib())
mod <- mread("pred1",  modlib())
mod <- mread("pbpk",   modlib())
mod <- mread("1005",   modlib())  # embedded NONMEM result
mod <- mread("nm-like", modlib()) # model with nonmem-like syntax
mod <- mread("evtools", modlib())

as.list(mod)$code
} # }
```
