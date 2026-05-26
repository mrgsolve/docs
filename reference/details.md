# Extract model details

Extract model details

## Usage

``` r
details(x, complete = FALSE, values = TRUE, ...)
```

## Arguments

- x:

  a model object

- complete:

  logical; if `TRUE`, un-annotated parameters and compartments will be
  added to the output

- values:

  logical; if `TRUE`, a values column will be added to the output

- ...:

  not used

## Details

This function is not exported. You will have to call it with
`mrgsolve:::details()`.

## Examples

``` r
mod <- mrgsolve::house()

mrgsolve:::details(mod)
#>      block  name                    descr     unit options  value
#> 1    PARAM    CL                Clearance     L/hr       .   1.00
#> 2    PARAM    VC   Volume of distribution        L       .  20.00
#> 3    PARAM    KA Absorption rate constant     1/hr       .   1.20
#> 4    PARAM    F1 Bioavailability fraction        .       .   1.00
#> 5    PARAM    D1        Infusion duration       hr       .   2.00
#> 6    PARAM  WTCL        Exponent WT on CL        .       .   0.75
#> 7    PARAM  WTVC        Exponent WT on VC        .       .   1.00
#> 8    PARAM SEXCL    Prop cov effect on CL        .       .   0.70
#> 9    PARAM SEXVC    Prop cov effect on VC        .       .   0.85
#> 10   PARAM   KIN  Resp prod rate constant     1/hr       . 100.00
#> 11   PARAM  KOUT  Resp elim rate constant     1/hr       .   2.00
#> 12   PARAM  IC50 Conc giving 50% max resp    ng/ml       .  10.00
#> 13   PARAM    WT                   Weight       kg       .  70.00
#> 14   PARAM   SEX     Covariate female sex        .       .   0.00
#> 15     CMT   GUT       Dosing compartment       mg       .   0.00
#> 16     CMT  CENT      Central compartment       mg       .   0.00
#> 17     CMT  RESP                 Response unitless       .  50.00
#> 18 CAPTURE    DV       Dependent variable    ng/ml       .     NA
#> 19 CAPTURE    CP     Plasma concentration    ng/ml       .     NA
```
