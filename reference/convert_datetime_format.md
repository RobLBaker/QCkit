# Convert EML date/time format string to one that R can parse

Convert EML date/time format string to one that R can parse

## Usage

``` r
convert_datetime_format(eml_format_string, convert_z = FALSE)
```

## Arguments

- eml_format_string:

  A character vector of EML date/time format strings. This function
  understands the following codes: YYYY = four digit year, YY = two
  digit year, MMM = three letter month abbrev., MM = two digit month, DD
  = two digit day, hh or HH = 24 hour time, mm = minutes, ss or SS =
  seconds, +/-hhmm, +/-hh:mm, or +/-hh = UTC offset.

- convert_z:

  Should a "Z" at the end of the format string (indicating UTC) be
  replaced by a "%z"? Only set to `TRUE` if you plan to use
  `fix_utc_offset` to change "Z" in datetime strings to "+0000".

## Value

A character vector of date/time format strings that can be parsed by
`readr` or `strptime`.

## Details

`convert_datetime_format()` is not a sophisticated function. If the EML
format string is not valid, it will happily and without complaint return
an R format string that will break your code. You have been warned. Note
that UTC offset formats using a colon or only two digits will be parsed
by this function, but if parsing datetime values from strings, you will
also need to use `fix_utc_offset` to change the UTC offsets to the
+/-hhmm format that R can read.

## Examples

``` r
convert_datetime_format("MM/DD/YYYY")
#> [1] "%m/%d/%Y"
convert_datetime_format(c("MM/DD/YYYY", "YY-MM-DD"))
#> [1] "%m/%d/%Y" "%y-%m-%d"
```
