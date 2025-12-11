# Check whether a coordinate pair is within the polygon of a park unit

`validate_coord()` compares a coordinate pair (in decimal degrees) to
the polygon for a park unit as provided through the NPS Units rest
services. The function returns a value of TRUE or FALSE.

## Usage

``` r
validate_coord(unit_code, lat, lon)
```

## Arguments

- unit_code:

  is the four-character unit code as designated by NPS.

- lat:

  latitude, in decimal degrees.

- lon:

  longitude, in decimal degrees.

## Examples

``` r
if (FALSE) { # \dontrun{
validate_coord("OBRI", 36.07951, -84.65610)
} # }
```
