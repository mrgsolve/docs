# Return the code blocks from a model specification file

Return the code blocks from a model specification file

## Usage

``` r
blocks(x, ...)

# S4 method for class 'mrgmod'
blocks(x, ...)

# S4 method for class 'character'
blocks(x, ...)
```

## Arguments

- x:

  model object or path to model specification file

- ...:

  passed along

## Examples

``` r
mod <- mrgsolve::house()
mod %>% blocks
#> 
#> Model file: housemodel.cpp 
#> 
#> $PARAM
#> @annotated
#> CL   : 1    : Clearance  (L/hr)
#> VC   : 20   : Volume of distribution (L)
#> KA   : 1.2  : Absorption rate constant (1/hr)
#> F1   : 1.0  : Bioavailability fraction (.)
#> D1   : 2.0  : Infusion duration (hr)
#> WTCL : 0.75 : Exponent WT on CL
#> WTVC : 1.00 : Exponent WT on VC
#> SEXCL: 0.7  : Prop cov effect on CL
#> SEXVC: 0.85 : Prop cov effect on VC
#> KIN  : 100  : Resp prod rate constant (1/hr)
#> KOUT : 2    : Resp elim rate constant (1/hr)
#> IC50 : 10   : Conc giving 50% max resp (ng/ml)
#> 
#> $PARAM
#> @annotated @covariates
#> WT   : 70   : Weight (kg)
#> SEX  :  0   : Covariate female sex
#> 
#> $MAIN
#> @!check_modeled_infusions
#> F_GUT = F1;
#> D_CENT = D1;
#> double CLi   = exp(log(CL)   + WTCL*log(WT/70) + log(SEXCL)*SEX + ECL);
#> double VCi   = exp(log(VC)   + WTVC*log(WT/70) + log(SEXVC)*SEX + EVC);
#> double KAi   = exp(log(KA)   + EKA);
#> double KOUTi = exp(log(KOUT) + EKOUT);
#> RESP_0 = KIN/KOUTi;
#> 
#> $ODE
#> dxdt_GUT = -KAi*GUT;
#> dxdt_CENT = KAi*GUT - (CLi/VCi)*CENT;
#> dxdt_RESP = KIN*(1-INH) - KOUTi*RESP;
#> 
#> $TABLE
#> double DV = CP*exp(EXPO);
mod %>% blocks(PARAM,TABLE)
#> 
#> Model file: housemodel.cpp 
#> 
#> $PARAM
#> @annotated
#> CL   : 1    : Clearance  (L/hr)
#> VC   : 20   : Volume of distribution (L)
#> KA   : 1.2  : Absorption rate constant (1/hr)
#> F1   : 1.0  : Bioavailability fraction (.)
#> D1   : 2.0  : Infusion duration (hr)
#> WTCL : 0.75 : Exponent WT on CL
#> WTVC : 1.00 : Exponent WT on VC
#> SEXCL: 0.7  : Prop cov effect on CL
#> SEXVC: 0.85 : Prop cov effect on VC
#> KIN  : 100  : Resp prod rate constant (1/hr)
#> KOUT : 2    : Resp elim rate constant (1/hr)
#> IC50 : 10   : Conc giving 50% max resp (ng/ml)
#> 
#> $PARAM
#> @annotated @covariates
#> WT   : 70   : Weight (kg)
#> SEX  :  0   : Covariate female sex
#> 
#> $TABLE
#> double DV = CP*exp(EXPO);
```
