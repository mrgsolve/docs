# Schedule dosing events on days of the week

This function lets you schedule doses on specific days of the week,
allowing you to create dosing regimens on Monday/Wednesday/Friday, or
Tuesday/Thursday, or every other day (however you want to define that)
etc.

## Usage

``` r
ev_days(
  ev = NULL,
  days = "",
  addl = 0,
  ii = 168,
  unit = c("hours", "days"),
  ...
)
```

## Arguments

- ev:

  an event object.

- days:

  comma- or space-separated character string of valid days of the the
  week (see details).

- addl:

  additional doses to administer.

- ii:

  inter-dose interval; intended use is to keep this at the default
  value.

- unit:

  time unit; the function can only currently handle hours or days.

- ...:

  event objects named by one of the valid days of the week (see
  **Details**).

## Details

Valid names of the week are:

- `m` for Monday

- `t` for Tuesday

- `w` for Wednesday

- `th` for Thursday

- `f` for Friday

- `sa` for Saturday

- `s` for Sunday

The whole purpose of this function is to schedule doses on specific days
of the week, in a repeating weekly schedule. Please do use caution when
changing `ii` from its default value.

## Examples

``` r

# Monday, Wednesday, Friday x 4 weeks
e1 <- ev(amt = 100)
ev_days(e1, days="m,w,f", addl = 3)
#>   time amt cmt evid  ii addl
#> 1    0 100   1    1 168    3
#> 2   48 100   1    1 168    3
#> 3   96 100   1    1 168    3

# 50 mg Tuesdays, 100 mg Thursdays x 6 months
e2 <- ev(amt = 50)
ev_days(t = e2, th = e1, addl = 23)
#>   time amt cmt evid  ii addl
#> 1   24  50   1    1 168   23
#> 2   72 100   1    1 168   23
```
