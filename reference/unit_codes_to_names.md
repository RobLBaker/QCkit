# Converts unit codes to full unit (park) names

`unit_code_to_names` takes a single unit code or vector of unit codes
and returns a data frame of full unit names using a public IRMA API. For
example if given the code "ROMO" the function will return "Rocky
Mountain National Park".

## Usage

``` r
unit_codes_to_names(unit_code)
```

## Arguments

- unit_code:

  string or list of strings consisting of (typically) four-letter unit
  codes.

## Value

a data frame consisting of a single column of full park names

## Examples

``` r
if (FALSE) { # \dontrun{
 unit_codes_to_names("ROMO")
 unit_codes_to_names(c("ROMO", "GRYN"))
 } # }
```
