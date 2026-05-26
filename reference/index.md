# Package index

## All functions

- [`PARAM()`](https://mrgsolve.org/docs/reference/BLOCK_PARSE.md)
  [`FIXED()`](https://mrgsolve.org/docs/reference/BLOCK_PARSE.md)
  [`THETA()`](https://mrgsolve.org/docs/reference/BLOCK_PARSE.md)
  [`INIT()`](https://mrgsolve.org/docs/reference/BLOCK_PARSE.md)
  [`CMT()`](https://mrgsolve.org/docs/reference/BLOCK_PARSE.md)
  [`CAPTURE()`](https://mrgsolve.org/docs/reference/BLOCK_PARSE.md)
  [`HANDLEMATRIX()`](https://mrgsolve.org/docs/reference/BLOCK_PARSE.md)
  : Functions to parse code blocks
- [`PKMODEL()`](https://mrgsolve.org/docs/reference/PKMODEL.md) : Parse
  PKMODEL BLOCK data
- [`Req()`](https://mrgsolve.org/docs/reference/Req.md)
  [`req()`](https://mrgsolve.org/docs/reference/Req.md) : Request
  simulated output
- [`aboutsolver`](https://mrgsolve.org/docs/reference/aboutsolver.md) :
  About the lsoda differential equation solver used by mrgsolve
- [`as.ev()`](https://mrgsolve.org/docs/reference/as.ev.md) : Coerce an
  object to class ev
- [`as.list(`*`<mrgmod>`*`)`](https://mrgsolve.org/docs/reference/as.list-mrgmod-method.md)
  : Coerce a model object to list
- [`as.list(`*`<mrgsims>`*`)`](https://mrgsolve.org/docs/reference/as.list-mrgsims-method.md)
  : Coerce an mrgsims object to list
- [`as_data_set()`](https://mrgsolve.org/docs/reference/as_data_set.md)
  : Create a simulation data set from ev objects or data frames
- [`as_deslist()`](https://mrgsolve.org/docs/reference/as_deslist.md) :
  Create a list of designs from a data frame
- [`blocks()`](https://mrgsolve.org/docs/reference/blocks.md) : Return
  the code blocks from a model specification file
- [`carry_out()`](https://mrgsolve.org/docs/reference/carry_out.md)
  [`carry.out()`](https://mrgsolve.org/docs/reference/carry_out.md) :
  Select items to carry into simulated output
- [`check_data_names()`](https://mrgsolve.org/docs/reference/check_data_names.md)
  : Check input data set names against model parameters
- [`cmtn()`](https://mrgsolve.org/docs/reference/cmtn.md) : Get the
  compartment number from a compartment name
- [`code()`](https://mrgsolve.org/docs/reference/code.md) : Extract the
  code from a model
- [`collapse_omega()`](https://mrgsolve.org/docs/reference/collapse_matrices.md)
  [`collapse_sigma()`](https://mrgsolve.org/docs/reference/collapse_matrices.md)
  : Collapse OMEGA or SIGMA matrix lists
- [`collapse_matrix()`](https://mrgsolve.org/docs/reference/collapse_matrix.md)
  : Collapse the matrices of a matlist object
- [`custom_tol()`](https://mrgsolve.org/docs/reference/custom_tol.md)
  [`custom_rtol()`](https://mrgsolve.org/docs/reference/custom_tol.md)
  [`custom_atol()`](https://mrgsolve.org/docs/reference/custom_tol.md) :
  Customize tolerances for specific compartments
- [`data_set()`](https://mrgsolve.org/docs/reference/data_set.md) :
  Select a data set for simulation
- [`design()`](https://mrgsolve.org/docs/reference/design.md) : Set
  observation designs for the simulation
- [`details()`](https://mrgsolve.org/docs/reference/details.md) :
  Extract model details
- [`convert_pow()`](https://mrgsolve.org/docs/reference/dsl_preprocess.md)
  [`warn_int_div()`](https://mrgsolve.org/docs/reference/dsl_preprocess.md)
  [`convert_fort_if()`](https://mrgsolve.org/docs/reference/dsl_preprocess.md)
  [`convert_semicolons()`](https://mrgsolve.org/docs/reference/dsl_preprocess.md)
  : DSL preprocessing functions
- [`env_eval()`](https://mrgsolve.org/docs/reference/env_eval.md) :
  Re-evaluate the code in the ENV block
- [`env_get()`](https://mrgsolve.org/docs/reference/env_get.md)
  [`env_get_obj()`](https://mrgsolve.org/docs/reference/env_get.md)
  [`env_get_env()`](https://mrgsolve.org/docs/reference/env_get.md) :
  Return model environment or objects from the model environment
- [`env_ls()`](https://mrgsolve.org/docs/reference/env_ls.md) : List
  objects in the model environment
- [`env_update()`](https://mrgsolve.org/docs/reference/env_update.md) :
  Update objects in model environment
- [`ev()`](https://mrgsolve.org/docs/reference/ev.md) : Event objects
  for simulating PK and other interventions
- [`ev_assign()`](https://mrgsolve.org/docs/reference/ev_assign.md)
  [`assign_ev()`](https://mrgsolve.org/docs/reference/ev_assign.md) :
  Replicate a list of events into a data set
- [`ev_days()`](https://mrgsolve.org/docs/reference/ev_days.md) :
  Schedule dosing events on days of the week
- [`mutate(`*`<ev>`*`)`](https://mrgsolve.org/docs/reference/ev_dplyr.md)
  [`select(`*`<ev>`*`)`](https://mrgsolve.org/docs/reference/ev_dplyr.md)
  [`filter(`*`<ev>`*`)`](https://mrgsolve.org/docs/reference/ev_dplyr.md)
  : dplyr verbs for event objects
- [`` `$`( ``*`<ev>`*`)`](https://mrgsolve.org/docs/reference/ev_extract.md)
  [`` `[[`( ``*`<ev>`*`)`](https://mrgsolve.org/docs/reference/ev_extract.md)
  : Select columns from an ev object
- [`ev_rep()`](https://mrgsolve.org/docs/reference/ev_rep.md) :
  Replicate an event object
- [`ev_repeat()`](https://mrgsolve.org/docs/reference/ev_repeat.md) :
  Repeat a block of dosing events
- [`ev_rx()`](https://mrgsolve.org/docs/reference/ev_rx.md)
  [`parse_rx()`](https://mrgsolve.org/docs/reference/ev_rx.md) : Create
  intervention objects from Rx input
- [`ev_seq()`](https://mrgsolve.org/docs/reference/ev_seq.md)
  [`seq(`*`<ev>`*`)`](https://mrgsolve.org/docs/reference/ev_seq.md) :
  Schedule a series of event objects
- [`evd()`](https://mrgsolve.org/docs/reference/evd.md)
  [`as.evd()`](https://mrgsolve.org/docs/reference/evd.md) : Create an
  event object with data-like names
- [`exidata`](https://mrgsolve.org/docs/reference/exdatasets.md)
  [`extran1`](https://mrgsolve.org/docs/reference/exdatasets.md)
  [`extran2`](https://mrgsolve.org/docs/reference/exdatasets.md)
  [`extran3`](https://mrgsolve.org/docs/reference/exdatasets.md)
  [`exTheoph`](https://mrgsolve.org/docs/reference/exdatasets.md)
  [`exBoot`](https://mrgsolve.org/docs/reference/exdatasets.md) :
  Example input data sets
- [`expand.idata()`](https://mrgsolve.org/docs/reference/expand.idata.md)
  [`expand.ev()`](https://mrgsolve.org/docs/reference/expand.idata.md)
  [`expand.evd()`](https://mrgsolve.org/docs/reference/expand.idata.md)
  [`ev_expand()`](https://mrgsolve.org/docs/reference/expand.idata.md)
  [`evd_expand()`](https://mrgsolve.org/docs/reference/expand.idata.md)
  : Create template data sets for simulation
- [`expand_observations()`](https://mrgsolve.org/docs/reference/expand_observations.md)
  : Insert observations into a data set
- [`get_tol()`](https://mrgsolve.org/docs/reference/get_tol.md)
  [`get_tol_list()`](https://mrgsolve.org/docs/reference/get_tol.md) :
  Extract rtol and atol information from a model object
- [`idata_set()`](https://mrgsolve.org/docs/reference/idata_set.md) :
  Select a idata set for simulation
- [`init()`](https://mrgsolve.org/docs/reference/init.md) : Methods for
  working with the model compartment list
- [`inventory()`](https://mrgsolve.org/docs/reference/inventory.md) :
  Check whether all required parameters needed in a model are present in
  an object
- [`is.mrgmod()`](https://mrgsolve.org/docs/reference/is.mrgmod.md) :
  Check if an object is a model object
- [`is.mrgsims()`](https://mrgsolve.org/docs/reference/is.mrgsims.md) :
  Check if an object is mrgsims output
- [`knobs()`](https://mrgsolve.org/docs/reference/knobs.md) : DEFUNCT:
  Run sensitivity analysis on model settings
- [`lctran()`](https://mrgsolve.org/docs/reference/lctran.md)
  [`uctran()`](https://mrgsolve.org/docs/reference/lctran.md) : Change
  the case of nmtran-like data items
- [`loadso()`](https://mrgsolve.org/docs/reference/loadso.md) : Load the
  model shared object
- [`c(`*`<matlist>`*`)`](https://mrgsolve.org/docs/reference/matlist_ops.md)
  : Operations with matlist objects
- [`as_bmat()`](https://mrgsolve.org/docs/reference/matrix_converters.md)
  [`as_dmat()`](https://mrgsolve.org/docs/reference/matrix_converters.md)
  [`as_cmat()`](https://mrgsolve.org/docs/reference/matrix_converters.md)
  : Coerce R objects to block or diagonal matrices
- [`bmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md)
  [`cmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md)
  [`dmat()`](https://mrgsolve.org/docs/reference/matrix_helpers.md) :
  Create matrices from vector input
- [`mcRNG()`](https://mrgsolve.org/docs/reference/mcRNG.md) : Set RNG to
  use L'Ecuyer-CMRG
- [`mcode()`](https://mrgsolve.org/docs/reference/mcode.md)
  [`mcode_cache()`](https://mrgsolve.org/docs/reference/mcode.md) :
  Write, compile, and load model code
- [`modlib()`](https://mrgsolve.org/docs/reference/modlib.md) : Internal
  model library
- [`modlib_details`](https://mrgsolve.org/docs/reference/modlib_details.md)
  : modlib: PK/PD Model parameters, compartments, and output variables
- [`modlib_pk`](https://mrgsolve.org/docs/reference/modlib_pk.md) :
  modlib: Pharmacokinetic models
- [`modlib_pkpd`](https://mrgsolve.org/docs/reference/modlib_pkpd.md) :
  modlib: Pharmacokinetic / pharmacodynamic models
- [`modlib_tmdd`](https://mrgsolve.org/docs/reference/modlib_tmdd.md) :
  modlib: Target mediated disposition model
- [`modlib_viral`](https://mrgsolve.org/docs/reference/modlib_viral.md)
  : modlib: HCV viral dynamics models
- [`mread()`](https://mrgsolve.org/docs/reference/mread.md)
  [`mread_cache()`](https://mrgsolve.org/docs/reference/mread.md)
  [`mread_file()`](https://mrgsolve.org/docs/reference/mread.md) : Read
  a model specification file
- [`mread_yaml()`](https://mrgsolve.org/docs/reference/mread_yaml.md)
  [`yaml_to_cpp()`](https://mrgsolve.org/docs/reference/mread_yaml.md) :
  Read a model from yaml format
- [`` `$`( ``*`<mrgmod>`*`)`](https://mrgsolve.org/docs/reference/mrgmod_extract.md)
  [`` `[[`( ``*`<mrgmod>`*`)`](https://mrgsolve.org/docs/reference/mrgmod_extract.md)
  [`` `[`( ``*`<mrgmod>`*`)`](https://mrgsolve.org/docs/reference/mrgmod_extract.md)
  : Select parameter values from a model object
- [`mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md)
  [`mrgsim_df()`](https://mrgsolve.org/docs/reference/mrgsim.md)
  [`do_mrgsim()`](https://mrgsolve.org/docs/reference/mrgsim.md) :
  Simulate from a model object
- [`mrgsim_q()`](https://mrgsolve.org/docs/reference/mrgsim_q.md) :
  Simulate from a model object with quicker turnaround
- [`mrgsim_e()`](https://mrgsolve.org/docs/reference/mrgsim_variants.md)
  [`mrgsim_d()`](https://mrgsolve.org/docs/reference/mrgsim_variants.md)
  [`mrgsim_ei()`](https://mrgsolve.org/docs/reference/mrgsim_variants.md)
  [`mrgsim_di()`](https://mrgsolve.org/docs/reference/mrgsim_variants.md)
  [`mrgsim_i()`](https://mrgsolve.org/docs/reference/mrgsim_variants.md)
  [`mrgsim_0()`](https://mrgsolve.org/docs/reference/mrgsim_variants.md)
  : mrgsim variant functions
- [`pull(`*`<mrgsims>`*`)`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`filter(`*`<mrgsims>`*`)`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`group_by(`*`<mrgsims>`*`)`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`distinct(`*`<mrgsims>`*`)`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`mutate(`*`<mrgsims>`*`)`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`summarise(`*`<each>`*`)`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`summarise(`*`<mrgsims>`*`)`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`do(`*`<mrgsims>`*`)`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`select(`*`<mrgsims>`*`)`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`slice(`*`<mrgsims>`*`)`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`as_data_frame.mrgsims()`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`as_tibble(`*`<mrgsims>`*`)`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  [`as.tbl.mrgsims()`](https://mrgsolve.org/docs/reference/mrgsims_dplyr.md)
  : Methods for handling output with dplyr verbs
- [`mutate_sims()`](https://mrgsolve.org/docs/reference/mrgsims_modify.md)
  [`select_sims()`](https://mrgsolve.org/docs/reference/mrgsims_modify.md)
  [`filter_sims()`](https://mrgsolve.org/docs/reference/mrgsims_modify.md)
  : Methods for modifying mrgsims objects
- [`mrgsolve`](https://mrgsolve.org/docs/reference/mrgsolve_package.md)
  [`mrgsolve-package`](https://mrgsolve.org/docs/reference/mrgsolve_package.md)
  : mrgsolve: Simulate from ODE-Based Models
- [`mwrite_cpp()`](https://mrgsolve.org/docs/reference/mwrite_cpp.md) :
  Write a model to native mrgsolve format
- [`mwrite_yaml()`](https://mrgsolve.org/docs/reference/mwrite_yaml.md)
  : Write model code to yaml format
- [`names(`*`<mrgmod>`*`)`](https://mrgsolve.org/docs/reference/names-mrgmod-method.md)
  : Get all names from a model object
- [`nmext()`](https://mrgsolve.org/docs/reference/nmext.md) : Import
  model estimates from a NONMEM ext file
- [`nmxml()`](https://mrgsolve.org/docs/reference/nmxml.md) : Import
  model estimates from a NONMEM xml file
- [`numerics_only()`](https://mrgsolve.org/docs/reference/numerics_only.md)
  : Prepare data.frame for input to mrgsim()
- [`obsaug()`](https://mrgsolve.org/docs/reference/obsaug.md) : Augment
  observations in the simulated output
- [`obsonly()`](https://mrgsolve.org/docs/reference/obsonly.md) :
  Collect only observation records in the simulated output
- [`omat()`](https://mrgsolve.org/docs/reference/omega.md) : Manipulate
  OMEGA matrices
- [`outvars()`](https://mrgsolve.org/docs/reference/outvars.md) : Show
  names of current output variables
- [`param()`](https://mrgsolve.org/docs/reference/param.md)
  [`allparam()`](https://mrgsolve.org/docs/reference/param.md) : Create
  and work with parameter objects
- [`param_tags()`](https://mrgsolve.org/docs/reference/param_tags.md) :
  Return parameter tags
- [`plot(`*`<mrgsims>`*`,`*`<missing>`*`)`](https://mrgsolve.org/docs/reference/plot_mrgsims.md)
  [`plot(`*`<mrgsims>`*`,`*`<formula>`*`)`](https://mrgsolve.org/docs/reference/plot_mrgsims.md)
  [`plot(`*`<mrgsims>`*`,`*`<character>`*`)`](https://mrgsolve.org/docs/reference/plot_mrgsims.md)
  : Generate a quick plot of simulated data
- [`plot_sims()`](https://mrgsolve.org/docs/reference/plot_sims.md) :
  Plot data as an mrgsims object
- [`qsim()`](https://mrgsolve.org/docs/reference/qsim.md) : Basic,
  simple simulation from model object
- [`read_nmext()`](https://mrgsolve.org/docs/reference/read_nmext.md) :
  Extract estimates from NONMEM ext file
- [`realize_addl()`](https://mrgsolve.org/docs/reference/realize_addl.md)
  : Make addl doses explicit in an event object or data set
- [`reserved()`](https://mrgsolve.org/docs/reference/reserved.md) :
  Reserved words
- [`reset_tol()`](https://mrgsolve.org/docs/reference/reset_tol.md)
  [`reset_rtol()`](https://mrgsolve.org/docs/reference/reset_tol.md)
  [`reset_atol()`](https://mrgsolve.org/docs/reference/reset_tol.md) :
  Reset all model tolerances
- [`revar()`](https://mrgsolve.org/docs/reference/revar.md) : Get model
  random effect variances and covariances
- [`see()`](https://mrgsolve.org/docs/reference/see.md) : Print model
  code to the console
- [`smat()`](https://mrgsolve.org/docs/reference/sigma.md) : Manipulate
  SIGMA matrices
- [`simargs()`](https://mrgsolve.org/docs/reference/simargs.md) : Access
  or clear arguments for calls to mrgsim()
- [`soloc()`](https://mrgsolve.org/docs/reference/soloc.md) : Return the
  location of the model shared object
- [`solversettings`](https://mrgsolve.org/docs/reference/solversettings.md)
  : Optional inputs for lsoda
- [`summary(`*`<mrgmod>`*`)`](https://mrgsolve.org/docs/reference/summary.mrgmod.md)
  : Print summary of a mrgmod object
- [`c(`*`<tgrid>`*`)`](https://mrgsolve.org/docs/reference/tgrid_ops.md)
  [`c(`*`<tgrids>`*`)`](https://mrgsolve.org/docs/reference/tgrid_ops.md)
  [`` `+`( ``*`<tgrid>`*`,`*`<numeric>`*`)`](https://mrgsolve.org/docs/reference/tgrid_ops.md)
  [`` `*`( ``*`<tgrid>`*`,`*`<numeric>`*`)`](https://mrgsolve.org/docs/reference/tgrid_ops.md)
  [`` `+`( ``*`<tgrids>`*`,`*`<numeric>`*`)`](https://mrgsolve.org/docs/reference/tgrid_ops.md)
  [`` `*`( ``*`<tgrids>`*`,`*`<numeric>`*`)`](https://mrgsolve.org/docs/reference/tgrid_ops.md)
  : Operations with tgrid objects
- [`tscale()`](https://mrgsolve.org/docs/reference/tscale.md) : Re-scale
  time in the simulated output
- [`update(`*`<mrgmod>`*`)`](https://mrgsolve.org/docs/reference/update.md)
  [`update(`*`<omegalist>`*`)`](https://mrgsolve.org/docs/reference/update.md)
  [`update(`*`<sigmalist>`*`)`](https://mrgsolve.org/docs/reference/update.md)
  [`update(`*`<parameter_list>`*`)`](https://mrgsolve.org/docs/reference/update.md)
  : Update the model object
- [`use_custom_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md)
  [`use_scalar_tol()`](https://mrgsolve.org/docs/reference/use_custom_tol.md)
  : Set up a model object to use either scalar or custom tolerances
- [`valid_data_set()`](https://mrgsolve.org/docs/reference/valid_data_set.md)
  [`valid_data_set.matrix()`](https://mrgsolve.org/docs/reference/valid_data_set.md)
  : Validate and prepare data sets for simulation
- [`valid_idata_set()`](https://mrgsolve.org/docs/reference/valid_idata_set.md)
  : Validate and prepare idata data sets for simulation
- [`within(`*`<mrgmod>`*`)`](https://mrgsolve.org/docs/reference/within.md)
  : Update parameters, initials, and settings within a model object
- [`zero_re()`](https://mrgsolve.org/docs/reference/zero_re.md) : Zero
  out random effects in a model object
