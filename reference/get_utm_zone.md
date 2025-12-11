# Return UTM Zone

`get_utm_zone()` replaces `convert_long_2_utm()` as this function name
is more descriptive. `get_utm_zone()` takes a longitude coordinate and
returns the corresponding UTM zone.

## Usage

``` r
get_utm_zone(lon)
```

## Arguments

- lon:

  - Decimal degree longitude value

## Value

The function returns a numeric UTM zone (between 1 and 60).

## Details

Input a longitude (decimal degree) coordinate and this simple function
returns the number of the UTM zone where that point falls.
