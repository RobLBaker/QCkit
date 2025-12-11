# Handles multiple missing values

**\[experimental\]** **\[questioning\]** Given a file name (.csv only)
and path, the function will search the columns for any that contain
multiple user-specified missing value codes. For any column with
multiple missing value codes, all the missing values (including blanks)
will be replaced with NA. A new column will be generated and, populated
with the given missing value code from the origin column. Values that
were not missing will be populated with "not_missing". The newly
generate column of categorical variables can be used do describe the
various/multiple reasons for why data is absent in the original column.

The function will then write the new dataframe to a file, overwriting
the original file. If it is important to keep a copy of the original
file, make a copy prior to running the function.

WARNING: this function will replace any blank cells in your data with
NA!

## Usage

``` r
document_missing_values(
  file_name,
  directory = here::here(),
  colname = NA,
  missing_val_codes = NA,
  replace_value = NA
)
```

## Arguments

- file_name:

  String. The name of the file to inspect

- directory:

  String. Location of file to read/write. Defaults to the current
  working directory.

- colname:

  **\[experimental\]** String. The columns to inspect. CURRENTLY ONLY
  WORKS AS SET TO DEFAULT "NA".

- missing_val_codes:

  List. A list of strings containing the missing value code or codes to
  search for.

- replace_value:

  String. The value (singular) to replace multiple missing values with.
  Defaults to NA.

## Value

writes a new dataframe to file. Return invisible.

## Details

Blank cells will be treated as NA.

## Examples

``` r
if (FALSE) { # \dontrun{
document_missing_values(file_name = "mydata.csv",
                        directory = here::here(),
                        colname = NA, #do not change during function development
                        missing_val_codes = c("missing", "blank", "no data"),
                        replace_value = NA)
                        } # }
```
