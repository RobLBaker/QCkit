# Returns the user's ORCID ID from active directory

This is a function to grab a users ORCID from Active Directory. Requires
VPN to access AD. If the user does not have an ORCID, returns "NA".

## Usage

``` r
get_user_orcid()
```

## Value

Sting. The user's ORCID ID

## Examples

``` r
if (FALSE) { # \dontrun{
orcid <- get_user_orcid()
} # }
```
