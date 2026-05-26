# Import model estimates from a NONMEM xml file

Import model estimates from a NONMEM xml file

## Usage

``` r
nmxml(
  run = numeric(0),
  project = character(0),
  file = character(0),
  path = character(0),
  root = c("cppfile", "working"),
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
  index = "last",
  xpath = ".//nm:estimation",
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

  the complete path to the `run.xml` file.

- root:

  the directory that `path` and `project` are relative to; this is
  currently limited to the `working` directory or `cppdir`, the
  directory where the model file is located.

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

- index:

  the estimation number to return; "last" will return the last
  estimation results; otherwise, pass an integer indicating which
  estimation results to return.

- xpath:

  xml path containing run results; if the default doesn't work, consider
  using `.//estimation` as an alternative; see details.

- env:

  internal use only.

## Value

A list with theta, omega and sigma elements, depending on what was
requested.

## Details

If `run` and `project` are supplied, the `.xml` file is assumed to be
located in `run.xml`, in directory `run` off the `project` directory. If
`file` is supplied, `run` and `project` arguments are ignored.

This function requires that the xml2 package be installed and loadable.
If [`requireNamespace("xml2")`](https://xml2.r-lib.org) fails, an error
will be generated.

`nmxml` usually expects to find run results in the xpath called
`.//nm:estimation`. Occasionally, the run results are not stored in this
namespace but no namespaces are found in the xml file. In this case, the
user can specify the xpath containing run results. Consider trying
`.//estimation` as an alternative if the default fails.

## See also

nmext

## Examples

``` r

if(requireNamespace("xml2")) {
  proj <- system.file("nonmem", package = "mrgsolve")
  mrgsolve:::nmxml(run = 1005, project = proj)
}
#> $theta
#> $theta$THETA1
#> [1] 9.507886
#> 
#> $theta$THETA2
#> [1] 22.79099
#> 
#> $theta$THETA3
#> [1] 0.07143366
#> 
#> $theta$THETA4
#> [1] 3.474506
#> 
#> $theta$THETA5
#> [1] 113.2767
#> 
#> $theta$THETA6
#> [1] 1.024354
#> 
#> $theta$THETA7
#> [1] 1.192118
#> 
#> 
#> $omega
#> $...
#>            [,1]        [,2]        [,3]
#> 1:   0.21387884  0.12077020 -0.01162777
#> 2:   0.12077020  0.09451047 -0.03720637
#> 3:  -0.01162777 -0.03720637  0.04656315
#> 
#> 
#> $sigma
#> $...
#>           [,1]      [,2]
#> 1:  0.04917071 0.0000000
#> 2:  0.00000000 0.2017688
#> 
#> 
#> $file
#> [1] "/private/var/folders/zv/v6tkdhrn1_bb1ndrc0c0j31w0000gp/T/Rtmp0CTHgW/temp_libpath161f33c47ec9b/mrgsolve/nonmem/1005/1005.xml"
#> 
#> attr(,"class")
#> [1] "NMXMLDATA"
```
