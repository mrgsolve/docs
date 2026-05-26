# Import model estimates from a NONMEM ext file

Import model estimates from a NONMEM ext file

## Usage

``` r
nmext(
  run = NA_real_,
  project = getwd(),
  file = paste0(run, ".ext"),
  path = NULL,
  root = c("cppfile", "working"),
  index = "last",
  theta = TRUE,
  omega = TRUE,
  sigma = TRUE,
  olabels = NULL,
  slabels = NULL,
  oprefix = "",
  sprefix = "",
  tname = "THETA",
  oname = "...",
  sname = "...",
  read_fun = "data.table",
  env = NULL
)
```

## Arguments

- run:

  run number.

- project:

  project directory.

- file:

  deprecated; use `path` instead.

- path:

  full path to NONMEM `ext` file.

- root:

  the directory that `path` and `project` are relative to; this is
  currently limited to the `working` directory or `cppdir`, the
  directory where the model file is located.

- index:

  the estimation number to return; "last" will return the last
  estimation results; otherwise, pass an integer indicating which
  estimation results to return.

- theta:

  logical; if TRUE, the `$THETA` vector is returned.

- omega:

  logical; if TRUE, the `$OMEGA` matrix is returned.

- sigma:

  logical; if TRUE, the `$SIGMA` matrix is returned.

- olabels:

  labels for `$OMEGA`.

- slabels:

  labels for `$SIGMA`.

- oprefix:

  prefix for `$OMEGA` labels.

- sprefix:

  prefix for `$SIGMA` labels.

- tname:

  name for `$THETA`.

- oname:

  name for `$OMEGA`.

- sname:

  name for `$SIGMA`.

- read_fun:

  function to use when reading the `ext` file.

- env:

  internal use only.

## See also

[`nmxml()`](https://mrgsolve.org/docs/reference/nmxml.md),
[`read_nmext()`](https://mrgsolve.org/docs/reference/read_nmext.md)
