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
head(WI_Bridges_new)
```

    ##    STATE_CODE_001 STRUCTURE_NUMBER_008 RECORD_TYPE_005A ROUTE_PREFIX_005B
    ## 1:             55      00000000000F303                1                 6
    ## 2:             55      00000000000F304                1                 6
    ## 3:             55      00000000000F310                1                 6
    ## 4:             55      00000000000F311                1                 6
    ## 5:             55      00000000000F315                1                 6
    ## 6:             55      00000000000F317                1                 6
    ##    SERVICE_LEVEL_005C ROUTE_NUMBER_005D DIRECTION_005E HIGHWAY_DISTRICT_002
    ## 1:                  1             00010              0                   07
    ## 2:                  1             01015              0                   07
    ## 3:                  1             00024              0                   06
    ## 4:                  1             00021              0                   03
    ## 5:                  1             00009              0                   08
    ## 6:                  1             00052              0                   08
    ##    COUNTY_CODE_003 PLACE_CODE_004      FEATURES_DESC_006A
    ## 1:              51              0   'FLAMBEAU BEAR RIVER'
    ## 2:              51              0           'TROUT RIVER'
    ## 3:             115              0 'WEST BRANCH RED RIVER'
    ## 4:             115              0            'RED  RIVER'
    ## 5:               3              0        'DENOMIE  CREEK'
    ## 6:               3          59450        'KAKAGON  RIVER'
    ##    CRITICAL_FACILITY_006B FACILITY_CARRIED_007                LOCATION_009
    ## 1:                     NA     'IRR BIA RTE 10' '6KM NW OF LAC DU FLAMBEAU'
    ## 2:                     NA       'IRR ROUTE 15'           'LAC DU FLAMBEAU'
    ## 3:                     NA    'IRR BIA RTE  24'     '10 KM  NE  OF  BOWLER'
    ## 4:                     NA    'IRR BIA RTE  21'     '13 KM  NE  OF  BOWLER'
    ## 5:                     NA     'IRR BIA RTE  9'    '3 KM  EAST  OF  ODANAH'
    ## 6:                     NA    'IRR BIA RTE  52'      '3 KM  NW  OF  ODANAH'
    ##    MIN_VERT_CLR_010 KILOPOINT_011 BASE_HWY_NETWORK_012 LRS_INV_ROUTE_013A
    ## 1:            99.99         0.161                    0         0000000000
    ## 2:            99.99         1.500                    0         0000000000
    ## 3:            99.99         2.737                    0         0000000000
    ## 4:            99.99         8.372                    0         0000000000
    ## 5:            99.99         3.220                    0         0000000000
    ## 6:            99.99         2.737                    0         0000000000
    ##    SUBROUTE_NO_013B  LAT_016 LONG_017 DETOUR_KILOS_019 TOLL_020 MAINTENANCE_021
    ## 1:                0 45585542 89561330                8        3              62
    ## 2:                0 46011583 89454321               17        3              62
    ## 3:                0 44542955 88544561                3        3              62
    ## 4:                0 44563600 88554200               16        3              62
    ## 5:                0 46360600 90390000                2        3              62
    ## 6:                0 46371020 90421190              199        3              62
    ##    OWNER_022 FUNCTIONAL_CLASS_026 YEAR_BUILT_027 TRAFFIC_LANES_ON_028A
    ## 1:        62                    9           1932                     2
    ## 2:        62                    9           1974                     1
    ## 3:        62                    9           1948                     2
    ## 4:        62                    9           1979                     2
    ## 5:        62                    9           1977                     2
    ## 6:        62                    9           1980                     2
    ##    TRAFFIC_LANES_UND_028B ADT_029 YEAR_ADT_030 DESIGN_LOAD_031
    ## 1:                      0      50         2019               0
    ## 2:                      0      20         2019               0
    ## 3:                      0     100         2018               0
    ## 4:                      0     150         2018               4
    ## 5:                      0     300         2018               5
    ## 6:                      0      20         2019               6
    ##    APPR_WIDTH_MT_032 MEDIAN_CODE_033 DEGREES_SKEW_034 STRUCTURE_FLARED_035
    ## 1:               7.9               0                0                    0
    ## 2:               3.7               0                0                    0
    ## 3:               6.7               0                0                    0
    ## 4:              10.4               0                0                    0
    ## 5:               8.8               0                0                    0
    ## 6:               9.1               0                0                    0
    ##    RAILINGS_036A TRANSITIONS_036B APPR_RAIL_036C APPR_RAIL_END_036D HISTORY_037
    ## 1:             1                0              0                  0           5
    ## 2:             0                0              0                  0           5
    ## 3:             0                1              1                  1           5
    ## 4:             1                1              1                  0           5
    ## 5:             0                0              0                  1           5
    ## 6:             1                0              1                  1           5
    ##    NAVIGATION_038 NAV_VERT_CLR_MT_039 NAV_HORR_CLR_MT_040
    ## 1:              0                   0                   0
    ## 2:              0                   0                   0
    ## 3:              0                   0                   0
    ## 4:              0                   0                   0
    ## 5:              N                   0                   0
    ## 6:              N                   0                   0
    ##    OPEN_CLOSED_POSTED_041 SERVICE_ON_042A SERVICE_UND_042B STRUCTURE_KIND_043A
    ## 1:                      B               1                5                   7
    ## 2:                      B               1                5                   7
    ## 3:                      P               1                5                   7
    ## 4:                      A               1                5                   5
    ## 5:                      A               1                5                   2
    ## 6:                      A               1                5                   5
    ##    STRUCTURE_TYPE_043B APPR_KIND_044A APPR_TYPE_044B MAIN_UNIT_SPANS_045
    ## 1:                   1              0              0                   2
    ## 2:                   3              0              0                   2
    ## 3:                   1              0              0                   1
    ## 4:                   2              0              0                   2
    ## 5:                   1              0              0                   3
    ## 6:                   5              0              0                   2
    ##    APPR_SPANS_046 HORR_CLR_MT_047 MAX_SPAN_LEN_MT_048 STRUCTURE_LEN_MT_049
    ## 1:              0             7.5                 5.5                 11.3
    ## 2:              0             3.7                 7.3                 14.6
    ## 3:              0             6.7                 6.1                  6.1
    ## 4:              0             9.1                20.4                 40.5
    ## 5:              0             8.6                 7.6                 21.0
    ## 6:              0             8.5                 9.1                 18.6
    ##    LEFT_CURB_MT_050A RIGHT_CURB_MT_050B ROADWAY_WIDTH_MT_051 DECK_WIDTH_MT_052
    ## 1:               0.2                0.2                  7.5               7.9
    ## 2:               0.0                0.0                  3.7               3.7
    ## 3:               0.0                0.0                  7.0               7.8
    ## 4:               0.0                0.0                  9.1              10.3
    ## 5:               0.0                0.0                  8.6              10.5
    ## 6:               0.0                0.0                  8.5               9.1
    ##    VERT_CLR_OVER_MT_053 VERT_CLR_UND_REF_054A VERT_CLR_UND_054B
    ## 1:                99.99                     N                 0
    ## 2:                99.99                     N                 0
    ## 3:                99.99                     N                 0
    ## 4:                99.90                     N                 0
    ## 5:                99.90                     N                 0
    ## 6:                99.99                     N                 0
    ##    LAT_UND_REF_055A LAT_UND_MT_055B LEFT_LAT_UND_MT_056 DECK_COND_058
    ## 1:                N               0                   0             4
    ## 2:                N               0                   0             5
    ## 3:                N               0                   0             5
    ## 4:                N               0                   0             5
    ## 5:                N               0                   0             5
    ## 6:                N               0                   0             7
    ##    SUPERSTRUCTURE_COND_059 SUBSTRUCTURE_COND_060 CHANNEL_COND_061
    ## 1:                       5                     5                4
    ## 2:                       5                     4                7
    ## 3:                       5                     7                5
    ## 4:                       7                     8                6
    ## 5:                       5                     7                4
    ## 6:                       8                     7                7
    ##    CULVERT_COND_062 OPR_RATING_METH_063 OPERATING_RATING_064
    ## 1:                N                   2                 24.7
    ## 2:                N                   2                  7.3
    ## 3:                N                   2                 21.6
    ## 4:                N                   1                 31.5
    ## 5:                N                   1                 40.6
    ## 6:                N                   1                 47.7
    ##    INV_RATING_METH_065 INVENTORY_RATING_066 STRUCTURAL_EVAL_067
    ## 1:                   2                 17.8                   5
    ## 2:                   2                  5.0                   2
    ## 3:                   2                 15.1                   4
    ## 4:                   1                 23.1                   6
    ## 5:                   1                 29.7                   5
    ## 6:                   1                 35.8                   7
    ##    DECK_GEOMETRY_EVAL_068 UNDCLRENCE_EVAL_069 POSTING_EVAL_070
    ## 1:                      6                   N                4
    ## 2:                      4                   N                4
    ## 3:                      5                   N                1
    ## 4:                      6                   N                5
    ## 5:                      6                   N                5
    ## 6:                      7                   N                5
    ##    WATERWAY_EVAL_071 APPR_ROAD_EVAL_072 WORK_PROPOSED_075A WORK_DONE_BY_075B
    ## 1:                 4                  4                 31                 1
    ## 2:                 7                  3                 31                 1
    ## 3:                 5                  6                 31                 1
    ## 4:                 8                  6                 NA                NA
    ## 5:                 4                  6                 NA                NA
    ## 6:                 6                  8                 NA                NA
    ##    IMP_LEN_MT_076 DATE_OF_INSPECT_090 INSPECT_FREQ_MONTHS_091 FRACTURE_092A
    ## 1:           11.5                 919                      24             N
    ## 2:           15.0                 919                      24             N
    ## 3:           11.0                 918                      24             N
    ## 4:            0.0                 918                      24             N
    ## 5:            0.0                 918                      24             N
    ## 6:            0.0                 819                      24             N
    ##    UNDWATER_LOOK_SEE_092B SPEC_INSPECT_092C FRACTURE_LAST_DATE_093A
    ## 1:                      N                 N                      NA
    ## 2:                      N                 N                      NA
    ## 3:                      N                 N                      NA
    ## 4:                      N                 N                      NA
    ## 5:                      N                 N                      NA
    ## 6:                    Y60                 N                      NA
    ##    UNDWATER_LAST_DATE_093B SPEC_LAST_DATE_093C BRIDGE_IMP_COST_094
    ## 1:                      NA                  NA                 402
    ## 2:                      NA                  NA                 187
    ## 3:                      NA                  NA                   0
    ## 4:                      NA                  NA                   0
    ## 5:                      NA                  NA                   0
    ## 6:                     819                  NA                   0
    ##    ROADWAY_IMP_COST_095 TOTAL_IMP_COST_096 YEAR_OF_IMP_097
    ## 1:                   50                452            2019
    ## 2:                   22                299            2019
    ## 3:                    0                460            2018
    ## 4:                    0                  0            2018
    ## 5:                    0                  0            2018
    ## 6:                    0                  0            2019
    ##    OTHER_STATE_CODE_098A OTHER_STATE_PCNT_098B OTHR_STATE_STRUC_NO_099
    ## 1:                    NA                     0                        
    ## 2:                    NA                     0                        
    ## 3:                    NA                     0                        
    ## 4:                    NA                     0                        
    ## 5:                    NA                     0                        
    ## 6:                    NA                     0                        
    ##    STRAHNET_HIGHWAY_100 PARALLEL_STRUCTURE_101 TRAFFIC_DIRECTION_102
    ## 1:                    0                      N                     2
    ## 2:                    0                      N                     3
    ## 3:                    0                      N                     2
    ## 4:                    0                      N                     2
    ## 5:                    0                      N                     2
    ## 6:                    0                      N                     2
    ##    TEMP_STRUCTURE_103 HIGHWAY_SYSTEM_104 FEDERAL_LANDS_105
    ## 1:                 NA                  0                 1
    ## 2:                 NA                  0                 1
    ## 3:                 NA                  0                 1
    ## 4:                 NA                  0                 1
    ## 5:                 NA                  0                 1
    ## 6:                 NA                  0                 1
    ##    YEAR_RECONSTRUCTED_106 DECK_STRUCTURE_TYPE_107 SURFACE_TYPE_108A
    ## 1:                   1958                       8                 6
    ## 2:                   1994                       8                 7
    ## 3:                   1990                       8                 6
    ## 4:                      0                       1                 0
    ## 5:                      0                       1                 6
    ## 6:                   2003                       1                 1
    ##    MEMBRANE_TYPE_108B DECK_PROTECTION_108C PERCENT_ADT_TRUCK_109
    ## 1:                  0                    0                    25
    ## 2:                  0                    0                     0
    ## 3:                  0                    0                    15
    ## 4:                  0                    0                    20
    ## 5:                  0                    0                    10
    ## 6:                  0                    0                    10
    ##    NATIONAL_NETWORK_110 PIER_PROTECTION_111 BRIDGE_LEN_IND_112
    ## 1:                    0                  NA                  Y
    ## 2:                    0                  NA                  Y
    ## 3:                    0                  NA                  Y
    ## 4:                    0                  NA                  Y
    ## 5:                    0                  NA                  Y
    ## 6:                    0                  NA                  Y
    ##    SCOUR_CRITICAL_113 FUTURE_ADT_114 YEAR_OF_FUTURE_ADT_115 MIN_NAV_CLR_MT_116
    ## 1:                  8             60                   2039                  0
    ## 2:                  5             23                   2039                  0
    ## 3:                  8            117                   2038                  0
    ## 4:                  8            250                   2038                  0
    ## 5:                  8            500                   2038                  0
    ## 6:                  8             25                   2039                  0
    ##    FED_AGENCY SUBMITTED_BY BRIDGE_CONDITION LOWEST_RATING DECK_AREA
    ## 1:          Y           62                P             4     89.27
    ## 2:          Y           62                P             4     54.02
    ## 3:          Y           62                F             5     47.58
    ## 4:          Y           62                F             5    417.15
    ## 5:          Y           62                F             5    220.50
    ## 6:          Y           62                G             7    169.26

``` r
#colnames(WI_Bridges_new)


dataFrame_WI <- WI_Bridges_new %>% 
  as_tibble()


WI_interesting_new <- dataFrame_WI[,c(1:2,4 ,67:69, 27)]
head(WI_interesting_new)
```

    ## # A tibble: 6 x 7
    ##   STATE_CODE_001 STRUCTURE_NUMBE… ROUTE_PREFIX_00… DECK_COND_058
    ##            <int> <chr>                       <int> <chr>        
    ## 1             55 00000000000F303                 6 4            
    ## 2             55 00000000000F304                 6 5            
    ## 3             55 00000000000F310                 6 5            
    ## 4             55 00000000000F311                 6 5            
    ## 5             55 00000000000F315                 6 5            
    ## 6             55 00000000000F317                 6 7            
    ## # … with 3 more variables: SUPERSTRUCTURE_COND_059 <chr>,
    ## #   SUBSTRUCTURE_COND_060 <chr>, YEAR_BUILT_027 <int>

``` r
WI_interesting_new <- na_if(WI_interesting_new, "N")

WI_interesting_new[, 3] <- sapply(WI_interesting_new[, 3], as.factor)

WI_interesting_new[, 4:6] <- sapply(WI_interesting_new[, c(4:6)], as.numeric, na.rm = TRUE)

WI_interesting_new <- arrange(WI_interesting_new,ROUTE_PREFIX_005B)





# Filtered based on type of road

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


WI_interesting_old <- dataFrame_WI_old[,c(1:2,4 ,67:69, 27)]
head(WI_interesting_old)
```

    ## # A tibble: 6 x 7
    ##   STATE_CODE_001 STRUCTURE_NUMBE… ROUTE_PREFIX_00… DECK_COND_058
    ##            <int> <chr>                       <int> <chr>        
    ## 1             55 00000000000F001                 6 4            
    ## 2             55 00000000000F301                 6 5            
    ## 3             55 00000000000F303                 6 6            
    ## 4             55 00000000000F309                 6 7            
    ## 5             55 00000000000F310                 6 4            
    ## 6             55 00000000000F311                 6 7            
    ## # … with 3 more variables: SUPERSTRUCTURE_COND_059 <chr>,
    ## #   SUBSTRUCTURE_COND_060 <chr>, YEAR_BUILT_027 <int>

``` r
WI_interesting_old <- na_if(WI_interesting_old, "N")

WI_interesting_old[, 3] <- sapply(WI_interesting_old[, 3], as.factor)

WI_interesting_old[, 4:6] <- sapply(WI_interesting_old[, c(4:6)], as.numeric, na.rm = TRUE)






WI_interesting_old <- arrange(WI_interesting_old,ROUTE_PREFIX_005B)






# Filtered based on type of road
# 
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
```
