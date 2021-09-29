HW2
================
William Haznaw
9/21/2021

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
# install.packages("nycflights13")
library(nycflights13)
library(ggplot2)
library(lubridate)
```

    ## 
    ## Attaching package: 'lubridate'

    ## The following objects are masked from 'package:base':
    ## 
    ##     date, intersect, setdiff, union

How many flights have a missing dep\_time? What other variables are
missing? What might these rows represent?

``` r
cancelled_flights = filter(flights, is.na(dep_time))
head(cancelled_flights)
```

    ## # A tibble: 6 x 19
    ##    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ## 1  2013     1     1       NA           1630        NA       NA           1815
    ## 2  2013     1     1       NA           1935        NA       NA           2240
    ## 3  2013     1     1       NA           1500        NA       NA           1825
    ## 4  2013     1     1       NA            600        NA       NA            901
    ## 5  2013     1     2       NA           1540        NA       NA           1747
    ## 6  2013     1     2       NA           1620        NA       NA           1746
    ## # … with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
    ## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
    ## #   hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
nrow(cancelled_flights)
```

    ## [1] 8255

Cancelled Flights. The other missing data is the delay of the flight and
also the arrival time because the flight would never have taken off.

Currently dep\_time and sched\_dep\_time are convenient to look at, but
hard to compute with because they’re not really continuous numbers.
Convert them to a more convenient representation of number of minutes
since midnight.

``` r
flights <-flights %>% 
    mutate(dep_minutes_since_midnight = (dep_time %/%100)*60 + (dep_time%%100),
           arr_minutes_since_midnight = (arr_time %/%100)*60 + (arr_time%%100)) 


flights %>% 
    select(dep_minutes_since_midnight,arr_minutes_since_midnight)
```

    ## # A tibble: 336,776 x 2
    ##    dep_minutes_since_midnight arr_minutes_since_midnight
    ##                         <dbl>                      <dbl>
    ##  1                        317                        510
    ##  2                        333                        530
    ##  3                        342                        563
    ##  4                        344                        604
    ##  5                        354                        492
    ##  6                        354                        460
    ##  7                        355                        553
    ##  8                        357                        429
    ##  9                        357                        518
    ## 10                        358                        473
    ## # … with 336,766 more rows

Look at the number of canceled flights per day. Is there a pattern? Is
the proportion of canceled flights related to the average delay? Use
multiple dyplr operations, all on one line, concluding with
ggplot(aes(x= ,y=)) + geom\_point()

``` r
flights %>%
  mutate(dep_date = lubridate::make_datetime(year, month, day)) %>%
  group_by(dep_date) %>%
  summarise(cancelled = sum(is.na(dep_delay)), 
            n = n(),
            mean_dep_delay = mean(dep_delay,na.rm=TRUE),
            mean_arr_delay = mean(arr_delay,na.rm=TRUE)) %>%
    ggplot(aes(x= cancelled/n)) + 
    geom_point(aes(y=mean_dep_delay)) + 
    geom_point(aes(y=mean_arr_delay)) + 
    ylab('mean delay')
```

    ## `summarise()` ungrouping output (override with `.groups` argument)

![](HW2_files/figure-gfm/unnamed-chunk-4-1.png)<!-- --> There is a
slight pattern of cancelled to mean delay but not the strongest there
could be.
