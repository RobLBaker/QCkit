# Retrieve the polygon information for the park unit from NPS REST services

`get_park_polygon()` retrieves a geoJSON string for a polygon of a park
unit. This is not the official boundary. Note that the REST API call
returns the default "convexHull". This is will work better or worse for
some parks, depending on the park shape/geography/number of disjunct
areas. \#'

## Usage

``` r
get_park_polygon(unit_code)
```

## Arguments

- unit_code:

  is the four-character unit code as designated by NPS.

## Examples

``` r
if (FALSE) { # \dontrun{
qc_getParkPolygon("OBRI")
} # }
```
