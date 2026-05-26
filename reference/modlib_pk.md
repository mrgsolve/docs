# modlib: Pharmacokinetic models

modlib: Pharmacokinetic models

## Arguments

- ...:

  passed to update.

## Details

See
[modlib_details](https://mrgsolve.org/docs/reference/modlib_details.md)
for more detailed descriptions of parameters and compartments.

The `pk1cmt` model is parameterized in terms of `CL`, `V`, `KA` and
`KA2` and uses compartments `EV`, `EV2`, and `CENT`. The `pk2cmt` model
adds a `PERIPH` compartment and parameters `Q` and `V3` to that of the
one-compartment model. Likewise, the three-compartment model (`pk3cmt`)
adds `PERIPH2` and parameters `Q4` and `V4` to that of the
two-compartment models. All pk models also have parameters `VMAX`
(defaulting to zero, no non-linear clearance) and `KM`.

## Model description

All ODE-based pk models have two extravascular dosing compartments and
potential for linear and nonlinear clearance.

- `pk1cmt`: one compartment pk model using ODEs

- `pk2cmt`: two compartment pk model using ODEs

- `pk3cmt`: three compartment pk model using ODEs

- `pk1`: one compartment pk model in closed-form

- `pk2`: two compartment pk model in closed-form

- `pk3`: three compartment pk model in closed-form

- `popex`: a simple population pk model
