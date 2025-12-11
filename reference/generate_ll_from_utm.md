# Coordinate Conversion from UTM to Latitude and Longitude

`generate_ll_from_utm()` takes your dataframe with UTM coordinates in
separate Easting and Northing columns, and adds on an additional two
columns with the converted decimalLatitude and decimalLongitude
coordinates using the reference coordinate system NAD83. Your data must
also contain columns specifying the zone and datum of your UTM
coordinates. In contrast to
[`convert_utm_to_ll()`](https://nationalparkservice.github.io/QCkit/reference/convert_utm_to_ll.md)
(superseded), `generate_ll_from_utm()` requires zone and datum columns.
It supports quoted or unquoted column names and a user-specified datum
for lat/long coordinates. It also adds an extra column to the output
data table that documents the lat/long coordinate reference system.

## Usage

``` r
generate_ll_from_utm(
  df,
  EastingCol,
  NorthingCol,
  ZoneCol,
  DatumCol,
  latlong_datum = "NAD83"
)
```

## Arguments

- df:

  - The dataframe with UTM coordinates you would like to convert. Input
    the name of your dataframe.

- EastingCol:

  - The name of your Easting UTM column. You may input the name with or
    without quotations, ie. EastingCol and "EastingCol" are both valid.

- NorthingCol:

  - The name of your Northing UTM column. You may input the name with or
    without quotations, ie. NorthingCol and "NorthingCol" are both
    valid.

- ZoneCol:

  - The column containing the UTM zone, with or without quotations.

- DatumCol:

  - The column containing the datum for your UTM coordinates, with or
    without quotations.

- latlong_datum:

  - The datum to use for lat/long coordinates. Defaults to NAD83.

## Value

The function returns your dataframe, mutated with an additional two
columns of decimalLongitude and decimalLatitude plus a column
LatLong_CRS containing a PROJ string that specifies the coordinate
reference system for these data.

## Details

Define the name of your dataframe, the easting and northing columns
within it, the UTM zone within which those coordinates are located, and
the reference coordinate system (datum). UTM Northing and Easting
columns must be in separate columns prior to running the function. If a
datum for the lat/long output is not defined, the function will default
to "NAD83". If there are missing coordinates in your dataframe they will
be preserved, however they will be moved to the end of your dataframe.
Note that some parameter names are not in snake_case but instead reflect
DarwinCore naming conventions.

This function uses tidy evaluation (i.e. you can provide column name
arguments as strings or you can leave them unquoted). If you wish to
store column names as strings in variables, you must enclose the
variables in double curly braces when you pass them into the function.
See code examples below.

## Examples

``` r
if (FALSE) { # \dontrun{

# Using magrittr pipe (%>%) and unquoted column names
my_dataframe %>%
generate_ll_from_utm(
  EastingCol = UTM_X,
  NorthingCol = UTM_Y,
  ZoneCol = Zone,
  DatumCol = Datum
)

# Providing column names as strings (in quotes)
generate_ll_from_utm(
  df = mydataframe,
  EastingCol = "EastingCoords",
  NorthingCol = "NorthingCoords",
  ZoneCol = "zone",
  DatumCol = "datum",
  latlong_datum = "WGS84"
)

# Column names stored as strings in separate variables
easting <- "EastingCoords"
northing <- "NorthingCoords"
zonecol <- "zone"
datumcol <- "datum"
latlong_dat <- "WGS84"

generate_ll_from_utm(
  df = mydataframe,
  EastingCol = {{easting}},  # enclose variables that store column names in {{}}
  NorthingCol = {{northing}},
  ZoneCol = {{zonecol}},
  DatumCol = {{datumcol}},
  latlong_datum = latlong_dat  # this isn't a column name so it doesn't need {{}}
)

} # }
```
