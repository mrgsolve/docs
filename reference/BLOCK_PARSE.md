# Functions to parse code blocks

Most of the basic blocks are listed in this help topic. But see also
[`PKMODEL()`](https://mrgsolve.org/docs/reference/PKMODEL.md) which has
more-involved options and is documented separately.

## Usage

``` r
PARAM(
  x,
  env,
  pos = 1,
  annotated = FALSE,
  object = NULL,
  as_object = FALSE,
  covariates = FALSE,
  input = FALSE,
  tag = NULL,
  ...
)

FIXED(x, env, pos = 1, annotated = FALSE, ...)

THETA(
  x,
  env,
  pos = 1,
  annotated = FALSE,
  object = NULL,
  as_object = FALSE,
  name = "THETA",
  fill = NULL,
  ...
)

INIT(x, env, pos = 1, annotated = FALSE, object = NULL, as_object = FALSE, ...)

CMT(
  x,
  env,
  pos = 1,
  annotated = FALSE,
  object = NULL,
  as_object = FALSE,
  number = NULL,
  prefix = "A",
  ...
)

CAPTURE(x, env, pos = 1, annotated = FALSE, etas = NULL, ...)

HANDLEMATRIX(
  x,
  env,
  pos = 1,
  annotated = FALSE,
  object = NULL,
  as_object = FALSE,
  name = "...",
  type = NULL,
  oclass = "",
  prefix = "",
  labels = NULL,
  unlinked = FALSE,
  ...
)
```

## Arguments

- x:

  data

- env:

  parse environment

- pos:

  block position

- annotated:

  logical

- object:

  the name of an object in `ENV`

- as_object:

  indicates that object code is being provided

- covariates:

  logical; mark as covariates and potentially required data input

- input:

  logical; mark as potentially required data input

- tag:

  space or comma-separated user-defined tags for the parameter block

- ...:

  passed

- name:

  block name

- fill:

  deprecated; not used

- number:

  number of compartments to create

- prefix:

  a prefix to add to the label

- etas:

  allows for block capture of ETAs in the simulated output; this should
  be R code that will get parsed and evaluated; the result should be an
  integer-like vector which identifies which ETAs will be captured.

- type:

  internal use

- oclass:

  internal use

- labels:

  aliases to use for simulated ETA values

- unlinked:

  internal use

## Details

When using `object` or `as_object` populate the block contents, the
following types are required

- `PARAM`: a named list

- `INIT` : a named list

- `THETA` : a numeric vector; names are ignored

- `CMT`: a character vector

- `OMEGA`: matrix; set rownames on the matrix to create ETA labels;
  setting rownames is the only way to specify `labels` when working
  through the `object` or `as_object` directives

- `SIGMA`: matrix; set rownames on the matrix to create EPS labels;
  setting rownames is the only way to specify `labels` when working
  through the `object` or `as_object` directives

## See also

[`PKMODEL()`](https://mrgsolve.org/docs/reference/PKMODEL.md)
