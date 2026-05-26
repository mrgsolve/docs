# Insert semicolons at the end of C++ statements

Appends a semicolon to each element of `code` that looks like a
statement but does not already have one. Lines that are left unchanged:
blank lines, lines already ending with `;`, lines ending with `{` or
`}`, C/C++ comments (`//` or `/*`), preprocessor directives (`#`), lines
containing block options (line starts with `@`), and lines ending with
Fortran block-structure keywords.

## Usage

``` r
convert_semicolons_impl(code)
```

## Arguments

- code:

  Character vector of source lines.

## Value

Character vector with semicolons inserted where needed.
