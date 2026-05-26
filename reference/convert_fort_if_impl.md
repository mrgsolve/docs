# Convert Fortran-style IF/THEN/ELSE/ENDIF to C++

Translates Fortran block-form and single-line IF constructs to C++ in
each element of `code`. Fortran relational and logical operators
(`.GE.`, `.LE.`, `.GT.`, `.LT.`, `.EQ.`, `.NE.`, `.AND.`, `.OR.`) are
converted everywhere they appear. Matching is case-insensitive.

## Usage

``` r
convert_fort_if_impl(code)
```

## Arguments

- code:

  Character vector of source lines.

## Value

Character vector with Fortran IF constructs replaced by C++.
