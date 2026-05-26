# modlib: HCV viral dynamics models

modlib: HCV viral dynamics models

## Models

- `viral1`: viral dynamics model with single HCV species

- `viral2`: viral dynamics model with wild-type and mutant HCV species

## Parameters

- `s`: new hepatocyte synthesis rate (cells/ml/day)

- `d`: hepatocyte death rate constant (1/day)

- `p`: viral production rate constant (copies/cell/day)

- `beta`: new infection rate constant (ml/copy/day)

- `delta`: infected cell death rate constant (1/day)

- `c`: viral clearance rate constant (1/day)

- `fit`: mutant virus fitness

- `N`: non-target hepatocytes

- `mu`: forward mutation rate

- `Tmax`: maximum number of target hepatocytes (cells/ml)

- `rho`: maximum hepatocyte regeneration rate (1/day)

## Compartments

- `T`: uninfected target hepatocytes (cells/ml)

- `I`: productively infected hepatocytes (cells/ml)

- `V`: hepatitis C virus (copies/ml)

- `IM`: mutant infected hepatocytes (cells/ml)

- `VM`: mutant hepatitis C virus (copies/ml)

- `expos`: exposure metric to drive pharmacodynamic model
