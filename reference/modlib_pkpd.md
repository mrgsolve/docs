# modlib: Pharmacokinetic / pharmacodynamic models

modlib: Pharmacokinetic / pharmacodynamic models

## Details

See
[modlib_details](https://mrgsolve.org/docs/reference/modlib_details.md)
for more detailed descriptions of parameters and compartments.

All PK/PD models include 2-compartment PK model with absorption from 2
extravascular compartments and linear + nonlinear clearance. The PK
models are parameterized with `CL`, `V2`, `Q`,
`V3, `VMAX`, `KM`, `KA`and`KA2`and implement compartments`EV`, `EV2`, `CENT`, `PERIPH`. The indirect response models have compartment `RESP`and the emax model has output variable`RESP`. PD parameters include `KIN`, `KOUT`, `IC50`, `EC50`, `IMAX`, `EMAX`, `E0`, and `n\`.

Also, once the model is loaded, use the
[`see()`](https://mrgsolve.org/docs/reference/see.md) method for
`mrgmod` to view the model code.

## Model description

- `irm1`: inhibition of response production

- `irm2`: inhibition of response loss

- `irm3`: stimulation of response production

- `irm4`: stimulation of response loss

- `pd_effect`: effect compartment model

- `emax`: sigmoid emax model
