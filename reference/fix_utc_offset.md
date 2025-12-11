# Fix UTC offset strings

UTC offsets can be formatted in multiple ways (e.g. -07, -07:00, -0700)
and R often struggles to parse these offsets. This function takes
date/time strings with valid UTC offsets, and formats them so that they
are consistent and readable by R. Here, you can supply a vector of dates
in ISO 8601 format and they will be returned in a consistent format
compatible with R. Date strings with missing or invalid UTC offsets will
result in a warning.

## Usage

``` r
fix_utc_offset(datetime_strings)
```

## Arguments

- datetime_strings:

  Character vector of dates in ISO 8601 format

## Value

datetime_strings with UTC offsets consistently formatted to four digits
(e.g. "2023-11-16T03:32:49-0700").

## Examples

``` r
datetimes <- c("2023-11-16T03:32:49+07:00", "2023-11-16T03:32:49-07",
"2023-11-16T03:32:49","2023-11-16T03:32:49Z")
fix_utc_offset(datetimes)
#> Warning: Date strings contain missing or invalid UTC offsets
#> [1] "2023-11-16T03:32:49+0700" "2023-11-16T03:32:49-0700"
#> [3] "2023-11-16T03:32:49"      "2023-11-16T03:32:49+0000"
```
