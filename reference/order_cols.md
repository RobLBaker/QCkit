# Ordering Columns Function 03-21-2023

`order_cols()` Checks and orders columns with TDWG Darwin Core naming
standards and custom names in a dataset

## Usage

``` r
order_cols(df)
```

## Arguments

- df:

  - This is the dataframe you want to run against the function. To call,
    simply type df = "the name of your dataframe".

## Value

- The function returns a list of required and suggested columns to
  include in your dataset. When assigning to an object, the object
  contains your new dataset with all columns ordered properly.

## Details

Check to see if you have three (highly) recommended columns (locality,
type, basisOfRecord) and various suggested columns present in your
dataset. Print a list of which columns are present and which are not.
Then, order all the columns in your dataset in the following order:
(highly) recommended columns, suggested columns, the rest of the Darwin
Core columns, "custom\_" (non-Darwin Core) columns, and finally
sensitive species data columns.

Any columns that are not darwinCore term names, do not start with
"custom\_" or are not "scientificName_flag" will be placed after the
darwinCore columns and before the "custom\_" columns.

One exception is if your dataset includes the column
custom_TaxonomicNotes, it will be placed directly after namePublishedIn,
if that column exists.

Suggested darwinCore column names (plus scientificName_flag) include (in
the order they will be placed): eventDate, eventDate_flag,
scientificName, scientificName_flag, taxonRank, verbatimIdentification,
vernacularName, namePublishedIn, recordedBy, individualCount,
decimalLongitude, decimalLatitude, coordinate_flag, geodeticDatum",
verbatimCoordinates, verbatimCoordinateSystem,
verbatimSRS,coordinateUncertaintyInMeters. Note that suggested names
include some custom, non-Darwin Core names such as
"scientificName_flag".

sensitive species data columns are defined as: informationWithheld,
dataGeneralizations, and footprintWKT.

## Examples

``` r
if (FALSE) { # \dontrun{
order_cols(df)
} # }
```
