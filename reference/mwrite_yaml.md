# Write model code to yaml format

Model code is written to a readable, transport format. This transport
format can be useful for (1) breaking connection to NONMEM modeling
outputs that are imported by `$NMXML` or `$NMEXT` and (2) saving model
updates (e.g., an updated parameter list). Models can be read back using
[`mread_yaml()`](https://mrgsolve.org/docs/reference/mread_yaml.md) or
converted to mrgsolve cpp format with
[`yaml_to_cpp()`](https://mrgsolve.org/docs/reference/mread_yaml.md).

## Usage

``` r
mwrite_yaml(x, file, digits = 8)
```

## Arguments

- x:

  a model object.

- file:

  output file name; if non-character (e.g., `NULL`), no output will be
  written to file.

- digits:

  precision to use when writing outputs.

## Value

A list containing data that was written out to the yaml file, with added
item `file`, is returned invisibly.

## Details

Parameters and omega and sigma matrices that were imported via `$NMXML`
or `$NMEXT` will be written into the yaml file and the NONMEM import
blocks will be dropped. This allows the user to load a model based on a
NONMEM run without having a connection to that output (e.g., `root.xml`
or `root.ext`). Given that the connection to the NONMEM modeling outputs
is broken when writing to yaml, any update to the NONMEM run will only
be propagated to the yaml file when `mwrite_yaml()` is run again.

The yaml file does not currently have the ability to track other
external dependencies, such as user-defined header files or other code
that might be sourced in by the user when the model is loaded via
[`mread()`](https://mrgsolve.org/docs/reference/mread.md). NONMEM xml
and ext files imported by `$NMXML` or `$NMEXT` are the *only* external
dependencies that are accounted for in the yaml transport file.

## See also

[`mread_yaml()`](https://mrgsolve.org/docs/reference/mread_yaml.md),
[`yaml_to_cpp()`](https://mrgsolve.org/docs/reference/mread_yaml.md)

## Examples

``` r
mod <- house()

temp1 <- tempfile(fileext = ".yaml")

x <- mwrite_yaml(mod, temp1)

readLines(temp1)
#>   [1] "source: mrgsolve::mwrite"                                                 
#>   [2] "mrgsolve: 2.0.1"                                                          
#>   [3] "format: yaml"                                                             
#>   [4] "version: 1.0"                                                             
#>   [5] "model: housemodel"                                                        
#>   [6] "prob:"                                                                    
#>   [7] "- '# `mrgsolve` housemodel'"                                              
#>   [8] "- This model is compiled with `mrgsolve`."                                
#>   [9] "- '  - Author: Metrum Research Group, LLC'"                               
#>  [10] "- '  - Description: Generic indirect response PK/PD model'"               
#>  [11] "- '  - Covariates: Weight, female sex'"                                   
#>  [12] "- '  - Random effects: CL, VC, KA, KOUT'"                                 
#>  [13] "- '  - Error model: exponential'"                                         
#>  [14] "- ''"                                                                     
#>  [15] "- '# Model Annotations: '"                                                
#>  [16] "- ''"                                                                     
#>  [17] "- 'block     name    descr                      unit     '"               
#>  [18] "- '--------  ------  -------------------------  ---------'"               
#>  [19] "- 'PARAM     CL      Clearance                  L/hr     '"               
#>  [20] "- 'PARAM     VC      Volume of distribution     L        '"               
#>  [21] "- 'PARAM     KA      Absorption rate constant   1/hr     '"               
#>  [22] "- 'PARAM     F1      Bioavailability fraction   .        '"               
#>  [23] "- 'PARAM     D1      Infusion duration          hr       '"               
#>  [24] "- 'PARAM     WTCL    Exponent WT on CL          .        '"               
#>  [25] "- 'PARAM     WTVC    Exponent WT on VC          .        '"               
#>  [26] "- 'PARAM     SEXCL   Prop cov effect on CL      .        '"               
#>  [27] "- 'PARAM     SEXVC   Prop cov effect on VC      .        '"               
#>  [28] "- 'PARAM     KIN     Resp prod rate constant    1/hr     '"               
#>  [29] "- 'PARAM     KOUT    Resp elim rate constant    1/hr     '"               
#>  [30] "- 'PARAM     IC50    Conc giving 50% max resp   ng/ml    '"               
#>  [31] "- 'PARAM     WT      Weight                     kg       '"               
#>  [32] "- 'PARAM     SEX     Covariate female sex       .        '"               
#>  [33] "- 'CMT       GUT     Dosing compartment         mg       '"               
#>  [34] "- 'CMT       CENT    Central compartment        mg       '"               
#>  [35] "- 'CMT       RESP    Response                   unitless '"               
#>  [36] "- 'CAPTURE   DV      Dependent variable         ng/ml    '"               
#>  [37] "- 'CAPTURE   CP      Plasma concentration       ng/ml    '"               
#>  [38] "param:"                                                                   
#>  [39] "  CL: 1.0"                                                                
#>  [40] "  VC: 20.0"                                                               
#>  [41] "  KA: 1.2"                                                                
#>  [42] "  F1: 1.0"                                                                
#>  [43] "  D1: 2.0"                                                                
#>  [44] "  WTCL: 0.75"                                                             
#>  [45] "  WTVC: 1.0"                                                              
#>  [46] "  SEXCL: 0.7"                                                             
#>  [47] "  SEXVC: 0.85"                                                            
#>  [48] "  KIN: 100.0"                                                             
#>  [49] "  KOUT: 2.0"                                                              
#>  [50] "  IC50: 10.0"                                                             
#>  [51] "  WT: 70.0"                                                               
#>  [52] "  SEX: 0.0"                                                               
#>  [53] "init:"                                                                    
#>  [54] "  GUT: 0.0"                                                               
#>  [55] "  CENT: 0.0"                                                              
#>  [56] "  RESP: 50.0"                                                             
#>  [57] "capture:"                                                                 
#>  [58] "- DV"                                                                     
#>  [59] "- CP"                                                                     
#>  [60] "omega:"                                                                   
#>  [61] "  data:"                                                                  
#>  [62] "    matrix1:"                                                             
#>  [63] "      row1: 0.0"                                                          
#>  [64] "      row2:"                                                              
#>  [65] "      - 0.0"                                                              
#>  [66] "      - 0.0"                                                              
#>  [67] "      row3:"                                                              
#>  [68] "      - 0.0"                                                              
#>  [69] "      - 0.0"                                                              
#>  [70] "      - 0.0"                                                              
#>  [71] "      row4:"                                                              
#>  [72] "      - 0.0"                                                              
#>  [73] "      - 0.0"                                                              
#>  [74] "      - 0.0"                                                              
#>  [75] "      - 0.0"                                                              
#>  [76] "  labels:"                                                                
#>  [77] "    matrix1:"                                                             
#>  [78] "    - ECL"                                                                
#>  [79] "    - EVC"                                                                
#>  [80] "    - EKA"                                                                
#>  [81] "    - EKOUT"                                                              
#>  [82] "  names: '...'"                                                           
#>  [83] "sigma:"                                                                   
#>  [84] "  data:"                                                                  
#>  [85] "    matrix1:"                                                             
#>  [86] "      row1: 0.0"                                                          
#>  [87] "  labels:"                                                                
#>  [88] "    matrix1: EXPO"                                                        
#>  [89] "  names: '...'"                                                           
#>  [90] "envir: []"                                                                
#>  [91] "plugin: base"                                                             
#>  [92] "update:"                                                                  
#>  [93] "  start: 0.0"                                                             
#>  [94] "  end: 120.0"                                                             
#>  [95] "  delta: 0.25"                                                            
#>  [96] "  add: []"                                                                
#>  [97] "  atol: 1.0e-08"                                                          
#>  [98] "  rtol: 1.0e-08"                                                          
#>  [99] "  ss_atol: 1.0e-08"                                                       
#> [100] "  ss_rtol: 1.0e-08"                                                       
#> [101] "  maxsteps: 20000.0"                                                      
#> [102] "  hmax: 0.0"                                                              
#> [103] "  hmin: 0.0"                                                              
#> [104] "  mxhnil: 2.0"                                                            
#> [105] "  ixpr: 0.0"                                                              
#> [106] "  mindt: 2.22044605e-15"                                                  
#> [107] "  digits: -1.0"                                                           
#> [108] "  tscale: 1.0"                                                            
#> [109] "  outvars:"                                                               
#> [110] "  - GUT"                                                                  
#> [111] "  - CENT"                                                                 
#> [112] "  - RESP"                                                                 
#> [113] "  - DV"                                                                   
#> [114] "  - CP"                                                                   
#> [115] "set:"                                                                     
#> [116] "  end: 120.0"                                                             
#> [117] "  delta: 0.25"                                                            
#> [118] "code:"                                                                    
#> [119] "- $PLUGIN"                                                                
#> [120] "- base"                                                                   
#> [121] "- ' '"                                                                    
#> [122] "- $GLOBAL"                                                                
#> [123] "- '#define CP (CENT/VCi)'"                                                
#> [124] "- '#define INH (CP/(IC50+CP))'"                                           
#> [125] "- typedef double localdouble;"                                            
#> [126] "- ' '"                                                                    
#> [127] "- $MAIN"                                                                  
#> [128] "- '@!check_modeled_infusions'"                                            
#> [129] "- F_GUT = F1;"                                                            
#> [130] "- D_CENT = D1;"                                                           
#> [131] "- double CLi   = exp(log(CL)   + WTCL*log(WT/70) + log(SEXCL)*SEX + ECL);"
#> [132] "- double VCi   = exp(log(VC)   + WTVC*log(WT/70) + log(SEXVC)*SEX + EVC);"
#> [133] "- double KAi   = exp(log(KA)   + EKA);"                                   
#> [134] "- double KOUTi = exp(log(KOUT) + EKOUT);"                                 
#> [135] "- RESP_0 = KIN/KOUTi;"                                                    
#> [136] "- ' '"                                                                    
#> [137] "- $ODE"                                                                   
#> [138] "- dxdt_GUT = -KAi*GUT;"                                                   
#> [139] "- dxdt_CENT = KAi*GUT - (CLi/VCi)*CENT;"                                  
#> [140] "- dxdt_RESP = KIN*(1-INH) - KOUTi*RESP;"                                  
#> [141] "- ' '"                                                                    
#> [142] "- $TABLE"                                                                 
#> [143] "- double DV = CP*exp(EXPO);"                                              
#> [144] "- ' '"                                                                    
```
