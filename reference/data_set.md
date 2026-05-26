# Select a data set for simulation

The input data set (`data_set`) is a data frame that specifies
observations, model events, and / or parameter values for a population
of individuals.

## Usage

``` r
data_set(x, data, ...)

# S4 method for class 'mrgmod,data.frame'
data_set(x, data, ...)

# S4 method for class 'mrgmod,ANY'
data_set(x, data, ...)

# S4 method for class 'mrgmod,ev'
data_set(x, data, ...)
```

## Arguments

- x:

  a model object.

- data:

  input data set as a data frame.

- ...:

  not used.

## Details

Input data sets are `R` data frames that can include columns with any
valid name, however columns with selected names are treated specially by
mrgsolve and incorporated into the simulation.

`ID` specifies the subject ID and is required for every input data set.

When columns have the same name as parameters (`$PARAM` or `$INPUT` in
the model specification file), the values in those columns will be used
to update the corresponding parameter as the simulation progresses.

Input data set may include the following columns related to PK dosing
events: `TIME`, `CMT`, `AMT`, `RATE`, `II`, `ADDL`, `SS`. Both `ID` and
`TIME` are required columns in the input data set unless `$PRED` is in
use. Lower case PK dosing column names including `time`, `cmt`, `amt`,
`rate`, `ii`, `addl`, `ss` are also recognized. However, an error will
be generated if a mix of both upper case and lower case columns in this
family are found. Use the functions
[`lctran()`](https://mrgsolve.org/docs/reference/lctran.md) and
[`uctran()`](https://mrgsolve.org/docs/reference/lctran.md) to convert
between upper and lower case naming for these data items.

`TIME` is the observation or event time, `CMT` is the compartment number
(see [`init()`](https://mrgsolve.org/docs/reference/init.md)), `AMT` is
the dosing amount, `RATE` is the infusion rate, `II` is the dosing
interval, `ADDL` specifies additional doses to administer, and `ss` is a
flag indicating that the system should be advanced to a pharmacokinetic
steady state prior to administering the dose. These column names operate
similarly to other non-linear mixed effects modeling software.

`EVID` is an integer value specifying the ID of an event record. Values
include:

- 0: observation

- 1: dose event, either bolus or infusion

- 2: other-type event; in mrgsolve, this functions like an observation
  record, but a discontinuity is created in the simulation at the time
  of the event (i.e., the ODE solver will stop and restart at the time
  of the event)

- 3: reset the system

- 4: reset the system and dose

- 8: replace the amount in a compartment

For all `EVID` greater than `0` and less than `100`, a discontinuity is
created in the simulation, as described for `EVID 2`.

An error will be generated when mrgsolve detects that the data set is
not sorted by `time` within an individual. mrgsolve does **not** allow
time to be reset to zero on records where `EVID` is set to 4 (reset and
dose).

Only numeric data can be brought in to the problem. Any non-numeric data
columns will be dropped with warning. See
[`numerics_only()`](https://mrgsolve.org/docs/reference/numerics_only.md),
which is used to prepare the data set.

An error will be generated if any parameter columns in the input data
set contain missing values (`NA`). Likewise, and error will be generated
if missing values are found in the following columns: `ID`,
`time`/`TIME`, `rate`/`RATE`.

See [exdatasets](https://mrgsolve.org/docs/reference/exdatasets.md) for
several example data sets that are provided by mrgsolve.

## See also

[`idata_set()`](https://mrgsolve.org/docs/reference/idata_set.md),
[`ev()`](https://mrgsolve.org/docs/reference/ev.md),
[`valid_data_set()`](https://mrgsolve.org/docs/reference/valid_data_set.md),
[`valid_idata_set()`](https://mrgsolve.org/docs/reference/valid_idata_set.md),
[`lctran()`](https://mrgsolve.org/docs/reference/lctran.md),
[`uctran()`](https://mrgsolve.org/docs/reference/lctran.md).

## Examples

``` r

mod <- house()

data <- expand.ev(ID = seq(3), amt = c(10, 20))

data(extran1)
head(extran1)
#>   ID  amt cmt time addl ii rate evid
#> 1  1 1000   1    0    3 24    0    1
#> 2  2 1000   2    0    0  0   20    1
#> 3  3 1000   1    0    0  0    0    1
#> 4  3  500   1   24    0  0    0    1
#> 5  3  500   1   48    0  0    0    1
#> 6  3 1000   1   72    0  0    0    1

mod %>% data_set(extran1) %>% mrgsim()
#> Model:  housemodel 
#> Dim:    2414 x 7 
#> Time:   0 to 120 
#> ID:     5 
#>     ID time    GUT  CENT  RESP    DV    CP
#> 1:   1 0.00    0.0   0.0 50.00  0.00  0.00
#> 2:   1 0.00 1000.0   0.0 50.00  0.00  0.00
#> 3:   1 0.25  740.8 257.5 42.29 12.87 12.87
#> 4:   1 0.50  548.8 445.0 32.69 22.25 22.25
#> 5:   1 0.75  406.6 580.8 25.29 29.04 29.04
#> 6:   1 1.00  301.2 678.3 20.05 33.91 33.91
#> 7:   1 1.25  223.1 747.4 16.45 37.37 37.37
#> 8:   1 1.50  165.3 795.6 14.01 39.78 39.78
mod %>% mrgsim(data = extran1)
#> Model:  housemodel 
#> Dim:    2414 x 7 
#> Time:   0 to 120 
#> ID:     5 
#>     ID time    GUT  CENT  RESP    DV    CP
#> 1:   1 0.00    0.0   0.0 50.00  0.00  0.00
#> 2:   1 0.00 1000.0   0.0 50.00  0.00  0.00
#> 3:   1 0.25  740.8 257.5 42.29 12.87 12.87
#> 4:   1 0.50  548.8 445.0 32.69 22.25 22.25
#> 5:   1 0.75  406.6 580.8 25.29 29.04 29.04
#> 6:   1 1.00  301.2 678.3 20.05 33.91 33.91
#> 7:   1 1.25  223.1 747.4 16.45 37.37 37.37
#> 8:   1 1.50  165.3 795.6 14.01 39.78 39.78
```
