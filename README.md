<a href="https://covid19datahub.io"><img src="https://storage.covid19datahub.io/logo.svg" align="right" height="128"/></a>

# R Interface to COVID-19 Data Hub

![](https://www.r-pkg.org/badges/version/COVID19) ![](https://cranlogs.r-pkg.org/badges/last-month/COVID19) [![DOI](https://joss.theoj.org/papers/10.21105/joss.02376/status.svg)](https://doi.org/10.21105/joss.02376)

## Quickstart

```R
# install the package
install.packages("COVID19")

# load the package
library("COVID19")
```

## Download the data

See the full documentation by typing `?covid19`

```r
# Worldwide data by country
x <- covid19()

# Worldwide data by state
x <- covid19(level = 2)

# Specific country data by city
x <- covid19(c("Italy","US"), level = 3)
```

## Merge with World Bank Open Data

The dataset can be extended with [World Bank Open Data](https://data.worldbank.org/) via the argument `wb`, a character vector of indicator codes. The codes can be found by inspecting the corresponding URL. For example, the code of the GDP indicator available at https://data.worldbank.org/indicator/NY.GDP.MKTP.CD is `NY.GDP.MKTP.CD`. 

```R
wb <- c("gdp" = "NY.GDP.MKTP.CD", "hosp_beds" = "SH.MED.BEDS.ZS")
x  <- covid19(wb = wb)
```

## Merge with Google Mobility Reports

The dataset can be extended with [Google Mobility Reports](https://www.google.com/covid19/mobility/) via the argument `gmr`, the url to the Google CSV file. At the time of writing, the CSV is available at:

```R
gmr <- "https://www.gstatic.com/covid19/mobility/Global_Mobility_Report.csv"
x   <- covid19(gmr = gmr)
```

## Merge with Apple Mobility Reports

The dataset can be extended with [Apple Mobility Reports](https://covid19.apple.com/mobility) via the argument `amr`, the url to the Apple CSV file. At the time of writing, the CSV is available at:

```R
amr <- "https://covid19-static.cdn-apple.com/covid19-mobility-data/"
amr <- paste0(amr, "2015HotfixDev10/v3/en-us/applemobilitytrends-2020-08-24.csv")
x   <- covid19(amr = amr)
```

## Data sources

Data sources are stored in the `src` attribute.

```R
s <- covid19cite(x)
View(s)
```

