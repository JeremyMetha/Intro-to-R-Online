---
description: A picture tells a thousand words...
---

# ggplot2 and the grammar of graphics

With data importing and wrangling under our belt, we're now ready to visualise our data and show it off to the world! To do this, we need to access one last package from the _tidyverse_, `ggplot2` .

## Setting Up

First things first, we need to make sure we have the package installed. If you're carrying on from the last _tidyverse_ chapter, `ggplot2` should be ready to go. We can double check this with the `library()` function.

```r
> library(tidyverse)
```

If this doesn't work, we'll need to install the packages first. Ideally installing thw whole `tidyverse` with,

```r
> install.packages("tidyverse")
```

Or if this doesn't work, just installing `ggplot2` with,

```r
> install.packages("ggplot2")
```

Finally, with our packages ready to go, the last thing to do is read in some data! We're going to continue with the titanic dataset we were working with in the last chapter, which we can read in and clean like so.

```r
> titanic = read_csv("https://goo.gl/4Gqsnz") %>%
    select(-Cabin) %>%
    na.omit()
```

This is exactly the same cleaning and reading process we covered last chapter, and should leave you with a dataframe named titanic, with 712 rows of observations, and 11 columns of variables. 

Before we get into the fun part, let's quickly go over just how ggplot works to put plots together.

## How `ggplot2` works: the Grammar of Graphics

Stemming from Leland Wilkinson's [Grammar of Graphics](https://www.springer.com/in/book/9780387245447), building plots with ggplot follows a very structured framework where different components stack upon each other to form our final graph.

![](../.gitbook/assets/1-mclnnvdhng-ikdbhjfhdna%20%281%29.png)

Moving from most to least essential, the components which make up a graph are:

* **Data:** In order to plot something, we need to have the underlying dataset!
* **Aesthetics:** Here we specifiy how we want our data to map onto our plot. Which variable belongs on the x-axis? What about the y-axis? Are we going to convey additional dimenisons of data with colour, or shape, or opacity?
* **Scale:** When setting scales, we need to allow for easy data visualisation. Most of the time we'll use a linear scale, but can also use other options such as geometric, or logarithmic, if the data is distributed differently and would better suit these transformations.
* **Geometric Objects:** These are the way that the data is represented on our graphs \(think points, lines, bars, etc..\) In ggplot, the name is frequently shortened to _geom._
* **Statistics:** We also need to think about summarising our data. Sure, we could plot everything if we want to, but often that will leave a resulting graph cluttered and confusing, particulary if we want to compare groups that have some overlap or variance.
* **Facets:** Speaking of groups, does ti make sens to plot everything on the one graph, or would smaller subgraphs for data in different categories be a better match?
* **Coordinate System:** This has only come up very rarely for me, but ggplot has the capacities to plot onto coordinates that aren't just an x-y plane, for all you pie chart lovers out there.

In practice, we can put these elements together a little like this:

![](../.gitbook/assets/picture-1%20%281%29.png)

With the theory and building blocks out of the way, let's get to some plotting!

