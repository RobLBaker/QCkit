# Remove empty tables from a list

Remove empty tables from a list

## Usage

``` r
remove_empty_tables(df_list)
```

## Arguments

- df_list:

  A list of tibbles or dataframes.

## Value

The same list but with empty tables removed.

## Examples

``` r
test_list <- list(item_a = tibble::tibble,
                  item_b = mtcars,
                  item_c = iris)

tidy_list <- remove_empty_tables(test_list)
```
