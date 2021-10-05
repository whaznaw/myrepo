HW3
================
William Haznaw
10/5/2021

html\_document

Due October 5th, by midnight: In r4ds flights… What time of day should
you fly if you want to avoid delays as much as possible? Does this
choice depend on anything? Season? Weather? Airport? Airline? Find three
patterns (“null results” are ok\!). Write your results into Rmarkdown.
Include a short introduction that summarizes the three results. Then,
have a section for each finding. Support each finding with data
summaries and visualizations. Include your code when necessary. This
shouldn’t be long, but it might take some time to find the things you
want to talk about and lay them out in an orderly way.

``` r
flights %>%
  group_by(hour,origin) %>% 
  summarise(average_dep_delay = mean(dep_delay, na.rm = T)) %>% 
  ggplot(aes(x = hour, y = average_dep_delay)) + 
  geom_point() +
  geom_smooth()
```

![](HW3_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

``` r
flights %>%
  group_by(hour,origin) %>% 
  summarise(average_arr_delay = mean(arr_delay, na.rm = T)) %>% 
  ggplot(aes(x = hour, y = average_arr_delay)) + 
  geom_point() +
  geom_smooth()
```

![](HW3_files/figure-gfm/unnamed-chunk-2-2.png)<!-- -->

For both arrival delays and departure delays, it appears that the
earlier in the day that you fly it is more likely to have a shorter
delay if any delay at all.

**Seasons**

``` r
flights2 = flights %>% 
  mutate(season = ifelse(month %in% 10:12, "Fall",
                               ifelse(month %in% 1:3, "Winter",
                                      ifelse(month %in% 4:6, "Spring",
                                             "Summer"))))

flights2 %>% 
  group_by(hour,origin,season) %>% 
  summarise(average_dep_delay = mean(dep_delay, na.rm = T)) %>% 
  ggplot(aes(x = hour, y = average_dep_delay)) + 
  geom_point() +
  geom_smooth() +
  facet_wrap(~season)
```

![](HW3_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

These graphs show the average departure delays of flights based on their
season. While they all show a similar shape to the normal average delays
in the previous graphs, fall and winter seem to be a bit different. Fall
has a much flatter peak than all combined and winter keeps increasing
almost steadily as the hours go on. Spring and summer seem similar to
the whole graph. (I only included the departure delay since the weather
would be most important to look at in the NYC area)

**Origin**

``` r
flights %>%
  group_by(hour,origin) %>% 
  summarise(average_dep_delay = mean(dep_delay, na.rm = T)) %>% 
  ggplot(aes(x = hour, y = average_dep_delay)) + 
  geom_point() +
  geom_smooth()+
  facet_wrap(~origin)
```

![](HW3_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
flights %>%
  group_by(hour,origin) %>% 
  summarise(average_arr_delay = mean(arr_delay, na.rm = T)) %>% 
  ggplot(aes(x = hour, y = average_arr_delay)) + 
  geom_point() +
  geom_smooth()+
  facet_wrap(~origin)
```

![](HW3_files/figure-gfm/unnamed-chunk-4-2.png)<!-- -->

It would still be most beneficial to fly early in the morning rather
than mid-day/afternoon no matter which NYC airport you choose to fly out
of.
