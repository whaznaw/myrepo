HW1
================
William Haznaw
9/21/2021

html\_document github\_document

1)  compile git and HTML
2)  include link to github
3)  do str(data) and some plot to show
data

### I did Two years of Wisconsin Bridges so this is 2020

``` r
WI_Bridges_new <- fread("https://www.fhwa.dot.gov/bridge/nbi/2020/delimited/WI20.txt")
str(WI_Bridges_new)
```

    ## Classes 'data.table' and 'data.frame':   14271 obs. of  123 variables:
    ##  $ STATE_CODE_001         : int  55 55 55 55 55 55 55 55 55 55 ...
    ##  $ STRUCTURE_NUMBER_008   : chr  "00000000000F303" "00000000000F304" "00000000000F310" "00000000000F311" ...
    ##  $ RECORD_TYPE_005A       : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ ROUTE_PREFIX_005B      : int  6 6 6 6 6 6 6 6 6 6 ...
    ##  $ SERVICE_LEVEL_005C     : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ ROUTE_NUMBER_005D      : chr  "00010" "01015" "00024" "00021" ...
    ##  $ DIRECTION_005E         : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ HIGHWAY_DISTRICT_002   : chr  "07" "07" "06" "03" ...
    ##  $ COUNTY_CODE_003        : int  51 51 115 115 3 3 3 115 3 3 ...
    ##  $ PLACE_CODE_004         : int  0 0 0 0 0 59450 59450 0 0 0 ...
    ##  $ FEATURES_DESC_006A     : chr  "'FLAMBEAU BEAR RIVER'" "'TROUT RIVER'" "'WEST BRANCH RED RIVER'" "'RED  RIVER'" ...
    ##  $ CRITICAL_FACILITY_006B : logi  NA NA NA NA NA NA ...
    ##  $ FACILITY_CARRIED_007   : chr  "'IRR BIA RTE 10'" "'IRR ROUTE 15'" "'IRR BIA RTE  24'" "'IRR BIA RTE  21'" ...
    ##  $ LOCATION_009           : chr  "'6KM NW OF LAC DU FLAMBEAU'" "'LAC DU FLAMBEAU'" "'10 KM  NE  OF  BOWLER'" "'13 KM  NE  OF  BOWLER'" ...
    ##  $ MIN_VERT_CLR_010       : num  100 100 100 100 100 ...
    ##  $ KILOPOINT_011          : num  0.161 1.5 2.737 8.372 3.22 ...
    ##  $ BASE_HWY_NETWORK_012   : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ LRS_INV_ROUTE_013A     : chr  "0000000000" "0000000000" "0000000000" "0000000000" ...
    ##  $ SUBROUTE_NO_013B       : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ LAT_016                : int  45585542 46011583 44542955 44563600 46360600 46371020 46365101 44551710 46280263 46290272 ...
    ##  $ LONG_017               : num  89561330 89454321 88544561 88554200 90390000 ...
    ##  $ DETOUR_KILOS_019       : int  8 17 3 16 2 199 199 8 24 24 ...
    ##  $ TOLL_020               : int  3 3 3 3 3 3 3 3 3 3 ...
    ##  $ MAINTENANCE_021        : int  62 62 62 62 62 62 62 62 62 62 ...
    ##  $ OWNER_022              : int  62 62 62 62 62 62 62 62 62 62 ...
    ##  $ FUNCTIONAL_CLASS_026   : int  9 9 9 9 9 9 9 9 9 9 ...
    ##  $ YEAR_BUILT_027         : int  1932 1974 1948 1979 1977 1980 1980 1994 1999 2006 ...
    ##  $ TRAFFIC_LANES_ON_028A  : int  2 1 2 2 2 2 2 2 2 2 ...
    ##  $ TRAFFIC_LANES_UND_028B : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ ADT_029                : int  50 20 100 150 300 20 30 450 50 50 ...
    ##  $ YEAR_ADT_030           : int  2019 2019 2018 2018 2018 2019 2019 2018 2019 2018 ...
    ##  $ DESIGN_LOAD_031        : chr  "0" "0" "0" "4" ...
    ##  $ APPR_WIDTH_MT_032      : num  7.9 3.7 6.7 10.4 8.8 9.1 9.1 11.6 7.3 7.3 ...
    ##  $ MEDIAN_CODE_033        : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ DEGREES_SKEW_034       : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ STRUCTURE_FLARED_035   : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ RAILINGS_036A          : chr  "1" "0" "0" "1" ...
    ##  $ TRANSITIONS_036B       : chr  "0" "0" "1" "1" ...
    ##  $ APPR_RAIL_036C         : chr  "0" "0" "1" "1" ...
    ##  $ APPR_RAIL_END_036D     : chr  "0" "0" "1" "0" ...
    ##  $ HISTORY_037            : int  5 5 5 5 5 5 5 5 5 5 ...
    ##  $ NAVIGATION_038         : chr  "0" "0" "0" "0" ...
    ##  $ NAV_VERT_CLR_MT_039    : num  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ NAV_HORR_CLR_MT_040    : num  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ OPEN_CLOSED_POSTED_041 : chr  "B" "B" "P" "A" ...
    ##  $ SERVICE_ON_042A        : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ SERVICE_UND_042B       : int  5 5 5 5 5 5 5 5 5 5 ...
    ##  $ STRUCTURE_KIND_043A    : int  7 7 7 5 2 5 5 5 2 5 ...
    ##  $ STRUCTURE_TYPE_043B    : int  1 3 1 2 1 5 5 2 1 2 ...
    ##  $ APPR_KIND_044A         : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ APPR_TYPE_044B         : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ MAIN_UNIT_SPANS_045    : int  2 2 1 2 3 2 2 1 3 3 ...
    ##  $ APPR_SPANS_046         : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ HORR_CLR_MT_047        : num  7.5 3.7 6.7 9.1 8.6 8.5 8.5 9.1 7.3 6.7 ...
    ##  $ MAX_SPAN_LEN_MT_048    : num  5.5 7.3 6.1 20.4 7.6 9.1 8.8 19.5 13.4 15.2 ...
    ##  $ STRUCTURE_LEN_MT_049   : num  11.3 14.6 6.1 40.5 21 18.6 18.3 19.5 32.9 21.8 ...
    ##  $ LEFT_CURB_MT_050A      : num  0.2 0 0 0 0 0 0 0 0 0 ...
    ##  $ RIGHT_CURB_MT_050B     : num  0.2 0 0 0 0 0 0 0 0 0 ...
    ##  $ ROADWAY_WIDTH_MT_051   : num  7.5 3.7 7 9.1 8.6 8.5 8.5 9.1 7.3 7.3 ...
    ##  $ DECK_WIDTH_MT_052      : num  7.9 3.7 7.8 10.3 10.5 9.1 9.1 10.4 7.9 7.9 ...
    ##  $ VERT_CLR_OVER_MT_053   : num  100 100 100 99.9 99.9 ...
    ##  $ VERT_CLR_UND_REF_054A  : chr  "N" "N" "N" "N" ...
    ##  $ VERT_CLR_UND_054B      : num  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ LAT_UND_REF_055A       : chr  "N" "N" "N" "N" ...
    ##  $ LAT_UND_MT_055B        : num  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ LEFT_LAT_UND_MT_056    : num  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ DECK_COND_058          : chr  "4" "5" "5" "5" ...
    ##  $ SUPERSTRUCTURE_COND_059: chr  "5" "5" "5" "7" ...
    ##  $ SUBSTRUCTURE_COND_060  : chr  "5" "4" "7" "8" ...
    ##  $ CHANNEL_COND_061       : chr  "4" "7" "5" "6" ...
    ##  $ CULVERT_COND_062       : chr  "N" "N" "N" "N" ...
    ##  $ OPR_RATING_METH_063    : chr  "2" "2" "2" "1" ...
    ##  $ OPERATING_RATING_064   : num  24.7 7.3 21.6 31.5 40.6 47.7 47.7 31.2 70.2 53.9 ...
    ##  $ INV_RATING_METH_065    : chr  "2" "2" "2" "1" ...
    ##  $ INVENTORY_RATING_066   : num  17.8 5 15.1 23.1 29.7 35.8 35.8 22.9 42.4 42.5 ...
    ##  $ STRUCTURAL_EVAL_067    : chr  "5" "2" "4" "6" ...
    ##  $ DECK_GEOMETRY_EVAL_068 : chr  "6" "4" "5" "6" ...
    ##  $ UNDCLRENCE_EVAL_069    : chr  "N" "N" "N" "N" ...
    ##  $ POSTING_EVAL_070       : int  4 4 1 5 5 5 5 5 5 5 ...
    ##  $ WATERWAY_EVAL_071      : chr  "4" "7" "5" "8" ...
    ##  $ APPR_ROAD_EVAL_072     : int  4 3 6 6 6 8 8 6 6 6 ...
    ##  $ WORK_PROPOSED_075A     : int  31 31 31 NA NA NA NA NA 31 NA ...
    ##  $ WORK_DONE_BY_075B      : int  1 1 1 NA NA NA NA NA 1 NA ...
    ##  $ IMP_LEN_MT_076         : num  11.5 15 11 0 0 0 0 0 40 0 ...
    ##  $ DATE_OF_INSPECT_090    : int  919 919 918 918 918 819 819 918 819 918 ...
    ##  $ INSPECT_FREQ_MONTHS_091: int  24 24 24 24 24 24 24 24 24 24 ...
    ##  $ FRACTURE_092A          : chr  "N" "N" "N" "N" ...
    ##  $ UNDWATER_LOOK_SEE_092B : chr  "N" "N" "N" "N" ...
    ##  $ SPEC_INSPECT_092C      : chr  "N" "N" "N" "N" ...
    ##  $ FRACTURE_LAST_DATE_093A: int  NA NA NA NA NA NA NA NA NA NA ...
    ##  $ UNDWATER_LAST_DATE_093B: int  NA NA NA NA NA 819 819 NA 819 NA ...
    ##  $ SPEC_LAST_DATE_093C    : int  NA NA NA NA NA NA NA NA NA NA ...
    ##  $ BRIDGE_IMP_COST_094    : int  402 187 0 0 0 0 0 0 0 0 ...
    ##  $ ROADWAY_IMP_COST_095   : int  50 22 0 0 0 0 0 0 0 0 ...
    ##  $ TOTAL_IMP_COST_096     : int  452 299 460 0 0 0 0 0 53 0 ...
    ##  $ YEAR_OF_IMP_097        : int  2019 2019 2018 2018 2018 2019 2019 2018 2019 2018 ...
    ##  $ OTHER_STATE_CODE_098A  : int  NA NA NA NA NA NA NA NA NA NA ...
    ##  $ OTHER_STATE_PCNT_098B  : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ OTHR_STATE_STRUC_NO_099: chr  "" "" "" "" ...
    ##   [list output truncated]
    ##  - attr(*, ".internal.selfref")=<externalptr>

``` r
#colnames(WI_Bridges_new)


dataFrame_WI <- WI_Bridges_new %>% 
  as_tibble()


WI_interesting_new <- dataFrame_WI[,c(1:2,4 ,67:69, 27, 111)]
head(WI_interesting_new)
```

    ## # A tibble: 6 x 8
    ##   STATE_CODE_001 STRUCTURE_NUMBE??? ROUTE_PREFIX_00??? DECK_COND_058
    ##            <int> <chr>                       <int> <chr>        
    ## 1             55 00000000000F303                 6 4            
    ## 2             55 00000000000F304                 6 5            
    ## 3             55 00000000000F310                 6 5            
    ## 4             55 00000000000F311                 6 5            
    ## 5             55 00000000000F315                 6 5            
    ## 6             55 00000000000F317                 6 7            
    ## # ??? with 4 more variables: SUPERSTRUCTURE_COND_059 <chr>,
    ## #   SUBSTRUCTURE_COND_060 <chr>, YEAR_BUILT_027 <int>,
    ## #   PERCENT_ADT_TRUCK_109 <int>

``` r
WI_interesting_new <- na_if(WI_interesting_new, "N")

WI_interesting_new[, 3] <- sapply(WI_interesting_new[, 3], as.factor)

WI_interesting_new[, 4:6] <- sapply(WI_interesting_new[, c(4:6)], 
                                    as.numeric, na.rm = TRUE)


hist(WI_interesting_new$DECK_COND_058)
```

![](HW1_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

``` r
hist(WI_interesting_new$SUPERSTRUCTURE_COND_059)
```

![](HW1_files/figure-gfm/unnamed-chunk-2-2.png)<!-- -->

``` r
hist(WI_interesting_new$SUBSTRUCTURE_COND_060)
```

![](HW1_files/figure-gfm/unnamed-chunk-2-3.png)<!-- -->

``` r
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

### Here is the older data from 2000

``` r
WI_Bridges_old <- fread("https://www.fhwa.dot.gov/bridge/nbi/2000/delimited/WI00.txt")
str(WI_Bridges_old)
```

    ## Classes 'data.table' and 'data.frame':   15924 obs. of  134 variables:
    ##  $ STATE_CODE_001         : int  55 55 55 55 55 55 55 55 55 55 ...
    ##  $ STRUCTURE_NUMBER_008   : chr  "00000000000F001" "00000000000F301" "00000000000F303" "00000000000F309" ...
    ##  $ RECORD_TYPE_005A       : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ ROUTE_PREFIX_005B      : int  6 6 6 6 6 6 6 6 6 6 ...
    ##  $ SERVICE_LEVEL_005C     : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ ROUTE_NUMBER_005D      : int  59 10 10 22 24 21 9 52 52 21 ...
    ##  $ DIRECTION_005E         : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ HIGHWAY_DISTRICT_002   : int  3 7 7 3 6 3 8 8 8 3 ...
    ##  $ COUNTY_CODE_003        : int  78 51 51 115 115 115 3 3 3 115 ...
    ##  $ PLACE_CODE_004         : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ FEATURES_DESC_006A     : chr  "'WOLF RIVER              '" "'FLAMBEAU    BEAR   RIVER'" "'FLAMBEAU   BEAR    RIVER'" "'RED       RIVER         '" ...
    ##  $ CRITICAL_FACILITY_006B : chr  "" "" "" "" ...
    ##  $ FACILITY_CARRIED_007   : chr  "'IRR BIA RTE 59    '" "'IRR BIA RTE     10'" "'INDIAN RTE      10'" "'IRR BIA RTE     22'" ...
    ##  $ LOCATION_009           : chr  "'IN KESHENA               '" "'17KM N OF LAC DU FLAMBEAU'" "'6KM NW OF LAC DU FLAMBEAU'" "'16 KM     NW  OF  GRESHAM'" ...
    ##  $ MIN_VERT_CLR_010       : num  100 100 100 100 100 ...
    ##  $ KILOPOINT_011          : num  4.991 12.558 0.161 3.542 2.737 ...
    ##  $ BASE_HWY_NETWORK_012   : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ LRS_INV_ROUTE_013A     : chr  "0000000000" "0000000000" "0000000000" "0000000000" ...
    ##  $ SUBROUTE_NO_013B       : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ LAT_016                : int  44530000 46025400 45585400 44551200 44543000 44563600 46360600 46371800 46365400 44551800 ...
    ##  $ LONG_017               : int  88382400 89590000 89560600 88533600 88544200 88554200 90390000 90420000 90414200 88562400 ...
    ##  $ DETOUR_KILOS_019       : int  3 24 8 23 3 16 2 199 199 8 ...
    ##  $ TOLL_020               : int  3 3 3 3 3 3 3 3 3 3 ...
    ##  $ MAINTENANCE_021        : int  62 62 62 62 62 62 62 62 62 62 ...
    ##  $ OWNER_022              : int  62 62 62 62 62 62 62 62 62 62 ...
    ##  $ FUNCTIONAL_CLASS_026   : int  19 9 9 9 9 9 9 9 9 9 ...
    ##  $ YEAR_BUILT_027         : int  1967 1932 1932 1952 1948 1979 1977 1980 1980 1984 ...
    ##  $ TRAFFIC_LANES_ON_028A  : int  2 2 2 2 2 2 2 2 2 2 ...
    ##  $ TRAFFIC_LANES_UND_028B : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ ADT_029                : int  500 50 50 250 100 150 300 80 80 450 ...
    ##  $ YEAR_ADT_030           : int  1998 1998 1998 1998 1998 1998 1998 1998 1998 1998 ...
    ##  $ DESIGN_LOAD_031        : int  4 2 0 0 0 4 5 6 6 4 ...
    ##  $ APPR_WIDTH_MT_032      : num  11.9 6.7 7.9 9.1 6.7 10.4 8.8 9.1 9.1 11.6 ...
    ##  $ MEDIAN_CODE_033        : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ DEGREES_SKEW_034       : int  10 0 0 0 0 0 0 0 0 0 ...
    ##  $ STRUCTURE_FLARED_035   : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ RAILINGS_036A          : chr  "1" "0" "0" "0" ...
    ##  $ TRANSITIONS_036B       : chr  "1" "0" "0" "0" ...
    ##  $ APPR_RAIL_036C         : chr  "1" "0" "0" "0" ...
    ##  $ APPR_RAIL_END_036D     : chr  "1" "0" "0" "0" ...
    ##  $ HISTORY_037            : int  5 5 5 5 5 5 5 5 5 5 ...
    ##  $ NAVIGATION_038         : chr  "N" "0" "0" "N" ...
    ##  $ NAV_VERT_CLR_MT_039    : num  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ NAV_HORR_CLR_MT_040    : num  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ OPEN_CLOSED_POSTED_041 : chr  "P" "A" "A" "A" ...
    ##  $ SERVICE_ON_042A        : int  5 1 1 1 1 1 5 1 1 1 ...
    ##  $ SERVICE_UND_042B       : int  5 5 5 5 5 5 5 5 5 5 ...
    ##  $ STRUCTURE_KIND_043A    : int  2 7 7 3 7 5 2 5 5 5 ...
    ##  $ STRUCTURE_TYPE_043B    : int  1 1 1 2 1 2 1 5 5 2 ...
    ##  $ APPR_KIND_044A         : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ APPR_TYPE_044B         : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ MAIN_UNIT_SPANS_045    : int  3 1 2 1 1 2 3 2 2 1 ...
    ##  $ APPR_SPANS_046         : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ HORR_CLR_MT_047        : num  9.6 6.7 7.5 6.7 6.7 9.1 8.6 8.5 8.5 9.1 ...
    ##  $ MAX_SPAN_LEN_MT_048    : num  22.3 6.1 5.5 9.1 6.1 20.4 7.6 9.1 8.8 19.5 ...
    ##  $ STRUCTURE_LEN_MT_049   : num  56.4 6.4 11.3 9.7 6.4 40.5 21 18.6 18.3 20.4 ...
    ##  $ LEFT_CURB_MT_050A      : num  0.2 0.2 0.2 0.3 0.2 0.6 0 0 0 0.6 ...
    ##  $ RIGHT_CURB_MT_050B     : num  1.5 0.2 0.2 0.3 0.2 0.6 1.2 0 0 0.6 ...
    ##  $ ROADWAY_WIDTH_MT_051   : num  9.6 7.3 7.5 6.7 7 9.1 8.6 8.5 8.5 9.1 ...
    ##  $ DECK_WIDTH_MT_052      : num  12 7.7 7.9 7.3 7.8 10.3 10.5 9.1 9.1 10.4 ...
    ##  $ VERT_CLR_OVER_MT_053   : num  100 100 100 100 100 ...
    ##  $ VERT_CLR_UND_REF_054A  : chr  "N" "N" "N" "N" ...
    ##  $ VERT_CLR_UND_054B      : num  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ LAT_UND_REF_055A       : chr  "N" "N" "N" "N" ...
    ##  $ LAT_UND_MT_055B        : num  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ LEFT_LAT_UND_MT_056    : num  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ DECK_COND_058          : chr  "4" "5" "6" "7" ...
    ##  $ SUPERSTRUCTURE_COND_059: chr  "4" "5" "6" "6" ...
    ##  $ SUBSTRUCTURE_COND_060  : chr  "5" "4" "5" "4" ...
    ##  $ CHANNEL_COND_061       : chr  "8" "6" "6" "8" ...
    ##  $ CULVERT_COND_062       : chr  "N" "N" "N" "N" ...
    ##  $ OPR_RATING_METH_063    : int  1 1 1 1 1 1 1 1 1 2 ...
    ##  $ OPERATING_RATING_064   : num  26.3 32.6 26.3 33.6 34.2 30.8 40 47.2 47.2 30.9 ...
    ##  $ INV_RATING_METH_065    : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ INVENTORY_RATING_066   : num  12.7 23.6 19.1 20 24.9 22.7 29.1 35.4 35.4 22.7 ...
    ##  $ STRUCTURAL_EVAL_067    : int  4 4 5 4 4 6 6 4 4 6 ...
    ##  $ DECK_GEOMETRY_EVAL_068 : chr  "6" "6" "6" "4" ...
    ##  $ UNDCLRENCE_EVAL_069    : chr  "N" "N" "N" "N" ...
    ##  $ POSTING_EVAL_070       : int  0 2 0 2 2 2 4 5 5 2 ...
    ##  $ WATERWAY_EVAL_071      : chr  "8" "6" "7" "6" ...
    ##  $ APPR_ROAD_EVAL_072     : int  6 6 7 8 8 6 6 6 8 6 ...
    ##  $ WORK_PROPOSED_075A     : int  31 31 NA 31 37 NA NA 35 35 NA ...
    ##  $ WORK_DONE_BY_075B      : int  1 1 NA 1 1 NA NA 1 1 NA ...
    ##  $ IMP_LEN_MT_076         : num  58 7.5 0 9.7 6.4 0 0 18.6 18.3 0 ...
    ##  $ DATE_OF_INSPECT_090    : int  1198 1098 1098 1198 1198 1198 1098 1098 1098 1198 ...
    ##  $ INSPECT_FREQ_MONTHS_091: int  12 24 24 24 24 24 24 24 24 24 ...
    ##  $ FRACTURE_092A          : chr  "N" "N" "N" "N" ...
    ##  $ UNDWATER_LOOK_SEE_092B : chr  "N" "N" "N" "N" ...
    ##  $ SPEC_INSPECT_092C      : chr  "N" "N" "N" "N" ...
    ##  $ FRACTURE_LAST_DATE_093A: int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ UNDWATER_LAST_DATE_093B: int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ SPEC_LAST_DATE_093C    : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ BRIDGE_IMP_COST_094    : int  375 200 0 200 40 0 0 30 30 0 ...
    ##  $ ROADWAY_IMP_COST_095   : int  25 50 0 20 1 0 0 20 20 0 ...
    ##  $ TOTAL_IMP_COST_096     : int  500 285 0 285 50 0 0 50 50 0 ...
    ##  $ YEAR_OF_IMP_097        : int  1998 1998 2000 1998 1998 2000 2000 1998 1998 2000 ...
    ##  $ OTHER_STATE_CODE_098A  : int  NA NA NA NA NA NA NA NA NA NA ...
    ##  $ OTHER_STATE_PCNT_098B  : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ OTHR_STATE_STRUC_NO_099: chr  "" "" "" "" ...
    ##   [list output truncated]
    ##  - attr(*, ".internal.selfref")=<externalptr>

``` r
dataFrame_WI_old <- WI_Bridges_old %>% 
  as_tibble()


WI_interesting_old <- dataFrame_WI_old[,c(1:2,4 ,67:69, 27, 111)]
head(WI_interesting_old)
```

    ## # A tibble: 6 x 8
    ##   STATE_CODE_001 STRUCTURE_NUMBE??? ROUTE_PREFIX_00??? DECK_COND_058
    ##            <int> <chr>                       <int> <chr>        
    ## 1             55 00000000000F001                 6 4            
    ## 2             55 00000000000F301                 6 5            
    ## 3             55 00000000000F303                 6 6            
    ## 4             55 00000000000F309                 6 7            
    ## 5             55 00000000000F310                 6 4            
    ## 6             55 00000000000F311                 6 7            
    ## # ??? with 4 more variables: SUPERSTRUCTURE_COND_059 <chr>,
    ## #   SUBSTRUCTURE_COND_060 <chr>, YEAR_BUILT_027 <int>,
    ## #   PERCENT_ADT_TRUCK_109 <int>

``` r
WI_interesting_old <- na_if(WI_interesting_old, "N")

WI_interesting_old[, 3] <- sapply(WI_interesting_old[, 3], as.factor)

WI_interesting_old[, 4:6] <- sapply(WI_interesting_old[, c(4:6)], as.numeric, na.rm = TRUE)


hist(WI_interesting_old$DECK_COND_058)
```

![](HW1_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

``` r
hist(WI_interesting_old$SUPERSTRUCTURE_COND_059)
```

![](HW1_files/figure-gfm/unnamed-chunk-3-2.png)<!-- -->

``` r
hist(WI_interesting_old$SUBSTRUCTURE_COND_060)
```

![](HW1_files/figure-gfm/unnamed-chunk-3-3.png)<!-- -->

``` r
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
