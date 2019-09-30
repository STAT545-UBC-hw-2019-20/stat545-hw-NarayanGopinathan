HW3
================
Narayan
9/28/2019

    ## -- Attaching packages ------------------------------------- tidyverse 1.2.1 --

    ## v ggplot2 3.2.1     v purrr   0.3.2
    ## v tibble  2.1.3     v dplyr   0.8.3
    ## v tidyr   1.0.0     v stringr 1.4.0
    ## v readr   1.3.1     v forcats 0.4.0

    ## -- Conflicts ---------------------------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax
for authoring HTML, PDF, and MS Word documents. For more details on
using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that
includes both content as well as the output of any embedded R code
chunks within the document. You can embed an R code chunk like this:

<https://stat545-ubc-hw-2019-20.github.io/stat545-hw-NarayanGopinathan/HW3.html>

# Task Option 2

``` r
gapminder %>%
    group_by(continent) %>%
    select(country, continent, gdpPercap, year) %>%
       filter(gdpPercap == max(gdpPercap))
```

    ## # A tibble: 5 x 4
    ## # Groups:   continent [5]
    ##   country       continent gdpPercap  year
    ##   <fct>         <fct>         <dbl> <int>
    ## 1 Australia     Oceania      34435.  2007
    ## 2 Kuwait        Asia        113523.  1957
    ## 3 Libya         Africa       21951.  1977
    ## 4 Norway        Europe       49357.  2007
    ## 5 United States Americas     42952.  2007

The above represent the maximum GDP per capita on each continent. The
below represent the minimum GDP per capita on each continent.

``` r
gapminder %>%
    group_by(continent) %>%
    select(country, continent, gdpPercap, year) %>%
       filter(gdpPercap == min(gdpPercap))
```

    ## # A tibble: 5 x 4
    ## # Groups:   continent [5]
    ##   country                continent gdpPercap  year
    ##   <fct>                  <fct>         <dbl> <int>
    ## 1 Australia              Oceania      10040.  1952
    ## 2 Bosnia and Herzegovina Europe         974.  1952
    ## 3 Congo, Dem. Rep.       Africa         241.  2002
    ## 4 Haiti                  Americas      1202.  2007
    ## 5 Myanmar                Asia           331   1952

## Task Option 5

``` r
ggplot(gapminder, aes(year, lifeExp)) +
  geom_point(alpha = 0.2) +
  facet_wrap(~continent)
```

![](HW3_files/figure-gfm/unnamed-chunk-4-1.png)<!-- --> As a result of
these graphs, we can clearly see that life expectancy has increased over
time in every continent. No country has a life expectancy above 90, due
to the natural limitations of human biology, but there has been wide
variation below that limit. Africa and Asia have the biggest ranges,
while Europe and Oceania have more uniformly high life expectancies due
to higher levels of wealth. In Africa, no country had a life expectancy
above 60 in 1957, while now many countries do. Conversely, in Oceania,
no country has ever had a life expectancy below 60 (within the timeframe
of this dataset).

## Task Option 6

``` r
gapminder %>%
  filter(country =='Rwanda') %>%
  select(year, gdpPercap, lifeExp, pop)
```

    ## # A tibble: 12 x 4
    ##     year gdpPercap lifeExp     pop
    ##    <int>     <dbl>   <dbl>   <int>
    ##  1  1952      493.    40   2534927
    ##  2  1957      540.    41.5 2822082
    ##  3  1962      597.    43   3051242
    ##  4  1967      511.    44.1 3451079
    ##  5  1972      591.    44.6 3992121
    ##  6  1977      670.    45   4657072
    ##  7  1982      882.    46.2 5507565
    ##  8  1987      848.    44.0 6349365
    ##  9  1992      737.    23.6 7290203
    ## 10  1997      590.    36.1 7212583
    ## 11  2002      786.    43.4 7852401
    ## 12  2007      863.    46.2 8860588

``` r
gapminder %>%
  filter(country == 'Rwanda') %>%
  select(lifeExp, year) %>%
    ggplot(aes(year, lifeExp))+
   geom_line(alpha = 0.5)
```

![](HW3_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

``` r
gapminder %>%
  filter(country == 'Rwanda') %>%
  select(gdpPercap, year) %>%
    ggplot(aes(year, gdpPercap))+
   geom_line(alpha = 0.5)
```

![](HW3_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

## The interesting story of Rwanda

The history of Rwanda is very tragic. It had entrenched poverty and low
life expectancies for the entire twentieth century, since it gained
independence in 1962. However, in the early 1990s things got
dramatically worse, as a civil war devolved into genocide. In 1994, the
genocide struck and the country’s life expectancy dropped dramatically,
such that a baby born in 1992 could only expect to live 23.6 years.
Rwanda’s post-war recovery has been even more dramatic, and it is now a
peaceful state with low crime and violence. By 2007 its life expectancy
had exceeded its pre-genocide levels, and by 2016, it had increased to
67, according to World Bank data.
