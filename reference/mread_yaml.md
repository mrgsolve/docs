# Read a model from yaml format

Read back models written to file using
[`mwrite_yaml()`](https://mrgsolve.org/docs/reference/mwrite_yaml.md).
Function `yaml_to_cpp()` is also provided to convert the yaml file to
mrgsolve cpp file format.

## Usage

``` r
mread_yaml(
  file,
  model = basename(file),
  project = tempdir(),
  update = FALSE,
  ...
)

yaml_to_cpp(file, model = basename(file), project = getwd(), update = TRUE)
```

## Arguments

- file:

  the yaml file name.

- model:

  a new model name to use when calling `mread_yaml()`.

- project:

  the directory where the model should be built.

- update:

  `TRUE` if model settings should be written into the cpp file in a
  `$SET` block.

- ...:

  passed to [`mread()`](https://mrgsolve.org/docs/reference/mread.md).

## Value

A model object.

## Details

Note that `yaml_to_cpp()` by default writes model settings into the cpp
file. `mread_yaml()` does not write model settings into the file but
rather update the model object directly with data read back from the
`yaml` file.

## See also

[`mwrite_yaml()`](https://mrgsolve.org/docs/reference/mwrite_yaml.md)

## Examples

``` r
mod <- house()

temp <- tempfile(fileext = ".yaml")

mwrite_yaml(mod, file = temp)

# Note: this model is not compiled
mod <- mread_yaml(temp, model = "new-house", compile = FALSE)
mod
#> 
#> 
#> --------------  source: new-house.mod  --------------
#> 
#>   project: /private/var/fol.../T/RtmpwTsssJ
#>   shared object: new-house.mod-so-1623f3a83b85e <not loaded>
#> 
#>   time:          start: 0 end: 120 delta: 0.25
#>                  add: <none>
#>   compartments:  GUT CENT RESP [3]
#>   parameters:    CL VC KA F1 D1 WTCL WTVC SEXCL SEXVC
#>                  KIN KOUT IC50 WT SEX [14]
#>   captures:      DV CP [2]
#>   omega:         4x4 
#>   sigma:         1x1 
#> 
#>   solver:        rtol: 1e-08 atol: 1e-08 itol: 1 (scalar)
#> ------------------------------------------------------

cppfile <- yaml_to_cpp(temp, project = tempdir())

readLines(cppfile)
#>   [1] "$PROB"                                                                  
#>   [2] "# `mrgsolve` housemodel"                                                
#>   [3] "This model is compiled with `mrgsolve`."                                
#>   [4] "  - Author: Metrum Research Group, LLC"                                 
#>   [5] "  - Description: Generic indirect response PK/PD model"                 
#>   [6] "  - Covariates: Weight, female sex"                                     
#>   [7] "  - Random effects: CL, VC, KA, KOUT"                                   
#>   [8] "  - Error model: exponential"                                           
#>   [9] ""                                                                       
#>  [10] "# Model Annotations: "                                                  
#>  [11] ""                                                                       
#>  [12] "block     name    descr                      unit     "                 
#>  [13] "--------  ------  -------------------------  ---------"                 
#>  [14] "PARAM     CL      Clearance                  L/hr     "                 
#>  [15] "PARAM     VC      Volume of distribution     L        "                 
#>  [16] "PARAM     KA      Absorption rate constant   1/hr     "                 
#>  [17] "PARAM     F1      Bioavailability fraction   .        "                 
#>  [18] "PARAM     D1      Infusion duration          hr       "                 
#>  [19] "PARAM     WTCL    Exponent WT on CL          .        "                 
#>  [20] "PARAM     WTVC    Exponent WT on VC          .        "                 
#>  [21] "PARAM     SEXCL   Prop cov effect on CL      .        "                 
#>  [22] "PARAM     SEXVC   Prop cov effect on VC      .        "                 
#>  [23] "PARAM     KIN     Resp prod rate constant    1/hr     "                 
#>  [24] "PARAM     KOUT    Resp elim rate constant    1/hr     "                 
#>  [25] "PARAM     IC50    Conc giving 50% max resp   ng/ml    "                 
#>  [26] "PARAM     WT      Weight                     kg       "                 
#>  [27] "PARAM     SEX     Covariate female sex       .        "                 
#>  [28] "CMT       GUT     Dosing compartment         mg       "                 
#>  [29] "CMT       CENT    Central compartment        mg       "                 
#>  [30] "CMT       RESP    Response                   unitless "                 
#>  [31] "CAPTURE   DV      Dependent variable         ng/ml    "                 
#>  [32] "CAPTURE   CP      Plasma concentration       ng/ml    "                 
#>  [33] ""                                                                       
#>  [34] "$PARAM"                                                                 
#>  [35] "CL = 1"                                                                 
#>  [36] "VC = 20"                                                                
#>  [37] "KA = 1.2"                                                               
#>  [38] "F1 = 1"                                                                 
#>  [39] "D1 = 2"                                                                 
#>  [40] "WTCL = 0.75"                                                            
#>  [41] "WTVC = 1"                                                               
#>  [42] "SEXCL = 0.7"                                                            
#>  [43] "SEXVC = 0.85"                                                           
#>  [44] "KIN = 100"                                                              
#>  [45] "KOUT = 2"                                                               
#>  [46] "IC50 = 10"                                                              
#>  [47] "WT = 70"                                                                
#>  [48] "SEX = 0"                                                                
#>  [49] ""                                                                       
#>  [50] "$INIT"                                                                  
#>  [51] "GUT = 0"                                                                
#>  [52] "CENT = 0"                                                               
#>  [53] "RESP = 50"                                                              
#>  [54] ""                                                                       
#>  [55] "$OMEGA"                                                                 
#>  [56] "@block"                                                                 
#>  [57] "@labels ECL EVC EKA EKOUT"                                              
#>  [58] "// row 1"                                                               
#>  [59] "0"                                                                      
#>  [60] "// row 2"                                                               
#>  [61] "0"                                                                      
#>  [62] "0"                                                                      
#>  [63] "// row 3"                                                               
#>  [64] "0"                                                                      
#>  [65] "0"                                                                      
#>  [66] "0"                                                                      
#>  [67] "// row 4"                                                               
#>  [68] "0"                                                                      
#>  [69] "0"                                                                      
#>  [70] "0"                                                                      
#>  [71] "0"                                                                      
#>  [72] ""                                                                       
#>  [73] "$SIGMA"                                                                 
#>  [74] "@block"                                                                 
#>  [75] "@labels EXPO"                                                           
#>  [76] "// row 1"                                                               
#>  [77] "0"                                                                      
#>  [78] ""                                                                       
#>  [79] "$PLUGIN"                                                                
#>  [80] "base"                                                                   
#>  [81] " "                                                                      
#>  [82] "$GLOBAL"                                                                
#>  [83] "#define CP (CENT/VCi)"                                                  
#>  [84] "#define INH (CP/(IC50+CP))"                                             
#>  [85] "typedef double localdouble;"                                            
#>  [86] " "                                                                      
#>  [87] "$MAIN"                                                                  
#>  [88] "@!check_modeled_infusions"                                              
#>  [89] "F_GUT = F1;"                                                            
#>  [90] "D_CENT = D1;"                                                           
#>  [91] "double CLi   = exp(log(CL)   + WTCL*log(WT/70) + log(SEXCL)*SEX + ECL);"
#>  [92] "double VCi   = exp(log(VC)   + WTVC*log(WT/70) + log(SEXVC)*SEX + EVC);"
#>  [93] "double KAi   = exp(log(KA)   + EKA);"                                   
#>  [94] "double KOUTi = exp(log(KOUT) + EKOUT);"                                 
#>  [95] "RESP_0 = KIN/KOUTi;"                                                    
#>  [96] " "                                                                      
#>  [97] "$ODE"                                                                   
#>  [98] "dxdt_GUT = -KAi*GUT;"                                                   
#>  [99] "dxdt_CENT = KAi*GUT - (CLi/VCi)*CENT;"                                  
#> [100] "dxdt_RESP = KIN*(1-INH) - KOUTi*RESP;"                                  
#> [101] " "                                                                      
#> [102] "$TABLE"                                                                 
#> [103] "double DV = CP*exp(EXPO);"                                              
#> [104] " "                                                                      
#> [105] "$CAPTURE"                                                               
#> [106] "DV"                                                                     
#> [107] "CP"                                                                     
#> [108] ""                                                                       
#> [109] "$SET"                                                                   
#> [110] "end = 120"                                                              
#> [111] "delta = 0.25"                                                           
#> [112] " "                                                                      
#> [113] "start = 0"                                                              
#> [114] "end = 120"                                                              
#> [115] "delta = 0.25"                                                           
#> [116] "add = numeric(0)"                                                       
#> [117] "atol = 1e-08"                                                           
#> [118] "rtol = 1e-08"                                                           
#> [119] "ss_atol = 1e-08"                                                        
#> [120] "ss_rtol = 1e-08"                                                        
#> [121] "maxsteps = 20000"                                                       
#> [122] "hmax = 0"                                                               
#> [123] "hmin = 0"                                                               
#> [124] "mxhnil = 2"                                                             
#> [125] "ixpr = 0"                                                               
#> [126] "mindt = 2.22044605e-15"                                                 
#> [127] "digits = -1"                                                            
#> [128] "tscale = 1"                                                             
#> [129] "outvars = c(\"GUT\", \"CENT\", \"RESP\", \"DV\", \"CP\")"               
#> [130] ""                                                                       
```
