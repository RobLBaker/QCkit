# Add elevation to a dataset

`get_elevation()` takes a dataframe that includes GPS coordinates (in
decimal degrees) and returns a dataframe with two new columns added to
it, minimumElevationInMeters and maximumElevationInMeters. The function
requires that the data supplied are numeric and that missing values are
specified with NA.

## Usage

``` r
get_elevation(
  df,
  decimal_lat,
  decimal_long,
  spatial_ref = c(4326, 102100),
  force = FALSE
)
```

## Arguments

- df:

  a data frame containing GPS decimal coordinates for individual points
  with latitude and longitude in separate columns.

- decimal_lat:

  String. The name of the column containing longitudes

- decimal_long:

  String. The name of the column containing latitudes

- spatial_ref:

  Categorical. Defaults to 4326. Can also be set to 102100.

- force:

  Logical. Defaults to FALSE. Returns verbose comments, interactions,
  and information. Set to TRUE to remove all interactive components and
  reduce/remove all comments and informative print statements.

## Value

a data frame with two new columns, minimumElevationInMeters and
maximumElevationInMeters

## Details

`get_elevation()` uses the USGS API for [The National
Map](https://apps.nationalmap.gov/epqs/) to identify the elevevation for
a given set of GPS coordinates. To reduce API queries (and time to
completion), the function will only search for unique GPS coordinates in
your dataframe. This could take some time. If you have lots of GPS
coordinates, you can also perform a [manual bulk
upload](https://apps.nationalmap.gov/bulkpqs/) (maximum = 500 points).

Note that both new columns (minimumElevationInMeters and
maximumElevationInMeters) contain the same elevation; this is expected
behavior as a single GPS coordinate should have the same maximum and
minimum elevations. The column names are generated in accordance with
the simple [Darwin Core Standards](https://dwc.tdwg.org/).

Points outside of the US may return NA values as they are not part of
The National Map.

## Examples

``` r
 if (FALSE) { # \dontrun{
new_dataframe <- get_elevation(df,
                              "decimalLatitude",
                              "decimalLongitude",
                              spatial_ref="4326")
new_dataframe <- get_elevation(df,
                              "decimalLatitude",
                              "decimalLongitude",
                              spatial_ref="102100",
                              force=TRUE)
 } # }
```
