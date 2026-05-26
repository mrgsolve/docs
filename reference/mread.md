# Read a model specification file

`mread()` reads and parses the mrgsolve model specification file, builds
the model, and returns a model object for simulation. `mread_cache()`
does the same, but caches the compilation result for later use.
`mread_file()` can be used for convenience, taking the model file name
as the first argument.

## Usage

``` r
mread(
  model,
  project = getOption("mrgsolve.project", getwd()),
  code = NULL,
  file = NULL,
  udll = TRUE,
  ignore.stdout = TRUE,
  raw = FALSE,
  compile = TRUE,
  audit = TRUE,
  quiet = getOption("mrgsolve_mread_quiet", FALSE),
  check.bounds = FALSE,
  warn = TRUE,
  soloc = getOption("mrgsolve.soloc", tempdir()),
  capture = NULL,
  preclean = FALSE,
  recover = FALSE,
  ...
)

mread_cache(
  model = NULL,
  project = getOption("mrgsolve.project", getwd()),
  file = paste0(model, ".cpp"),
  code = NULL,
  soloc = getOption("mrgsolve.soloc", tempdir()),
  quiet = FALSE,
  preclean = FALSE,
  capture = NULL,
  ...
)

mread_file(file, ...)
```

## Arguments

- model:

  model name.

- project:

  location of the model specification file an any headers to be
  included; see also the discussion about model; this argument can be
  set via [`options()`](https://rdrr.io/r/base/options.html). library
  under details as well as the
  [`modlib()`](https://mrgsolve.org/docs/reference/modlib.md) help
  topic.

- code:

  a character string with model specification code to be used instead of
  a model file.

- file:

  the full file name (with extension, but without path) where the model
  is specified.

- udll:

  use unique name for shared object.

- ignore.stdout:

  passed to system call when compiling the model; set this to `FALSE` to
  print output to the R console.

- raw:

  if `TRUE`, return model content as a list, bypassing the compile step;
  this argument is typically used for debugging problems with the model
  build.

- compile:

  logical; if `TRUE`, the model will be built.

- audit:

  check the model specification file for errors.

- quiet:

  don't print messages from mrgsolve when compiling.

- check.bounds:

  check boundaries of parameter list.

- warn:

  logical; if `TRUE`, print warning messages that may arise while
  building the model.

- soloc:

  the directory location where the model shared object is built and
  stored; see details; this argument can be set via
  [`options()`](https://rdrr.io/r/base/options.html); if the directory
  does not exist, `mread()` will attempt to create it.

- capture:

  a character vector or comma-separated string of additional model
  variables to capture; these variables will be added to the capture
  list for the current call to `mread()` only.

- preclean:

  logical; if `TRUE`, compilation artifacts are cleaned up first.

- recover:

  if `TRUE`, a list of build will be returned in case the model shared
  object fails to compile; use this option to and the returned object to
  collect information assist in debugging.

- ...:

  passed to [`update()`](https://mrgsolve.org/docs/reference/update.md);
  also arguments passed to `mread()` from `mread_cache()`.

## Details

The `model` argument is required. For typical use, the `file` argument
is omitted and the value for `file` is generated from the value for
`model`. To determine the source file name, mrgsolve will look for a
file extension in `model`. A file extension is assumed when it finds a
period followed by one to three alpha-numeric characters at the end of
the string (e.g. `mymodel.txt` but not `my.model`). If no file extension
is found, the extension `.cpp` is assumed (e.g. `file` is
`<model-name>.cpp`). If a file extension is found, `file` is
`<model-name>`.

Best practice is to avoid using `.` in `model` unless you are using
`model` to point to the model specification file name. Otherwise, use
`mread_file()`.

Use the `soloc` argument to specify a directory location for building
the model. This is the location where the model shared object will be
stored on disk. The default is a temporary directory, so compilation
artifacts are lost when R restarts when the default is used. Changing
`soloc` to a persistent directory location will preserve those artifacts
across R restarts. Also, if simulation from a single model is being done
in separate processes on separate compute nodes, it might be necessary
to store these compilation artifacts in a local directory to make them
accessible to the different nodes. If the `soloc` directory does not
exist, `mread()` will attempt to create it.

Similarly, using `mread_cache()` will cache results in the temporary
directory and the cache cannot be accessed after the R process is
restarted.

## Model Library

mrgsolve comes bundled with several pre-coded PK, PK/PD, and other
systems models that are accessible via the `mread()` interface.

Models available in the library include:

- PK models: `pk1cmt`, `pk2cmt`, `pk3cmt`, `pk1`, `pk2`, `popex`, `tmdd`

- PKPD models: `irm1`, `irm2`, `irm3`, `irm4`, `emax`, `effect`

- Other models: `viral1`, `viral2`

When the library model is accessed, mrgsolve will compile and load the
model as you would for any other model. It is only necessary to
reference the correct model name and point the `project` argument to the
mrgsolve model library location via
[`modlib()`](https://mrgsolve.org/docs/reference/modlib.md).

For more details, see
[modlib_pk](https://mrgsolve.org/docs/reference/modlib_pk.md),
[modlib_pkpd](https://mrgsolve.org/docs/reference/modlib_pkpd.md),
[modlib_tmdd](https://mrgsolve.org/docs/reference/modlib_tmdd.md),
[modlib_viral](https://mrgsolve.org/docs/reference/modlib_viral.md), and
[modlib_details](https://mrgsolve.org/docs/reference/modlib_details.md)
for more information about the state variables and parameters in each
model.

## See also

[`mcode()`](https://mrgsolve.org/docs/reference/mcode.md),
[`mcode_cache()`](https://mrgsolve.org/docs/reference/mcode.md)

## Examples

``` r

if (FALSE) { # \dontrun{
code <- '
$PARAM CL = 1, VC = 5
$CMT CENT
$ODE dxdt_CENT = -(CL/VC)*CENT;
'

mod <- mcode("ex_mread", code)
mod

mod %>% init(CENT=1000) %>% mrgsim() %>% plot()

mod <- mread("irm3", modlib())

# if the model is in the file mymodel.cpp
mod <- mread("mymodel")

# if the model is in the file mymodel.txt
mod <- mread(file = "mymodel.txt")

or

mod <- mread_file("mymodel.txt")
} # }
```
