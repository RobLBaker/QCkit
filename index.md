# QCkit

QCkit is a collection of quality control functions to munge, check,
flag, correct, and summarize data collected by the U.S. National Park
Service Inventory & Monitoring Division. These functions will be
particularly useful in preparing data for metadata creation and in
writing Data Release Reports, but may include aspects that are more
widely applicable outside the National Park Service (such as converting
UTMs to Latitude and Longitude).

Functions are typically user generated and so may not have been
thoroughly tested for all use cases.

If you would like to contribute useful functions please initiate a pull
request.

Please request enhancements and bug fixes through
[Issues](https://github.com/doi-nps/QCkit/issues).

# Installation

Stand-alone installation:

``` r
# install.packages("remotes")
remotes::install_github("doi-nps/QCkit")
library(QCkit)
```

QCkit is also part of the
[NPSdataverse](https://doi-nps.github.io/NPSdataverse/) and can be
installed along with the other components of NPSdataverse:

``` r
# install.packages("remotes")
remotes::install_github("doi-nps/NPSdataverse")
library(NPSdataverse)
```
