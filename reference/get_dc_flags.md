# Create Table of Data Quality Flags in Flagging Columns within individual data columns

**\[deprecated\]** get_dc_flags (dc=data columns) returns a data frame
that, for each data file in a data package lists the name of each data
flagging column and the number of each flag type within that column (A,
AE, R, P) as well as the total number of data points in the data
flagging columns for each .csv, excluding NAs. Unweighted Relative
Response (RRU) is calculated as the total number of accepted data points
(A, AE, and data that are not flagged).

## Usage

``` r
get_dc_flags(directory = here::here())
```

## Arguments

- directory:

  is the path to the data package .csv files (defaults to the current
  working directory).

## Value

a dataframe named dc_flag that contains a row for each .csv file in the
directory with the file name, the count of each flag and total number of
data points in each .csv (including data flagging columns).

## Details

The function can be run from within the working directory where the data
package is, or the directory can be specified. The function only
supports .csv files and assumes that all data flagging columns have
column names ending in "\_flag". It counts cells within those columns
that start with one of the flagging characters (A, AE, R, P) and ignores
trailing characters and whitespaces.

## Examples

``` r
if (FALSE) { # \dontrun{
get_df_flags("~/my_data_package_directory")
get_df_flags() # if your current working directory IS the data package
directory.
# ->
get_custom_flags(output="columns")
} # }
```
