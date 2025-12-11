# Return UTM Zone

**\[deprecated\]** `convert_long_2_utm()` was deprecated in favor of
[`get_utm_zone()`](https://nationalparkservice.github.io/QCkit/reference/get_utm_zone.md)
as the new funciton name more accurately reflects what the function
does. `convert_long_to_utm()` take a longitude coordinate and returns
the corresponding UTM zone.

## Usage

``` r
convert_long_to_utm(lon)
```

## Arguments

- lon:

  - Decimal degree longitude value

## Value

The function returns a numeric UTM zone (between 1 and 60).

## Details

Input a longitude (decimal degree) coordinate and this simple function
returns the number of the UTM zone where that point falls.
