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
country in North America with a very high pwpc, which we know from the
lab instructions is Trinidad and Tobago.

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

![](lab-02_files/figure-gfm/plastic-waste-density-1.png)<!-- -->

Now, if we adjust the alpha to 0.3, the distributions are transparent,
allowing us to see the full distribution of pwpc for each continent all
at once.

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

### Exercise 3.1

The plots below show the same information displayed in Exercises 1 & 2,
this time presented as a box plot and as a violin plot.

The box plot clearly shows the median pwpc score among countries in each
continent as well as the countries that have unusually high pwpc scores
(i.e., outliers) and how far those outliers are from the typical range
of scores.

Conversely, the violin plot does a nice job of showing how pwpc is
distributed in each continent. For example, the fact that the violins(?)
are more bottom heavy for Africa and South America shows that these
continents have a greater proportion of countries with relatively low
pwpc than other continents with more peaks and valleys.

``` r
ggplot(data = plastic_waste,
       mapping = aes(x = continent, y = plastic_waste_per_cap))+
  geom_boxplot()
```

    ## Warning: Removed 51 rows containing non-finite values (`stat_boxplot()`).

![](lab-02_files/figure-gfm/plastic-waste-violin-1.png)<!-- -->

``` r
ggplot(data = plastic_waste,
       mapping = aes(x = continent, y = plastic_waste_per_cap))+
  geom_violin()
```

    ## Warning: Removed 51 rows containing non-finite values (`stat_ydensity()`).

![](lab-02_files/figure-gfm/plastic-waste-violin-2.png)<!-- -->

### Exercise 4.1

The scatterplot below shows the relationship between plastic waste per
capita (pwpc) and the amount of mismanaged plastic waste per capita. To
make the plot easier to interpret, I have filtered out Trinidad and
Tobago, which is an extreme outleir with a pwpc greater than 3. It looks
like there may be a few different relationships in this dataset, with a
subset of datapoints showing a positive linear relationship between pwpc
and mismanaged pwpc, while another subset shows no relationship because
the amount of mismanaged pwpc is consistently low regardless of the
amount of pwpc.

``` r
ggplot(data = plastic_waste %>%
         filter(plastic_waste_per_cap < 3), aes(x = mismanaged_plastic_waste_per_cap, 
                                 y = plastic_waste_per_cap))+
  geom_point()
```

![](lab-02_files/figure-gfm/plastic-waste-mismanaged-1.png)<!-- -->

### Exercise 4.2

Now, we use color to show which continent each datapoint in the
scatterplot is from. Now we can see that the relationship between pwpc
and mismanaged pwpc seems to differ between different continents.

The relationship appears to be positive and linear for countries in
Africa and Oceana. This shows that for within these continents, a
greater amount of plastic waste is typically associated with a greater
amount of mismanaged plastic waste.

Conversely, there does not appear to be much of a linear relationship
for countries in Europe and South America. Within these continents, it
looks like countries typically have a low amount of mismanaged plastic
waste, regardless of their overall amount of plastic waste.

Countries within Asia and North America seem to show a relationship
between pwpc and mismanaged pwpc that is somewhere in between these two
patterns.

``` r
ggplot(data = plastic_waste %>%
         filter(plastic_waste_per_cap < 3), aes(x = mismanaged_plastic_waste_per_cap, 
                                 y = plastic_waste_per_cap,
                                 color = continent))+
  geom_point(size = 2)
```

![](lab-02_files/figure-gfm/plastic-waste-mismanaged-continent-1.png)<!-- -->

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
