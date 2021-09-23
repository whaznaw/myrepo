HW1
================
William Haznaw
9/21/2021

1)  compile git and HTML
2)  include link to github
3)  do str(data) and some plot to show
data

<!-- end list -->

``` r
WI_Bridges_new <- fread("https://www.fhwa.dot.gov/bridge/nbi/2020/delimited/WI20.txt")
#head(WI_Bridges_new)

#colnames(WI_Bridges_new)


dataFrame_WI <- WI_Bridges_new %>% 
  as_tibble()


WI_interesting_new <- dataFrame_WI[,c(1:2,4 ,67:69, 27, 111)]
head(WI_interesting_new)
```

    ## # A tibble: 6 x 8
    ##   STATE_CODE_001 STRUCTURE_NUMBE… ROUTE_PREFIX_00… DECK_COND_058
    ##            <int> <chr>                       <int> <chr>        
    ## 1             55 00000000000F303                 6 4            
    ## 2             55 00000000000F304                 6 5            
    ## 3             55 00000000000F310                 6 5            
    ## 4             55 00000000000F311                 6 5            
    ## 5             55 00000000000F315                 6 5            
    ## 6             55 00000000000F317                 6 7            
    ## # … with 4 more variables: SUPERSTRUCTURE_COND_059 <chr>,
    ## #   SUBSTRUCTURE_COND_060 <chr>, YEAR_BUILT_027 <int>,
    ## #   PERCENT_ADT_TRUCK_109 <int>

``` r
WI_interesting_new <- na_if(WI_interesting_new, "N")

WI_interesting_new[, 3] <- sapply(WI_interesting_new[, 3], as.factor)

WI_interesting_new[, 4:6] <- sapply(WI_interesting_new[, c(4:6)], 
                                    as.numeric, na.rm = TRUE)

lm_new <- lm(DECK_COND_058 ~ PERCENT_ADT_TRUCK_109, data = WI_interesting_new)
lm_new2 <-lm(SUPERSTRUCTURE_COND_059 ~ PERCENT_ADT_TRUCK_109, data = WI_interesting_new)
lm_new3 <-lm(SUBSTRUCTURE_COND_060 ~ PERCENT_ADT_TRUCK_109, data = WI_interesting_new)

summary(lm_new)
```

    ## 
    ## Call:
    ## lm(formula = DECK_COND_058 ~ PERCENT_ADT_TRUCK_109, data = WI_interesting_new)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -6.5306 -0.5306  0.2996  0.4694  2.4694 
    ## 
    ## Coefficients:
    ##                       Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)            6.53060    0.01163  561.28   <2e-16 ***
    ## PERCENT_ADT_TRUCK_109  0.02123    0.00173   12.27   <2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 1.073 on 12074 degrees of freedom
    ##   (2195 observations deleted due to missingness)
    ## Multiple R-squared:  0.01231,    Adjusted R-squared:  0.01223 
    ## F-statistic: 150.5 on 1 and 12074 DF,  p-value: < 2.2e-16

``` r
summary(lm_new2)
```

    ## 
    ## Call:
    ## lm(formula = SUPERSTRUCTURE_COND_059 ~ PERCENT_ADT_TRUCK_109, 
    ##     data = WI_interesting_new)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -6.6889 -0.6889  0.2102  1.0589  2.3111 
    ## 
    ## Coefficients:
    ##                       Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)           6.688947   0.012321  542.87   <2e-16 ***
    ## PERCENT_ADT_TRUCK_109 0.025220   0.001829   13.79   <2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 1.137 on 12084 degrees of freedom
    ##   (2185 observations deleted due to missingness)
    ## Multiple R-squared:  0.01549,    Adjusted R-squared:  0.01541 
    ## F-statistic: 190.2 on 1 and 12084 DF,  p-value: < 2.2e-16

``` r
summary(lm_new3)
```

    ## 
    ## Call:
    ## lm(formula = SUBSTRUCTURE_COND_060 ~ PERCENT_ADT_TRUCK_109, data = WI_interesting_new)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -6.7137 -0.7137  0.2161  1.0756  2.2863 
    ## 
    ## Coefficients:
    ##                       Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)           6.713656   0.012778  525.43   <2e-16 ***
    ## PERCENT_ADT_TRUCK_109 0.023419   0.001896   12.35   <2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 1.179 on 12084 degrees of freedom
    ##   (2185 observations deleted due to missingness)
    ## Multiple R-squared:  0.01246,    Adjusted R-squared:  0.01238 
    ## F-statistic: 152.5 on 1 and 12084 DF,  p-value: < 2.2e-16

``` r
# Filtered based on type of road

# WI_interesting_new <- arrange(WI_interesting_new,ROUTE_PREFIX_005B)
# Interstate_highway <- filter(WI_interesting_new, ROUTE_PREFIX_005B == "1")
# U.S._numbered_highway<- filter(WI_interesting_new, ROUTE_PREFIX_005B == "2")
# State_highway<- filter(WI_interesting_new, ROUTE_PREFIX_005B == "3")
# County_highway<- filter(WI_interesting_new, ROUTE_PREFIX_005B == "4")
# City_street<- filter(WI_interesting_new, ROUTE_PREFIX_005B == "5")
# Federal_lands_road<- filter(WI_interesting_new, ROUTE_PREFIX_005B == "6")
# State_lands_road<- filter(WI_interesting_new, ROUTE_PREFIX_005B == "7")
# Other<- filter(WI_interesting_new, ROUTE_PREFIX_005B == "8")


# means of conditions by road

# mean(Interstate_highway$DECK_COND_058,na.rm=TRUE)
# mean(U.S._numbered_highway$DECK_COND_058,na.rm=TRUE)
# mean(State_highway$DECK_COND_058,na.rm=TRUE)
# mean(County_highway$DECK_COND_058,na.rm=TRUE)
# mean(City_street$DECK_COND_058,na.rm=TRUE)
# mean(Federal_lands_road$DECK_COND_058,na.rm=TRUE)
# mean(State_lands_road$DECK_COND_058,na.rm=TRUE)
# mean(Other$DECK_COND_058,na.rm=TRUE)
```

``` r
WI_Bridges_old <- fread("https://www.fhwa.dot.gov/bridge/nbi/2000/delimited/WI00.txt")


dataFrame_WI_old <- WI_Bridges_old %>% 
  as_tibble()


WI_interesting_old <- dataFrame_WI_old[,c(1:2,4 ,67:69, 27, 111)]
head(WI_interesting_old)
```

    ## # A tibble: 6 x 8
    ##   STATE_CODE_001 STRUCTURE_NUMBE… ROUTE_PREFIX_00… DECK_COND_058
    ##            <int> <chr>                       <int> <chr>        
    ## 1             55 00000000000F001                 6 4            
    ## 2             55 00000000000F301                 6 5            
    ## 3             55 00000000000F303                 6 6            
    ## 4             55 00000000000F309                 6 7            
    ## 5             55 00000000000F310                 6 4            
    ## 6             55 00000000000F311                 6 7            
    ## # … with 4 more variables: SUPERSTRUCTURE_COND_059 <chr>,
    ## #   SUBSTRUCTURE_COND_060 <chr>, YEAR_BUILT_027 <int>,
    ## #   PERCENT_ADT_TRUCK_109 <int>

``` r
WI_interesting_old <- na_if(WI_interesting_old, "N")

WI_interesting_old[, 3] <- sapply(WI_interesting_old[, 3], as.factor)

WI_interesting_old[, 4:6] <- sapply(WI_interesting_old[, c(4:6)], as.numeric, na.rm = TRUE)




lm_old <- lm(DECK_COND_058 ~ PERCENT_ADT_TRUCK_109, data = WI_interesting_old)
lm_old2 <-lm(SUPERSTRUCTURE_COND_059 ~ PERCENT_ADT_TRUCK_109, data = WI_interesting_old)
lm_old3 <-lm(SUBSTRUCTURE_COND_060 ~ PERCENT_ADT_TRUCK_109, data = WI_interesting_old)

summary(lm_old)
```

    ## 
    ## Call:
    ## lm(formula = DECK_COND_058 ~ PERCENT_ADT_TRUCK_109, data = WI_interesting_old)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -5.7069 -0.7069  0.2931  1.2931  2.5924 
    ## 
    ## Coefficients:
    ##                        Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)            6.706912   0.014475 463.357  < 2e-16 ***
    ## PERCENT_ADT_TRUCK_109 -0.007484   0.001844  -4.058 4.98e-05 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 1.354 on 11763 degrees of freedom
    ##   (4159 observations deleted due to missingness)
    ## Multiple R-squared:  0.001398,   Adjusted R-squared:  0.001313 
    ## F-statistic: 16.47 on 1 and 11763 DF,  p-value: 4.976e-05

``` r
summary(lm_old2)
```

    ## 
    ## Call:
    ## lm(formula = SUPERSTRUCTURE_COND_059 ~ PERCENT_ADT_TRUCK_109, 
    ##     data = WI_interesting_old)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -5.8551 -0.8551  0.1449  1.1449  2.1449 
    ## 
    ## Coefficients:
    ##                       Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)           6.855082   0.014742 464.999   <2e-16 ***
    ## PERCENT_ADT_TRUCK_109 0.001208   0.001896   0.637    0.524    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 1.366 on 11527 degrees of freedom
    ##   (4395 observations deleted due to missingness)
    ## Multiple R-squared:  3.522e-05,  Adjusted R-squared:  -5.153e-05 
    ## F-statistic: 0.406 on 1 and 11527 DF,  p-value: 0.524

``` r
summary(lm_old3)
```

    ## 
    ## Call:
    ## lm(formula = SUBSTRUCTURE_COND_060 ~ PERCENT_ADT_TRUCK_109, data = WI_interesting_old)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -5.7579 -0.7579  0.2421  1.2421  2.2421 
    ## 
    ## Coefficients:
    ##                       Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)           6.757917   0.014954 451.902   <2e-16 ***
    ## PERCENT_ADT_TRUCK_109 0.001985   0.001923   1.032    0.302    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 1.385 on 11527 degrees of freedom
    ##   (4395 observations deleted due to missingness)
    ## Multiple R-squared:  9.238e-05,  Adjusted R-squared:  5.633e-06 
    ## F-statistic: 1.065 on 1 and 11527 DF,  p-value: 0.3021

``` r
# Filtered based on type of road
# 
# WI_interesting_old <- arrange(WI_interesting_old,ROUTE_PREFIX_005B)
# Interstate_highway_old <- filter(WI_interesting_old, ROUTE_PREFIX_005B == "1")
# U.S._numbered_highway_old<- filter(WI_interesting_old, ROUTE_PREFIX_005B == "2")
# State_highway_old<- filter(WI_interesting_old, ROUTE_PREFIX_005B == "3")
# County_highway_old<- filter(WI_interesting_old, ROUTE_PREFIX_005B == "4")
# City_street_old<- filter(WI_interesting_old, ROUTE_PREFIX_005B == "5")
# Federal_lands_road_old<- filter(WI_interesting_old, ROUTE_PREFIX_005B == "6")
# State_lands_road_old<- filter(WI_interesting_old, ROUTE_PREFIX_005B == "7")
# Other_old<- filter(WI_interesting_old, ROUTE_PREFIX_005B == "8")



# means of conditions by road

# mean(Interstate_highway_old$DECK_COND_058,na.rm=TRUE)
# mean(U.S._numbered_highway_old$DECK_COND_058,na.rm=TRUE)
# mean(State_highway_old$DECK_COND_058,na.rm=TRUE)
# mean(County_highway_old$DECK_COND_058,na.rm=TRUE)
# mean(City_street_old$DECK_COND_058,na.rm=TRUE)
# mean(Federal_lands_road_old$DECK_COND_058,na.rm=TRUE)
# mean(State_lands_road_old$DECK_COND_058,na.rm=TRUE)
# mean(Other_old$DECK_COND_058,na.rm=TRUE)
```

``` r
Y2K_new <- filter(WI_interesting_new,YEAR_BUILT_027 == "1999")

deck_condition_in_2020 <- mean(Y2K_new$DECK_COND_058, na.rm=TRUE)



Y2K = filter(WI_interesting_old,YEAR_BUILT_027 == "1999")

deck_condition_in_2000 <- mean(Y2K$DECK_COND_058, na.rm=TRUE)


cat("The mean deck condition for bridges built in 1999 in the year 2000 was" ,
    deck_condition_in_2000, "and the mean deck 
    condition for bridges that were built in 
    the year 1999 in 2020 was", deck_condition_in_2020)
```

    ## The mean deck condition for bridges built in 1999 in the year 2000 was 8.407895 and the mean deck 
    ##     condition for bridges that were built in 
    ##     the year 1999 in 2020 was 6.95122
