---
description: Bending data to answer your questions with dplyr.
---

# Manipulating Data

To manipulate data in the tidyverse, we go to the `dplyr` package - a toolbox of different **"data pliers"** we can use to modify and manipulate our dataset. Just like _readr_, _`dplyr`_ also comes with a handy cheatsheet for data transformation you can find [here](https://github.com/rstudio/cheatsheets/raw/master/data-transformation.pdf). 

Today we're going to cover 5 key functions that'll come in handy in your data transformation. These are `filter()`, `select()`, `mutate()`, `summarise()` and `group_by()`.  

But before we get onto that, let's talk about another key feature in the tidyverse that makes reading and writing code a breeze! Ladies and gentlemen, meet the [**pipe**](https://magrittr.tidyverse.org/) ****`%>%`.

## Piping your data

The pipe is a useful tool that simplifies writing code by allowing us to string together functions into a single **pipeline,** which can be executed all at once. Let's take another look at our cleaning code from the last chapter.

```r
> titanic_no_cabin <- select(titanic, -Cabin) 
> titanic_cleaned <- na.omit(titanic_no_cabin)
```

Here we have each command running by itself, and storing data into an intermediate variable called `titanic_no_cabin` in the middle. While this is perfectly fine,  if we do everything in a stepwise manner, we're quickly going to clog up our environment with a whole bunch of intermediate nonsense we don't really want.

Another way to approach this would be to combine these into a single command, like this.

```r
> titanic_cleaned <- na.omit(select(titanic, -Cabin))
```

This works fine too, but it's easy to get confused as to what is going on, and changing code on the go can be a right pain. Instead, we can use the pipe to string functions together like this.

```r
> titanic_cleaned <- titanic %>% # we take the titanic dataset
    select(-Cabin) %>% # select the bits we want
    na.omit() # then remove the NAs
```

The pipe takes the **output** from the function in the left and uses it as the first **input** for the function on the right \(or next line down\). In a nutshell, the following two commands are equivalent:

```r
> x %>% f(y)
# This is equivalent to:
> f(x,y)
```

The pipe makes it easy to follow and edit code. I you want more resources on the pipe, you can check [this video](https://youtu.be/hI1qy8C-5VE) or the documentation [here](https://magrittr.tidyverse.org/).

_Hint: Rather than typing out the symbols `%>%`every time you want a pipe, you can use the shortcut `shift+command+M` on mac or `shift+control+M` on windows._

With pipes in hand, let's go transform some data!

### Challenges

#### Challenge 1.1

{% tabs %}
{% tab title="Challenge" %}
```
Write the following command using the pipe operator:
> sum(2,10)
```
{% endtab %}

{% tab title="Solution" %}
```r
> 2 %>% sum(10)
[1] 12
```
{% endtab %}
{% endtabs %}

## filter\(\)

The first function we're going to have a look at, is `filter()`. This is a useful function for selecting a **subset** of observations \(rows\) of our data, based on whatever conditions we might want. Remember those comparisons we were using back in the first chapter? Now we can get a chance to use them!

Let's say I want to look at the subset of passengers aboard the Titanic who were 35 years of age. Using `filter()`, this is super easy to do! All we need to do is tell the filter function we want the "Age" variable to be equal to 35.

```r
> titanic35 <- titanic_cleaned %>% filter(Age == 35)
> glimpse(titanic35)
Observations: 18
Variables: 12
$ PassengerId <dbl> 4, 5, 21, 212, 231, 259, 270, 280, 364, 384, 487, 591
$ Survived    <dbl> 1, 0, 0, 1, 1, 1, 1, 1, 0, 1, 1, 0, 1, 0, 1, 1, 0, 0
$ Pclass      <dbl> 1, 3, 2, 2, 1, 1, 1, 3, 3, 1, 1, 3, 1, 3, 1, 1, 2, 3
$ Name        <chr> "Futrelle, Mrs. Jacques Heath (Lily May Peel)", "Alle
$ Sex         <chr> "female", "male", "male", "female", "female", "female
$ Age         <dbl> 35, 35, 35, 35, 35, 35, 35, 35, 35, 35, 35, 35, 35, 3
$ SibSp       <dbl> 1, 0, 0, 0, 1, 0, 0, 1, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0
$ Parch       <dbl> 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
$ Ticket      <chr> "113803", "373450", "239865", "F.C.C. 13528", "36973"
$ Fare        <dbl> 53.1000, 8.0500, 26.0000, 21.0000, 83.4750, 512.3292,
$ Embarked    <chr> "S", "S", "S", "S", "S", "C", "S", "S", "S", "S", "S"
```

In addition to our comparison operators \(`==`, `<=`, `>=`, `!=`, `<` and `>` \), we can also combine these using the logical **and** \(`&` \) and **or** \(`|`\) operators to do stuff like:

 Find passengers who are 35 **or** 40...

```r
> titanic3540 <- titanic_cleaned %>% filter(Age == 35 | Age == 40)
```

Find passengers who are **between** 35 and 40...

```r
> titanic35to40 <- titanic_cleaned %>% filter(Age >= 35 & Age <= 40)
```

Find female passengers from 1st class...

```r
> titanic1stfemales <- titanic_cleaned %>% 
    filter(Pclass == 1 & Sex == "female")
```

Or female passengers from 1st class who survived the voyage...

```r
> titanic1stfemalessurvived <- titanic_cleaned %>% 
    filter(Pclass == 1 & Sex == "female" & Survived == 1)
```

and the list goes on! Using `filter()`, you can slice up your dataset into whatever specific subsets you might want.

### Challenges

#### Challenge 2.1

{% tabs %}
{% tab title="Challenge" %}
```
Produce a data frame with only those passengers that:
Are males older than 30 years old.
```
{% endtab %}

{% tab title="Solution" %}
```r
> titanicMale30=titanic%>% filter(Sex=="male", Age>30)
```
{% endtab %}
{% endtabs %}

#### Challenge 2.2

{% tabs %}
{% tab title="Challenge" %}
```
Produce a data frame with only those passengers that:
Are Females between the ages of 5 and 60 (Not including 5 and 60 y/o)
```
{% endtab %}

{% tab title="Solution" %}
```r
> titanicFemale5_60=titanic%>% filter(Sex==“female”, Age>5, Age<60)
```
{% endtab %}
{% endtabs %}

## select\(\)

Here's one we've already seen in action. While `filter()` works to subset our data on a **row by row** basis, `select()` lets us subset our data by **columns**. We can do this in a couple of ways. Either by dropping variables we don't want by placing a minus `-` sign in front of them, like we did while cleaning the dataset, or by specifying which columns we want to keep by name.

Let's look at an example. Suppose we want to create a new data frame that only contains the names and the age of the passengers. You can do this by:

```r
> names_age <- titanic_cleaned %>% 
    select(Name, Age)
```

We can also combine this with filter to grab only the specific information we're interested in for our subsets. Say we want the names and fares of women in first class who survived. We can get that info like this:

```r
> names_fares <- titanic_cleaned %>% 
    filter(Pclass == 1 & Sex == "female" & Survived == 1) %>%
    select(Name, Fare)
```

Note that the `select()` function needs to come **after** the `filter()` function, otherwise there wouldn't be anything for us to filter by!

### Challenges

#### Challenge 3.1

{% tabs %}
{% tab title="Challenge" %}
```
Produce a data frame that does not include the names of the passengers.
```
{% endtab %}

{% tab title="Solution" %}
```r
> titanic_no_names <- titanic_cleaned %>% 
    select(-Name)
```
{% endtab %}
{% endtabs %}

#### Challenge 3.2

{% tabs %}
{% tab title="Challenge" %}
```
1. Write a single command (which can span multiple lines and includes pipes) that 
will produce a tibble that has the values for Age, SibSp and Fare for males only. 

2. How many rows does your tibble have and why?
```
{% endtab %}

{% tab title="Solution" %}
```r
> titanic_male <- titanic_cleaned %>% 
     filter(Sex=="male") %>% 
     select(Age,Sibsp,Fare)
> nrow(titanic_male)
[1] 453
# There were 453 males passengers
```
{% endtab %}
{% endtabs %}

## mutate\(\)

While `filter()` and `select()` are tools useful for _reducing_ our dataset, `mutate()` allows us to do the opposite and _generate_ new columns in our dataset. 

Say we want to have a representation of the fare variable adjusted for inflation to todays prices to give a better feel of the value of titanic tickets. A little poking around suggests that we would need to multiply the fare values by roughly 82 to get an equivalent price \(in 2020 AUD$\). Using `mutate()` we can create a new variable in our dataset called `fareToday`.

```r
> titanic_cleaned <- titanic_cleaned %>% 
    mutate(fareToday = Fare * 82)
```

Now that we've set up an equivalent price, let's have a look at how expensive these tickets were.

```r
> summary(titanic_cleaned$fareToday)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    0.0   660.1  1283.0  2834.5  2706.0 42011.0 
```

$42,011 is a damn lot for a ticket!

`mutate()`is also useful for creating new variables for us to filter or sort by. Say we're interested in separating out children and adults aboard the Titanic. We can use mutate to make a new logical variable stating whether a passenger was a child or adult using comparisons from our `Age` variable, like this.

```r
> titanic_cleaned <- titanic_cleaned %>%
    mutate(Child = Age < 18)
```

This is quite a powerful feature, especially when combined with the next two tools, `group_by()` and `summarise()`.

### Challenges

#### Challenge 4.1

{% tabs %}
{% tab title="Challenge" %}
```
Create a DataFrame with a new numeric variable that has the Fare value rounded to
the nearest integer.
Hint: Use the function round()
```
{% endtab %}

{% tab title="Solution" %}
```r
> titanic_round_fare <- titanic_cleaned %>%
    mutate(fareRound = round(Fare))
```
{% endtab %}
{% endtabs %}

## group\_by\(\) and summarise\(\)

`group_by()` and `summarise()`are a pair of functions which work hand in hand to draw comparisons between, and answer questions about subsets of our dataset.

`summarise()`is a function that creates a new data frame of **summary statistics** from our entire dataset for one or more variables. To use it, we call the `summarise()` function, with names for our new columns, and whatever **summary functions** we want to use within it. These summary functions are things like:

* `mean()` to give us the mean value of a variable.
* `sd()` to give us the standard deviation of a variable.
* `min()` giving us the lowest value of a variable.
* `max()` giving us the highest value of a variable.
* `n()` giving us the number of observations in a variable.

and many more.

Let's go ahead and generate some summary statistics about the ages of passengers on the Titanic.

```r
> ageSummary <- titanic_cleaned %>%
    summarise(meanAge = mean(Age), 
        sdAge = sd(Age),
        minAge = min(Age),
        maxAge = max(Age), 
        count = n()) 
> ageSummary 
# A tibble: 1 x 5
  meanAge sdAge minAge maxAge count
    <dbl> <dbl>  <dbl>  <dbl> <int>
1    29.6  14.5   0.42     80   712
```

Simple!

Where `summarise()` really gets powerful is when we combine it with `group_by()`to perform summaries on a **group by group** basis. Let's rerun those age summary statistics, but this time we're going to group by class beforehand.

```r
> ageClassSummary <- titanic_cleaned %>%
    group_by(Pclass) %>% # all we need to do is add a group by here...
    summarise(meanAge = mean(Age), 
        sdAge = sd(Age),
        minAge = min(Age),
        maxAge = max(Age), 
        count = n()) 
> ageClassSummary # ... in order to get a class by class summary here!
# A tibble: 3 x 6
  Pclass meanAge sdAge minAge maxAge count
   <dbl>   <dbl> <dbl>  <dbl>  <dbl> <int>
1      1    38.1  14.8   0.92     80   184
2      2    29.9  14.0   0.67     70   173
3      3    25.1  12.5   0.42     74   355
```

Now things are really getting interesting! We can see that passengers in 1st class were considerably older than those in 2nd and 3rd \(means = 38.1, 29.9, and 25.1 respectively\), and that there were far fewer 1st than 3rd class passengers \(184 vs. 355\).

With `mutate()`, `group_by()` and `summarise()`, we can answer all kinds of questions about our dataset!

Were males or females more likely to survive?

```r
> titanic_cleaned %>%
    group_by(Sex) %>%
    summarise(meanSurvived = mean(Survived))
# A tibble: 2 x 2
  Sex    meanSurvived
  <chr>         <dbl>
1 female        0.753
2 male          0.205
```

Who paid more? Kids or adults?

```r
> titanic_cleaned %>%
    group_by(Child) %>%
    summarise(meanFare = mean(fareToday))
# A tibble: 2 x 2
  Child meanFare
  <lgl>    <dbl>
1 FALSE    2886.
2 TRUE     2560.
```

And by grouping by multiple variables we can dive deeper into understanding the dataset, such as understanding the boarding dynamics of different classes.

```r
> titanic_cleaned %>%
   group_by(Embarked, Pclass) %>% # you can group by more than one variable! 
   summarise(count = n())
# A tibble: 9 x 3
# Groups:   Embarked [3]
  Embarked Pclass count # ... and get all combinations in our summary!
  <chr>     <dbl> <int>
1 C             1    74
2 C             2    15
3 C             3    41
4 Q             1     2
5 Q             2     2
6 Q             3    24
7 S             1   108
8 S             2   156
9 S             3   290
```

Here we can see that the majority of passengers \(especially those in 3rd class\) embarked at Southampton, with a bunch more first class passengers joining at Cherbourg, and very few hopping aboard at Queenstown.

### Challenges

#### Challenge 5.1

{% tabs %}
{% tab title="Challenge" %}
```
Find the overall survival rate using the summarise() function.
```
{% endtab %}

{% tab title="Solution" %}
```r
> summary_results = titanic_cleaned %>%
    summarise(survival_rate = mean(Survived))

> summary_results
# A tibble: 1 x 1  
  survival_rate
          <dbl>
          0.404

```
{% endtab %}
{% endtabs %}

#### Challenge 5.2

{% tabs %}
{% tab title="Challenge" %}
```
Calculate the survival rate per Class and Sex. 
Which combination of Class and Sex had the highest survival rate?
```
{% endtab %}

{% tab title="Solution" %}
```r
> summary_results = titanic_cleaned %>%
    group_by(Sex,Pclass) %>%
    summarise(survival_rate = mean(Survived))
# A tibble: 6 x 3
# Groups:   Sex [2]  
Sex    Pclass survival_rate  
<chr>   <dbl>         <dbl>
female      1         0.9642 
female      2         0.9193 
female      3         0.4614 
male        1         0.3965 
male        2         0.1526 
male        3         0.150

```
{% endtab %}
{% endtabs %}

## Saving your data

Having performed our analyses, the last thing we might want to do is save our data into a file somewhere. When manipulating data in the _tidyverse_, the only place anything is changing is within RStudio itself, not in the underlying files we loaded the data from. 

Fortunately, it is easy to save data into a file for use by other programs, or to bring back into R at a later date.

Let's save our cleaned dataset into a new csv file named "titanic\_cleaned.csv" using `write_csv()`. 

```r
> write_csv(titanic_cleaned, "titanic_cleaned.csv")
```

This will save a new csv file to your working directory, and should appear in your files panel looking a little like this.

![A clean, shiny brand\_new dataset!](../.gitbook/assets/screen-shot-2020-06-10-at-11.01.40-am.png)

If you wan to change the working directory, you can type 

```r
> setwd("path/to/directory")
```

Or you can select it manually by going to the menu and clicking on Session &gt; Set Working Directory .

With these tools under your belt, you're now ready to go tackle your own datasets and read, transform, export, and question to your heart's content. 

Go for it!

### Challenges

#### Challenge 6.1

{% tabs %}
{% tab title="Challenge" %}
```
Save a dataset that includes only first class passengers as a .tsv file.
```
{% endtab %}

{% tab title="Solution" %}
```r
> first_class_passengers = titanic_cleaned %>% 
    filter(Pclass == 1)
    
> write_tsv(first_class_passengers, path="titanic_first_class.txt")
```
{% endtab %}
{% endtabs %}

