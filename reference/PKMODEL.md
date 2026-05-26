# Parse PKMODEL BLOCK data

Parse PKMODEL BLOCK data

## Usage

``` r
PKMODEL(
  ncmt = 1,
  depot = FALSE,
  cmt = NULL,
  advan = NULL,
  trans = NULL,
  env = list(),
  pos = 1,
  ...
)
```

## Arguments

- ncmt:

  number of compartments; must be 1 (one-compartment, not including a
  depot dosing compartment), 2 (two-compartment model, not including a
  depot dosing compartment), or 3 (three-compartment model, not
  including a depot dosing compartment).

- depot:

  logical indicating whether to add depot compartment.

- cmt:

  compartment names as comma-delimited character.

- advan:

  ADVAN subroutine number; can be 1, 2, 3, 4, 11, or 12; when specified,
  `ncmt` and `depot` are derived from the ADVAN number and the
  appropriate compartments are registered to the model unless specified
  elsewhere (see **Details**).

- trans:

  the parameterization for the PK model; must be 1, 2, 4, or 11.

- env:

  parse environment.

- pos:

  block position number.

- ...:

  not used.

## Details

When using `$PKMODEL`, certain symbols must be defined in the model
specification depending on the value of `ncmt`, `depot` and `trans`.

- `ncmt` 1, `depot FALSE`, trans 2: `CL`, `V`

- `ncmt` 1, `depot TRUE` , trans 2: `CL`, `V`, `KA`

- `ncmt` 2, `depot FALSE`, trans 4: `CL`, `V1`, `Q`, `V2`

- `ncmt` 2, `depot TRUE` , trans 4: `CL`, `V2`, `Q`, `V3`, `KA`

- `ncmt` 3, `depot FALSE`, trans 4: `CL`, `V1`, `Q2`, `V2`, `Q3`, `V3`

- `ncmt` 3, `depot TRUE` , trans 4: `CL`, `V2`, `Q3`, `V3`, `KA`, `Q4`,
  `V4`

If `trans=11` is specified, use the symbols listed above for the `ncmt`
/ `depot` combination, but append `i` at the end (e.g. `CLi` or `Q2i` or
`KAi`).

If `trans=1`, the user must utilize the following symbols:

- `pred_CL` for clearance

- `pred_V` or `pred_V2` for central compartment volume of distribution

- `pred_Q` for intercompartmental clearance

- `pred_V3` for peripheral compartment volume of distribution

- `pred_KA` for absorption rate constant

- `pred_Q2` for second intercompartmental clearance (3-cmt)

- `pred_VP2` or `pred_V4` for second peripheral compartment volume of
  distribution (3-cmt)

When `advan` is supplied by the user, default compartments are
registered in the model unless specified elsewhere. Compartment names
are `A1`, `A2`, etc. to the number of compartments for the specified
`advan`. These compartments will *not* be added in case (1) the model
contains a `$CMT` block (2) the model contains a `$INIT` block or (3) no
compartments have been registered in the model at the time `$PKMODEL` is
processed (for example, via `$YAML`).

## See also

[BLOCK_PARSE](https://mrgsolve.org/docs/reference/BLOCK_PARSE.md)

## Examples

``` r
if (FALSE) { # \dontrun{
code <- '
$PARAM CL = 1, V2 = 20, Q = 2, V3 = 10, KA = 1
$PKMODEL ncmt = 2, depot = TRUE, cmt = "GUT CENT PERIPH"
'
mod <- mcode("pk2-example", code)

code <- '
$PARAM CL = 1, V2 = 20, Q3 = 2, V3 = 10, Q4 = 0.5, V4 = 50, KA = 1
$PKMODEL advan = 12
'
mod <- mcode("advan12-example", code)
} # }
```
