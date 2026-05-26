# Schedule a series of event objects

Use this function when you want to schedule two or more event objects in
time according the dosing interval (`ii`) and additional doses (`addl`).

## Usage

``` r
ev_seq(..., ID = NULL, .dots = NULL, id = NULL)

# S3 method for class 'ev'
seq(...)
```

## Arguments

- ...:

  event objects or numeric arguments named `wait` or `ii` to implement a
  period of no-dosing activity in the sequence (see **Details**).

- ID:

  numeric vector of subject IDs.

- .dots:

  a list of event objects that replaces `...`.

- id:

  deprecated; use `ID`.

## Value

A single event object sorted by `time`.

## Details

Use the generic [`seq()`](https://rdrr.io/r/base/seq.html) when the
first argument is an event object. If a waiting period (`wait` or `ii`)
is the first event, you will need to use `ev_seq()`. When an event
object has multiple rows, the end time for that sequence is taken to be
one dosing interval after the event that takes place on the last row of
the event object.

The doses for the next event line start after all of the doses from the
previous event line plus one dosing interval from the previous event
line (see **Examples**).

When numerics named `wait` or `ii` are mixed in with the event objects,
a period with no dosing activity is incorporated into the sequence,
between the adjacent dosing event objects. `wait` and `ii` accomplish a
similar result, but differ by the starting point for the inactive
period.

- Use `wait` to schedule the next dose relative to the end of the dosing
  interval for the previous dose.

- Use `ii` to schedule the next dose relative to the time of the the
  previous dose.

So `wait` acts like similar to an event object, by starting the waiting
period from one dosing interval after the last dose while `ii` starts
the waiting period from the time of the last dose itself. Both `wait`
and `ii` can accomplish identical behavior depending on whether the last
dosing interval is included (or not) in the value. Values for `wait` or
`ii` can be negative.

**NOTE**: `.ii` had been available historically as an undocumented
feature. Starting with mrgsolve version `0.11.3`, the argument will be
called `ii`. For now, both `ii` and `.ii` will be accepted but you will
get a deprecation warning if you use `.ii`. Please use `ii` instead.

Values for `time` in any event object act like a prefix time spacer
wherever that event occurs in the event sequence (see **Examples**).

## Examples

``` r
e1 <- ev(amt = 100, ii = 12, addl = 1)

e2 <- ev(amt = 200)

seq(e1, e2)
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100 12    1   1    1
#> 2   24 200  0    0   1    1

seq(e1, ii = 8, e2)
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100 12    1   1    1
#> 2   20 200  0    0   1    1

seq(e1, wait = 8, e2)
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100 12    1   1    1
#> 2   32 200  0    0   1    1

seq(e1, ii = 8, e2, ID = seq(10))
#> Events:
#>    ID time amt ii addl cmt evid
#> 1   1    0 100 12    1   1    1
#> 2   2    0 100 12    1   1    1
#> 3   3    0 100 12    1   1    1
#> 4   4    0 100 12    1   1    1
#> 5   5    0 100 12    1   1    1
#> 6   6    0 100 12    1   1    1
#> 7   7    0 100 12    1   1    1
#> 8   8    0 100 12    1   1    1
#> 9   9    0 100 12    1   1    1
#> 10 10    0 100 12    1   1    1
#> 11  1   20 200  0    0   1    1
#> 12  2   20 200  0    0   1    1
#> 13  3   20 200  0    0   1    1
#> 14  4   20 200  0    0   1    1
#> 15  5   20 200  0    0   1    1
#> 16  6   20 200  0    0   1    1
#> 17  7   20 200  0    0   1    1
#> 18  8   20 200  0    0   1    1
#> 19  9   20 200  0    0   1    1
#> 20 10   20 200  0    0   1    1

ev_seq(ii = 12, e1, ii = 120, e2, ii = 120, e1)
#> Events:
#>   time amt ii addl cmt evid
#> 1   12 100 12    1   1    1
#> 2  144 200  0    0   1    1
#> 3  264 100 12    1   1    1

seq(ev(amt = 100, ii = 12), ev(time = 8, amt = 200))
#> Events:
#>   time amt ii addl cmt evid
#> 1    0 100 12    0   1    1
#> 2   20 200  0    0   1    1

```
