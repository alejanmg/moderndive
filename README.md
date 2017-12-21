
ModernDive R Package <img src="images/hex_blue_text.png" align="right" width=125 />
-----------------------------------------------------------------------------------

R package accompanying ModernDive: An Introduction to Statistical and Data Sciences via R available at <http://moderndive.com/>.

Installation
------------

Get the released version from CRAN:

``` r
install.packages("moderndive")
```

Or the development version from GitHub:

``` r
# If you haven't installed devtools yet, do so:
# install.packages("devtools")
devtools::install_github("moderndive/moderndive")
```

Demo
----

The following three `get_regression_X()` functions are tidyverse-friendly wrappers meant for the novice regression user. They have more intuitive/verb-like function names than the corresponding `broom` commands:

-   `get_regression_table()`: a wrapper to `tidy()` to return the regression table
-   `get_regression_points()`: a wrapper to `augment()` to return a table of all regression points
-   `get_regression_summaries()`: a wrapper to `glance()` to return summary statistics about the regression

Furthermore

-   It cleans the output format eliminates all information not pertinent for simple analyses
-   You can set the output to be `knitr::kable()` suitable for R Markdown output via `print = TRUE`
-   You can control the pseudoprecision via the `digits` argument

``` r
devtools::install_github("moderndive/moderndive")
library(moderndive)
library(tidyverse)

# Regression tables
get_regression_table(mpg ~ hp, data = mtcars)
get_regression_table(mpg ~ hp + wt, data = mtcars, digits = 4, print = TRUE)

# Regression points. For residual analysis for example
mtcars <- mtcars %>% 
  mutate(cyl = as.factor(cyl))
get_regression_points(mpg ~ hp + cyl, data = mtcars)

# Regression summaries
get_regression_summaries(mpg ~ hp, data = mtcars)
get_regression_summaries(mpg ~ hp, data = mtcars, digits = 5, print = TRUE)
```