# Test whether decimal GPS coordinates are inside a park unit

This function can take a list of coordinates and park units as input. In
addition to being vectorized, depending on the park borders, it can be a
major improvement on
[`validate_coord()`](https://nationalparkservice.github.io/QCkit/reference/validate_coord.md).

## Usage

``` r
validate_coord_list(lat, lon, park_units)
```

## Arguments

- lat:

  numeric. An individual or vector of numeric values representing the
  decimal degree latitude of a coordinate

- lon:

  numeric. An individual or vector of numeric values representing the
  decimal degree longitude of a coordinate

- park_units:

  String. Or list of strings each containing the four letter park unit
  designation

## Value

logical

## Examples

``` r
if (FALSE) { # \dontrun{
x <- validate_coord_list(lat = 105.555, long = -47.4332, park_units = "DRTO")

# or a dataframe with many coordinates and potentially many park units:
x <- validate_coord_list(lat = df$decimalLatitutde,
                lon = df$decimalLongitude,
                park_units = df$park_units)
# you can then merge it back in to the original dataframe:
df$test_GPS_coord <- x
} # }
```
