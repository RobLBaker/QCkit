# Convert Coordinates Into a Polygon to Obscure Specific Location

`fuzz_location()` "fuzzes" a specific location to something less precise
prior to public release of information about sensitive resources for
which data are not to be released to the public. This function takes
coordinates in either UTM or decimal degrees, converts to UTM (if in
decimal degrees), creates a bounding box based on rounding of UTM
coordinates, and then creates a polygon from the resultant points. The
function returns a string in Well-Known-Text format.

## Usage

``` r
fuzz_location(lat, lon, coord_ref_sys = 4326, fuzz_level = "Fuzzed - 1km")
```

## Arguments

- lat:

  - The latitude in either UTMs or decimal degrees.

- lon:

  - The longitude in either UTMs or decimal degrees

- coord_ref_sys:

  - The EPSG coordinate system of the latitude and longitude
    coordinates. Either 4326 for decimal degrees/WGS84 datum, 4269 for
    decimal degrees/NAD83, or 326xx for UTM/WGS84 datum (where the xx is
    the northern UTM zone). For example 32616 is for UTM zone 16N.

- fuzz_level:

  - Use "Fuzzed - 10km", "Fuzzed - 1km", or "Fuzzed - 100m"

## Details

Details will be defined later.

## Examples

``` r
if (FALSE) { # \dontrun{
fuzz_location(703977, 4035059, 32616, "Fuzzed - 1km")
fuzz_location(36.43909, -84.72429, 4326, "Fuzzed - 1km")
} # }
```
