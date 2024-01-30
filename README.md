
<!-- README.md is generated from README.Rmd. Please edit that file -->

# readjsa

<!-- badges: start -->

[![R-CMD-check](https://github.com/MattCowgill/readjsa/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/MattCowgill/readjsa/actions/workflows/R-CMD-check.yaml)
<!-- badges: end -->

{readjsa} streamlines the process of getting data from [Jobs and Skills
Australia](https://www.jobsandskills.gov.au) into R.

## Installation

You can install the development version of readjsa from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("MattCowgill/readjsa")
```

## Getting REOS data

It’s straightforward to get data from the Recruitment Experience &
Outlook Survey (REOS):

``` r
library(readjsa)
library(ggplot2)
library(dplyr)
#> 
#> Attaching package: 'dplyr'
#> The following objects are masked from 'package:stats':
#> 
#>     filter, lag
#> The following objects are masked from 'package:base':
#> 
#>     intersect, setdiff, setequal, union

reos <- read_reos(tables = "all")

reos |> 
  filter(series == "Recruitment rate",
         frequency == "Monthly") |> 
  ggplot(aes(x = date, y = value, col = disaggregation)) +
  geom_line()
```

<img src="man/figures/README-reos-example-1.png" width="100%" />
