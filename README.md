pa_2
================
Hector
2025-10-22

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.1     ✔ stringr   1.5.1
    ## ✔ ggplot2   4.0.0     ✔ tibble    3.3.0
    ## ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
    ## ✔ purrr     1.1.0     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
dat <- read.csv("./data/data.csv")

dat <- dat |>
  separate(
    col = info,
    into = c("word", "stress_cond"),
    sep = "_"
  )
library(dplyr)
library(tidyr)
library(ggplot2)

# Recode stress labels to look nice
dat <- dat |>
  mutate(
    stress_cond = recode(stress_cond,
                         "stressed" = "Stressed",
                         "unstressed" = "Unstressed")
  )

aggregate (durationV~stress_cond, FUN = mean, data = dat)
```

    ##   stress_cond durationV
    ## 1           1     0.086
    ## 2           2     0.052

``` r
aggregate (f0~stress_cond, FUN = mean, data = dat)
```

    ##   stress_cond      f0
    ## 1           1 106.530
    ## 2           2  93.934

``` r
aggregate (int~stress_cond, FUN = mean, data = dat)
```

    ##   stress_cond    int
    ## 1           1 68.906
    ## 2           2 67.270
