# Time after dose

## Introduction

`TAD` stands for time after dose. In mrgsolve, any time `TAD` is
calculated automatically, a dose is a record in the input data set where
`EVID` is set to either 1 or 4.

## TAD calculated as runtime argument

For a while, you’ve been able to get time after dose in your simulated
output

``` r

library(mrgsolve)
library(dplyr)

mod <- modlib("pk1", req = "")

mod %>% 
  ev(amt = 100, ii = 4, addl = 3, time = 2) %>%
  mrgsim(tad = TRUE, add = c(3.888,5.91)) %>% 
  as_tibble() %>% 
  head(n = 10)
```

    ## # A tibble: 10 × 4
    ##       ID  time   tad    CP
    ##    <dbl> <dbl> <dbl> <dbl>
    ##  1     1  0    -2     0   
    ##  2     1  1    -1     0   
    ##  3     1  2     0     0   
    ##  4     1  2     0     0   
    ##  5     1  3     1     3.07
    ##  6     1  3.89  1.89  3.99
    ##  7     1  4     2     4.05
    ##  8     1  5     3     4.27
    ##  9     1  5.91  3.91  4.22
    ## 10     1  6     0     4.21

This is convenient because you can choose the output at run time, we
give you the negative numbers prior to the first dose etc. This sort of
calculation is possible because we let mrgsolve know ahead of time that
we want this calculation done and mrgsolve makes an extra pass through
the records to find when is the first dose for each individual.

## TAD calculated in the model

Sometimes you would like to work with time after dose in your model.
This isn’t super-complicated to do but does require some programming and
setup and all of that. As of mrgsolve 0.9.1, there is a special function
to do these calculations for you.

``` r

mod <- mread("time-after-dose.txt",req = "")
```

Looking at the `[MAIN]` block:

``` c
```

When you call `self.tad()` you will get the time after dose. It’s
important that this gets called on every record … specifically every
dosing record. It will not work properly if it is not called every
record and there is no check at this time to make sure you follow that
rule. So please follow the rule.

To see an example:

``` c
[ param ] CL = 1, V = 20, KA = 1

[ pkmodel ] cmt = "GUT,CENT", depot = TRUE

[ main ] 
capture tadose = self.tad();

[ table]
capture CP  = CENT/V;
```

``` r

mod %>% 
  ev(amt = 100, ii = 4, addl = 3, time = 2) %>%
  mrgsim(tad = TRUE, add = c(3.888, 5.91)) %>% 
  as_tibble() %>% 
  head(n = 10)
```

    ## # A tibble: 10 × 5
    ##       ID  time   tad tadose    CP
    ##    <dbl> <dbl> <dbl>  <dbl> <dbl>
    ##  1     1  0    -2     -1     0   
    ##  2     1  1    -1     -1     0   
    ##  3     1  2     0     -1     0   
    ##  4     1  2     0      0     0   
    ##  5     1  3     1      1     3.07
    ##  6     1  3.89  1.89   1.89  3.99
    ##  7     1  4     2      2     4.05
    ##  8     1  5     3      3     4.27
    ##  9     1  5.91  3.91   3.91  4.22
    ## 10     1  6     0      0     4.21

You will notice two differences between `tad` (output requested at run
time) and `tadose` (values calculated in the model itself) in the output
listing above:

1.  `tadose` is -1 before the first dose
2.  specifically, `tadose` is -1 at the 2 hour observation record that
    occurs that the same time as the dose, but happens before the dose
    in record order

The main point if this is that you can easily obtain time after dose in
the problem (model) itself to use as you program the model and also
output the number into the simulated output.

## Time after dose in specific compartment

Version 0.10.7 adds a new plugin with the ability to calculate time
after dose in any compartment.

We write a model using the `tad` plugin to track time after dose in
compartments `one` and `two`. We create `tadose` objects to track this
and we can call the `tad()` method on these objects, passing in the
`self` data item.

``` r

code <- '

[plugin] tad

[ global ] 
mrg::tadose tad_cmt_1(1); 
mrg::tadose tad_cmt_2(2);

[ pkmodel ] cmt = "GUT,CENT", depot = TRUE

[ param ] CL = 1, V = 20, KA = 1

[ main ] 
capture tad1 = tad_cmt_1.tad(self); 
capture tad2 = tad_cmt_2.tad(self);

'
  
mod <- mcode("tad", code, soloc = '.')


data <- c(
  ev(amt = 100, cmt = 1, time = 1), 
  ev(amt = 200, cmt = 2, time = 3)
)

mrgsim(mod, data)
```

    ## Model:  tad 
    ## Dim:    27 x 6 
    ## Time:   0 to 24 
    ## ID:     1 
    ##     ID time     GUT   CENT tad1 tad2
    ## 1:   1    0   0.000   0.00   -1   -1
    ## 2:   1    1   0.000   0.00   -1   -1
    ## 3:   1    1 100.000   0.00    0   -1
    ## 4:   1    2  36.788  61.41    1   -1
    ## 5:   1    3  13.534  81.00    2   -1
    ## 6:   1    3  13.534 281.00    2    0
    ## 7:   1    4   4.979 275.61    3    1
    ## 8:   1    5   1.832 265.22    4    2

Note that time after dose is -1 until a dose is administered.

Recall also that time after dose can be calculated more simply if there
is only one dose type by passing the `tad` argument:

``` r

data1 <- filter(data, cmt ==1) %>% mutate(time = 3)
mod %>% mrgsim(data1, tad = TRUE)
```

    ## Model:  tad 
    ## Dim:    26 x 7 
    ## Time:   0 to 24 
    ## ID:     1 
    ##     ID time tad     GUT  CENT tad1 tad2
    ## 1:   1    0  -3   0.000  0.00   -1   -1
    ## 2:   1    1  -2   0.000  0.00   -1   -1
    ## 3:   1    2  -1   0.000  0.00   -1   -1
    ## 4:   1    3   0   0.000  0.00   -1   -1
    ## 5:   1    3   0 100.000  0.00    0   -1
    ## 6:   1    4   1  36.788 61.41    1   -1
    ## 7:   1    5   2  13.534 81.00    2   -1
    ## 8:   1    6   3   4.979 85.36    3   -1

This is a little nicer because it will fill in negative `tad` values for
you.
