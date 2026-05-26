# modlib: Target mediated disposition model

modlib: Target mediated disposition model

## Arguments

- ...:

  passed to update.

## Parameters

- `KEL`: elimination rate constant

- `KTP`: tissue to plasma rate constant

- `KPT`: plasma to tissue rate constant

- `V2`: volume of distribution

- `KA`, `KA2`: absorption rate constants

- `KINT`: internalization rate constant

- `KON`: association rate constant

- `KOFF`: dissociation rate constant

- `KSYN`: target synthesis rate

- `KDEG`: target degradation rate constant

## Compartments

- `CENT`: unbound drug in central compartment

- `TISS`: unbound drug in tissue compartment

- `REC`: concentration of target

- `RC`: concentration of drug-target complex

- `EV`, `EV2`: extravascular dosing compartments

## Output variables

- `CP`: unbound drug in the central compartment

- `TOTAL`: total concentration of target (complexed and uncomplexed)
