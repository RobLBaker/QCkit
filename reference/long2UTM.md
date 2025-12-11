# Return UTM Zone

**\[deprecated\]** `long2UTM` was deprecated in favor of
[`convert_long_to_utm()`](https://nationalparkservice.github.io/QCkit/reference/convert_long_to_utm.md)
to enforce a consistent function naming pattern across the package and
to conform to the tidyverse style guide.

`long2UTM()` take a longitude coordinate and returns the corresponding
UTM zone.

## Usage

``` r
long2UTM(lon)
```

## Arguments

- lon:

  - Decimal degree longitude value

## Value

The function returns a numeric UTM zone (between 1 and 60).

## Details

Input a longitude (decimal degree) coordinate and this simple function
returns the number of the UTM zone where that point falls.
