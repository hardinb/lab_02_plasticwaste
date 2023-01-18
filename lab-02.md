Lab 02 - Plastic waste
================
Ben Hardin
1/17/2023

## Load packages and data

``` r
library(tidyverse) 
```

``` r
plastic_waste <- read.csv("data/plastic-waste.csv")
```

## Exercises

### Exercise 1

This code chunk creates a set of histograms showing the distribution of
plastic waste per capita (pwpc) separated by country. The histograms
show that African countries typically have the least amount of pwpc, and
that most countries have a pwpc of \< 0.5 kg per person. There is one
country in North America with a very high pwpc, which we know is
Trinidad and Tobago.

``` r
ggplot(data = plastic_waste,
       aes(x = plastic_waste_per_cap))+
  geom_histogram(binwidth = 0.2)+
  facet_wrap(~ continent)
```

    ## Warning: Removed 51 rows containing non-finite values (`stat_bin()`).

![](lab-02_files/figure-gfm/plastic-waste-continent-1.png)<!-- -->

### Exercise 2.1

Here we have displayed the same information from the histograms in a
different way by plotting the density distribution of pwpc for each
continent, separated by color. However, the graph is hard to read
because the alpha level is too high (in this case, 1.0), so the
distributions cover one another up.

``` r
ggplot(data = plastic_waste,
       aes(x = plastic_waste_per_cap,
           color = continent,
           fill = continent))+
  geom_density()
```

    ## Warning: Removed 51 rows containing non-finite values (`stat_density()`).

![](lab-02_files/figure-gfm/plastic-waste-density-1.png)<!-- --> Now, if
we adjust the alpha to 0.3, the distributions are transparent, allowing
us to see the full distribution of pwpc for each continent all at once.

``` r
ggplot(data = plastic_waste,
       aes(x = plastic_waste_per_cap,
           color = continent,
           fill = continent))+
  geom_density(alpha = 0.3)
```

    ## Warning: Removed 51 rows containing non-finite values (`stat_density()`).

![](lab-02_files/figure-gfm/plastic-waste-density-new-alpha-1.png)<!-- -->

### Exercise 2.2

We mapped the color and fill of the curves to the aesthetics argument
because this argument is used to map certain characteristics of the plot
to the values or levels of a variable in the dataset. In this case, we
wanted each level (i.e., each continent) to be represented by a separate
distribution mapped to a unique color.

We instead mapped the alpha to the geom argument because this argument
is used to determine characteristics of all the points in the plot
regardless of their value or level. In this case, we wanted the
distributions to be equally transparent for all continents.

### Exercise 4

Remove this text, and add your answer for Exercise 4 here.

``` r
# insert code here
```

### Exercise 5

Remove this text, and add your answer for Exercise 5 here.

``` r
# insert code here
```

### Exercise 6

Remove this text, and add your answer for Exercise 6 here.

``` r
# insert code here
```

### Exercise 7

Remove this text, and add your answer for Exercise 7 here.

``` r
# insert code here
```

``` r
# insert code here
```

### Exercise 8

Remove this text, and add your answer for Exercise 8 here.

``` r
# insert code here
```

## Pro-Tips

### Excercise 3

Try this :D

ggplot(data = plastic_waste, mapping = aes(x = continent, y =
plastic_waste_per_cap)) + geom_violin()+ geom_boxplot(width=.3,
fill=“green”) + stat_summary(fun.y=median, geom=“point”)

### Exercise 5

Helpful
reference:<http://www.sthda.com/english/wiki/ggplot2-themes-and-background-colors-the-3-elements>
