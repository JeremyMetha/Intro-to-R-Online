---
description: Your one stop shop for data analysis.
---

# The Tidyverse

Now that we're familiar with the RStudio interface, and the data **types** and **structures** used in R, we're ready to start manipulating and analysing our own real world data with a little help from a collection of packages known as the _tidyverse._

\_\_

![The heart of the tidyverse](../.gitbook/assets/tidyverse2.png)

## What is the _tidyverse?_

At its core, the _tidyverse_ is a collection of packages designed to work together as a **full pipeline** for doing every stage of data analysis on **tidy** data as an alternative to the inbuilt base R functions. 

I use the _tidyverse_ for my data analyses for 2 main reasons:

1. All the packages in the _tidyverse_ fit together seamlessly and I don't need to worry about compatibility issues between different functions from different sources.
2. _Tidyverse_ scripts are easier to write, read and understand than base R code \(thanks largely to something called a [**pipe**](https://magrittr.tidyverse.org/)\).

## What is tidy data?

While messy data  can be messy in myriad ways, all tidy data follows the same structure, allowing us to easily manipulate and transform our data however we want. 

For a dataset to be considered **tidy**, it needs to follow 3 key rules:

1. Every different **variable** in our dataset gets a **column** to itself.
2. Every different **observation** or **object measured** in our dataset gets a **row** to itself.
3. Every different **value** in our dataset gets its own **cell.**

In practice, this looks a little something like this!

![The three rules of tidy data.](../.gitbook/assets/tidy-1.png)

Remember, that in a data frame a column corresponds to a **vector** and a ****row corresponds to a **list.**

Let's look at the cats data set we created in the data structures chapter here. Is this a tidy dataset?

```r
> cats
      name colour weight hates_mondays
1     Otis  black     11         FALSE
2     Luna calico      8         FALSE
3     Puss  tabby     13         FALSE
4 Garfield ginger     42          TRUE
```

Yes it is! We have our four variables \(`name`, `colour`, `weight` and `hates_mondays`\) in their own **columns**, our four observations \(Otis, Luna, Puss and Garfield\) in their own **rows**, and only a single value in each of our **cells**.

### What do I do if my dataset isn't tidy? Can I still use the tidyverse?

You most certainly can! While we won't be talking about it in this class, the _tidyr_ package exists specifically to help you transform your data from a non-tidy to a tidy format. You can read more about _tidyr_ and how to use it [here](https://tidyr.tidyverse.org).

## Setting up the _tidyverse_

If you haven't yet, the first thing we're going to need to do is install the `tidyverse` package onto our computers for R to use. To do this, we need to run:

```r
> install.packages ("tidyverse")
```

R will download and install a bunch of different files for us - don't worry if this takes a little while, we're installing quite a lot of stuff here!

Once we've downloaded the package, the next thing we need to do is load it into our R environment using the `library()` function, like so:

```r
> library(tidyverse)
```

That library function **attaches** the _tidyverse_ to our R session, allowing us to use the functions it contains. While it seems a bit redundant to need to load a package after we've already installed it, this is actually a useful safety feature to make sure we're using the functions we mean to. Note that you only need to install the `tidyverse` once, but you need to call the `library` command every time you start a new R session.

In R, **function names are not unique** and multiple different packages might contain functions by the same name that do different things. Loading **only the packages** you're using in a project helps to prevent these accidents from occurring.

Now that we've got the `tidyverse` up and running, let's jump in and start playing with a real world dataset!

### Challenges

#### Challenge 1

{% tabs %}
{% tab title="Challenge" %}
```r
# Is this a tidy data set?
> dogs
      name_birthyear    name_age
1     Luke_2015         Butch_9
2     Barney_2019       Luke_6
3     Butch_2012        Barney_2
```
{% endtab %}

{% tab title="Solution" %}
```r
No, it is not. 
1. Each variable does not have its own column.
2. Each value does not get its own cell.
```
{% endtab %}
{% endtabs %}

