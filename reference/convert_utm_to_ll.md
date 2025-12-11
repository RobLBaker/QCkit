# Coordinate Conversion from UTM to Latitude and Longitude

**\[superseded\]** `convert_utm_to_ll()` was superseded in favor of
[`generate_ll_from_utm()`](https://nationalparkservice.github.io/QCkit/reference/generate_ll_from_utm.md)
to support and encourage including zone and datum columns in datasets.
[`generate_ll_from_utm()`](https://nationalparkservice.github.io/QCkit/reference/generate_ll_from_utm.md)
also adds the ability to specify the coordinate reference system for
lat/long coordinates, and accepts column names either quoted or unquoted
for better compatibility with tidyverse piping. `convert_utm_to_ll()`
takes your dataframe with UTM coordinates in separate Easting and
Northing columns, and adds on an additional two columns with the
converted decimalLatitude and decimalLongitude coordinates using the
reference coordinate system WGS84. You may need to turn the VPN OFF for
this function to work properly.

## Usage

``` r
convert_utm_to_ll(df, EastingCol, NorthingCol, zone, datum = "WGS84")
```

## Arguments

- df:

  - The dataframe with UTM coordinates you would like to convert. Input
    the name of your dataframe.

- EastingCol:

  - The name of your Easting UTM column. Input the name in quotations,
    ie. "EastingCol".

- NorthingCol:

  - The name of your Northing UTM column. Input the name in quotations,
    ie. "NorthingCol".

- zone:

  - The UTM Zone. Input the zone number in quotations, ie. "17".

- datum:

  - The datum used in the coordinate reference system of your
    coordinates. Input in quotations, ie. "WGS84"

## Value

The function returns your dataframe, mutated with an additional two
columns of decimal Longitude and decimal Latitude.

## Details

Define the name of your dataframe, the easting and northing columns
within it, the UTM zone within which those coordinates are located, and
the reference coordinate system (datum). UTM Northing and Easting
columns must be in separate columns prior to running the function. If a
datum is not defined, the function will default to "WGS84". If there are
missing coordinates in your dataframe they will be preserved, however
they will be moved to the end of your dataframe. Note that some
parameter names are not in snake_case but instead reflect DarwinCore
naming conventions.

## Examples

``` r
if (FALSE) { # \dontrun{
convert_utm_to_ll(
  df = mydataframe,
  EastingCol = "EastingCoords",
  NorthingCol = "NorthingCoords",
  zone = "17",
  datum = "WGS84"
)
} # }
```
