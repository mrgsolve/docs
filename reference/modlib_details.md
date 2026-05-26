# modlib: PK/PD Model parameters, compartments, and output variables

modlib: PK/PD Model parameters, compartments, and output variables

## Compartments

- `EV`, `EV2`: extravascular dosing compartments

- `CENT`: central PK compartment

- `PERIPH`: peripheral PK compartment

- `PERIPH2`: peripheral PK compartment 2

- `RESP`: response PD compartment (irm models)

## Output variables

- `CP`: concentration in the central compartment

- `RESP`: response (emax model)

## PK parameters

- `KA`, `KA2`: first order absorption rate constants from first and
  second extravascular compartment (1/time)

- `CL`: clearance (volume/time)

- `V`: volume of distribution (volume)

- `V2`: volume of distribution, central compartment (volume)

- `V3`: volume of distribution, peripheral compartment (volume)

- `V4`: volume of distribution, peripheral compartment 2 (volume)

- `Q`: intercompartmental clearance (volume/time)

- `Q3`: intercompartmental clearance (volume/time)

- `Q4`: intercompartmental clearance 2 (volume/time)

- `VMAX`: maximum rate, nonlinear process (mass/time)

- `KM`: Michaelis constant (mass/volume)

- `K10`: elimination rate constant (1/time)

- `K12`: rate constant for transfer to peripheral compartment from
  central (1/time)

- `K21`: rate constant for transfer to central compartment from
  peripheral (1/time)

## PD parameters

- `E0`: baseline effect (emax model)

- `EMAX`, `IMAX`: maximum effect (response)

- `EC50`, `IC50`: concentration producing 50 percent of effect
  (mass/volume)

- `KIN`: zero-order response production rate (irm models)
  (response/time)

- `KOUT`: first-order response elimination rate (irm models) (1/time)

- `n`: sigmoidicity factor

- `KEO`: rate constant for transfer to effect compartment (1/time)
