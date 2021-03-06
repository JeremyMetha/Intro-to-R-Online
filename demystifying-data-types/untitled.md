---
description: 'A list, a vector, and a data frame walk into a bar...'
---

# Data Structures

Just like data types, all of our data objects in R also belong to **data structures**. We're already familiar with **values** and **vectors**, now read on to meet the rest of the family!

## Values

The simplest data structure in R is that of a single value, like what get back from running:

```r
frequently_used_number  <- 1/40
```

For all intents and purposes, R treats these values as vectors, just with only a single element! With that said, let's move along to some _real_ vectors \(sorry `frequently_used_number`\).

## Vectors

Vectors are the other data structure we have already ran into. They are the simplest way of storing multiple data elements in R.

Let's go ahead and make some vectors using the concatenate function `c()`.

```r
# a logical vector 
logicals <- c(TRUE, TRUE, FALSE)

# an integer vector
integers <- c(1:10) # the colon ":" gives us the sequence 
                    # of intergers between 1 and 10

# a numeric vector 
doubles <- integers + 0.1 # here we're coercing our integer vector of
                          # 1 to 10 into a numeric vector of 1.1 to 10.1
# a character vector 
strings <- c("a", "f", "c", "d", "e") # remember the quotation marks

# and a looooooong numeric vector, just because

long <- seq(1, 100, 0.1) # seq will generate a vector from 1 to 1000, 
                          # in 0.1 unit steps
```

At its core, R is a language built around vectors. As such, there are a lot of inbuilt functions we can use to manipulate them. We'll go over a few now.

### Looking into a vector

The first thing we might want to do with our vector is look at it. Let's call our long vector and see what's in it:

```r
> long
[1]   1.0   1.1   1.2   1.3   1.4   1.5   1.6   1.7   1.8   1.9   2.0   2.1   2.2   2.3   2.4   2.5   2.6   2.7   2.8   2.9   3.0   3.1   3.2   3.3   3.4   3.5
 [27]   3.6   3.7   3.8   3.9   4.0   4.1   4.2   4.3   4.4   4.5   4.6   4.7   4.8   4.9   5.0   5.1   5.2   5.3   5.4   5.5   5.6   5.7   5.8   5.9   6.0   6.1
 [53]   6.2   6.3   6.4   6.5   6.6   6.7   6.8   6.9   7.0   7.1   7.2   7.3   7.4   7.5   7.6   7.7   7.8   7.9   8.0   8.1   8.2   8.3   8.4   8.5   8.6   8.7
 [79]   8.8   8.9   9.0   9.1   9.2   9.3   9.4   9.5   9.6   9.7   9.8   9.9  10.0  10.1  10.2  10.3  10.4  10.5  10.6  10.7  10.8  10.9  11.0  11.1  11.2  11.3
[105]  11.4  11.5  11.6  11.7  11.8  11.9  12.0  12.1  12.2  12.3  12.4  12.5  12.6  12.7  12.8  12.9  13.0  13.1  13.2  13.3  13.4  13.5  13.6  13.7  13.8  13.9
[131]  14.0  14.1  14.2  14.3  14.4  14.5  14.6  14.7  14.8  14.9  15.0  15.1  15.2  15.3  15.4  15.5  15.6  15.7  15.8  15.9  16.0  16.1  16.2  16.3  16.4  16.5
[157]  16.6  16.7  16.8  16.9  17.0  17.1  17.2  17.3  17.4  17.5  17.6  17.7  17.8  17.9  18.0  18.1  18.2  18.3  18.4  18.5  18.6  18.7  18.8  18.9  19.0  19.1
[183]  19.2  19.3  19.4  19.5  19.6  19.7  19.8  19.9  20.0  20.1  20.2  20.3  20.4  20.5  20.6  20.7  20.8  20.9  21.0  21.1  21.2  21.3  21.4  21.5  21.6  21.7
[209]  21.8  21.9  22.0  22.1  22.2  22.3  22.4  22.5  22.6  22.7  22.8  22.9  23.0  23.1  23.2  23.3  23.4  23.5  23.6  23.7  23.8  23.9  24.0  24.1  24.2  24.3
[235]  24.4  24.5  24.6  24.7  24.8  24.9  25.0  25.1  25.2  25.3  25.4  25.5  25.6  25.7  25.8  25.9  26.0  26.1  26.2  26.3  26.4  26.5  26.6  26.7  26.8  26.9
[261]  27.0  27.1  27.2  27.3  27.4  27.5  27.6  27.7  27.8  27.9  28.0  28.1  28.2  28.3  28.4  28.5  28.6  28.7  28.8  28.9  29.0  29.1  29.2  29.3  29.4  29.5
[287]  29.6  29.7  29.8  29.9  30.0  30.1  30.2  30.3  30.4  30.5  30.6  30.7  30.8  30.9  31.0  31.1  31.2  31.3  31.4  31.5  31.6  31.7  31.8  31.9  32.0  32.1
[313]  32.2  32.3  32.4  32.5  32.6  32.7  32.8  32.9  33.0  33.1  33.2  33.3  33.4  33.5  33.6  33.7  33.8  33.9  34.0  34.1  34.2  34.3  34.4  34.5  34.6  34.7
[339]  34.8  34.9  35.0  35.1  35.2  35.3  35.4  35.5  35.6  35.7  35.8  35.9  36.0  36.1  36.2  36.3  36.4  36.5  36.6  36.7  36.8  36.9  37.0  37.1  37.2  37.3
[365]  37.4  37.5  37.6  37.7  37.8  37.9  38.0  38.1  38.2  38.3  38.4  38.5  38.6  38.7  38.8  38.9  39.0  39.1  39.2  39.3  39.4  39.5  39.6  39.7  39.8  39.9
[391]  40.0  40.1  40.2  40.3  40.4  40.5  40.6  40.7  40.8  40.9  41.0  41.1  41.2  41.3  41.4  41.5  41.6  41.7  41.8  41.9  42.0  42.1  42.2  42.3  42.4  42.5
[417]  42.6  42.7  42.8  42.9  43.0  43.1  43.2  43.3  43.4  43.5  43.6  43.7  43.8  43.9  44.0  44.1  44.2  44.3  44.4  44.5  44.6  44.7  44.8  44.9  45.0  45.1
[443]  45.2  45.3  45.4  45.5  45.6  45.7  45.8  45.9  46.0  46.1  46.2  46.3  46.4  46.5  46.6  46.7  46.8  46.9  47.0  47.1  47.2  47.3  47.4  47.5  47.6  47.7
[469]  47.8  47.9  48.0  48.1  48.2  48.3  48.4  48.5  48.6  48.7  48.8  48.9  49.0  49.1  49.2  49.3  49.4  49.5  49.6  49.7  49.8  49.9  50.0  50.1  50.2  50.3
[495]  50.4  50.5  50.6  50.7  50.8  50.9  51.0  51.1  51.2  51.3  51.4  51.5  51.6  51.7  51.8  51.9  52.0  52.1  52.2  52.3  52.4  52.5  52.6  52.7  52.8  52.9
[521]  53.0  53.1  53.2  53.3  53.4  53.5  53.6  53.7  53.8  53.9  54.0  54.1  54.2  54.3  54.4  54.5  54.6  54.7  54.8  54.9  55.0  55.1  55.2  55.3  55.4  55.5
[547]  55.6  55.7  55.8  55.9  56.0  56.1  56.2  56.3  56.4  56.5  56.6  56.7  56.8  56.9  57.0  57.1  57.2  57.3  57.4  57.5  57.6  57.7  57.8  57.9  58.0  58.1
[573]  58.2  58.3  58.4  58.5  58.6  58.7  58.8  58.9  59.0  59.1  59.2  59.3  59.4  59.5  59.6  59.7  59.8  59.9  60.0  60.1  60.2  60.3  60.4  60.5  60.6  60.7
[599]  60.8  60.9  61.0  61.1  61.2  61.3  61.4  61.5  61.6  61.7  61.8  61.9  62.0  62.1  62.2  62.3  62.4  62.5  62.6  62.7  62.8  62.9  63.0  63.1  63.2  63.3
[625]  63.4  63.5  63.6  63.7  63.8  63.9  64.0  64.1  64.2  64.3  64.4  64.5  64.6  64.7  64.8  64.9  65.0  65.1  65.2  65.3  65.4  65.5  65.6  65.7  65.8  65.9
[651]  66.0  66.1  66.2  66.3  66.4  66.5  66.6  66.7  66.8  66.9  67.0  67.1  67.2  67.3  67.4  67.5  67.6  67.7  67.8  67.9  68.0  68.1  68.2  68.3  68.4  68.5
[677]  68.6  68.7  68.8  68.9  69.0  69.1  69.2  69.3  69.4  69.5  69.6  69.7  69.8  69.9  70.0  70.1  70.2  70.3  70.4  70.5  70.6  70.7  70.8  70.9  71.0  71.1
[703]  71.2  71.3  71.4  71.5  71.6  71.7  71.8  71.9  72.0  72.1  72.2  72.3  72.4  72.5  72.6  72.7  72.8  72.9  73.0  73.1  73.2  73.3  73.4  73.5  73.6  73.7
[729]  73.8  73.9  74.0  74.1  74.2  74.3  74.4  74.5  74.6  74.7  74.8  74.9  75.0  75.1  75.2  75.3  75.4  75.5  75.6  75.7  75.8  75.9  76.0  76.1  76.2  76.3
[755]  76.4  76.5  76.6  76.7  76.8  76.9  77.0  77.1  77.2  77.3  77.4  77.5  77.6  77.7  77.8  77.9  78.0  78.1  78.2  78.3  78.4  78.5  78.6  78.7  78.8  78.9
[781]  79.0  79.1  79.2  79.3  79.4  79.5  79.6  79.7  79.8  79.9  80.0  80.1  80.2  80.3  80.4  80.5  80.6  80.7  80.8  80.9  81.0  81.1  81.2  81.3  81.4  81.5
[807]  81.6  81.7  81.8  81.9  82.0  82.1  82.2  82.3  82.4  82.5  82.6  82.7  82.8  82.9  83.0  83.1  83.2  83.3  83.4  83.5  83.6  83.7  83.8  83.9  84.0  84.1
[833]  84.2  84.3  84.4  84.5  84.6  84.7  84.8  84.9  85.0  85.1  85.2  85.3  85.4  85.5  85.6  85.7  85.8  85.9  86.0  86.1  86.2  86.3  86.4  86.5  86.6  86.7
[859]  86.8  86.9  87.0  87.1  87.2  87.3  87.4  87.5  87.6  87.7  87.8  87.9  88.0  88.1  88.2  88.3  88.4  88.5  88.6  88.7  88.8  88.9  89.0  89.1  89.2  89.3
[885]  89.4  89.5  89.6  89.7  89.8  89.9  90.0  90.1  90.2  90.3  90.4  90.5  90.6  90.7  90.8  90.9  91.0  91.1  91.2  91.3  91.4  91.5  91.6  91.7  91.8  91.9
[911]  92.0  92.1  92.2  92.3  92.4  92.5  92.6  92.7  92.8  92.9  93.0  93.1  93.2  93.3  93.4  93.5  93.6  93.7  93.8  93.9  94.0  94.1  94.2  94.3  94.4  94.5
[937]  94.6  94.7  94.8  94.9  95.0  95.1  95.2  95.3  95.4  95.5  95.6  95.7  95.8  95.9  96.0  96.1  96.2  96.3  96.4  96.5  96.6  96.7  96.8  96.9  97.0  97.1
[963]  97.2  97.3  97.4  97.5  97.6  97.7  97.8  97.9  98.0  98.1  98.2  98.3  98.4  98.5  98.6  98.7  98.8  98.9  99.0  99.1  99.2  99.3  99.4  99.5  99.6  99.7
[989]  99.8  99.9 100.0
```

Jeez thats a lot of data! Fortunately we have a couple of different ways to look at parts of the vector without looking at the whole thing.

We can look at just the first few elements with `head()`

```r
> head(long)
[1] 1.0 1.1 1.2 1.3 1.4 1.5

# you can also specify how many elements you want to see
> head(long, 11)
 [1] 1.0 1.1 1.2 1.3 1.4 1.5 1.6 1.7 1.8 1.9 2.0
```

or just the last few elements with `tail()`

```r
> tail(long)
[1]  99.5  99.6  99.7  99.8  99.9 100.0

# you can also specify how many elements you want to see
> tail(long, 11)
 [1]  99.0  99.1  99.2  99.3  99.4  99.5  99.6  99.7  99.8  99.9 100.0
```

or pick and choose sections of the vector by **subsetting** using `[]` brackets to select the position, or **index**, of the elements we want.

```r
# we can subset a single index
> long[21]
[1] 3

# or a group of indices
> long[40:50]
[1] 4.9 5.0 5.1 5.2 5.3 5.4 5.5 5.6 5.7 5.8 5.9

# we can also use the "-" sign to look at a vector without an index or indices
> strings
[1] "a" "f" "c" "d" "e"

> strings[-2]
[1] "a" "c" "d" "e"

> strings[-c(2:5)]
[1] "a"
```

Note that indexing in R starts at 1. That is, if you want the first element of `sample_vector` you just need to type `sample_vector[1]`.  Intuitive, right?

### Modifying vectors

In addition to chopping up vectors by subsetting, we can also modify them or add to them by **reassigning** in the same way we'd assign a variable.

```r
# let's fix that our strings vector by replacing that "f" with a "b"

> strings[2] <- "b"

> strings
[1] "a" "b" "c" "d" "e"

# much nicer! but i think i'd still like that "f" on the end
#
> strings[6] <- "f"

> strings
[1] "a" "b" "c" "d" "e" "f"
```

### Vectors and coercion

One limitation of vectors is that they can **only** contain one type of data. Let's try to make a vector with some different data types.

```r
# if we try for a mix of data types
> mixed_bag <- c(TRUE, 10, 5+3i, "far_too_many_ducks")

# everything will be coerced into the most complex type

> typeof(mixed_bag)
[1] "character"

> mixed_bag
[1] "TRUE" "10" "5+3i" "far_too_many_ducks"
```

No worries, if we do want to group together objects with different data types, we just need to use a different data structure, this brings us to **lists**...

### Challenges

#### Challenge 1.1

{% tabs %}
{% tab title="Challenge" %}
```r
# What is the data type of each of the following objects:
> c(1, 2, 3)
c('d', 'e', 'f') 
c("d", "e", "f") 
c(TRUE,1L,10)
c("11",10,12)
c("Sun","night", FALSE)
```
{% endtab %}

{% tab title="Solution" %}
```r
> v1 = c('d', 'e', 'f') 
> typeof(v1)
[1] "character"
> v2 = c("d", "e", "f") 
> typeof(v2)
[1] "character"
> v3 = c(TRUE,1L,10)
> typeof(v3)
[1] "double"
> v4 = c("11",10,12)
> typeof(v4)
[1] "character"
> v5 = c("Sun","night", FALSE)
> typeof(v5)
[1] "character"
```
{% endtab %}
{% endtabs %}

#### Challenge 1.2

{% tabs %}
{% tab title="Challenge" %}
```r
# Subsetting vectors
# 1. Create a vector that ranges from 10 to 50 in steps of 3.
# 2. How many elements are in the vector?
# 3. What is the value of the 7th element 7 in the vector?
# 4. Replace the 10th element in the vector with your favourite 
#    number in the whole world.
# 5. How can you access the last 8 elements of the vector? 
#    Try finding two alternative ways.
# 6. Advanced: what is the sum of all the elements except the 
#    first 3 elements?
```
{% endtab %}

{% tab title="Solution" %}
```r
# 1 
> vec = seq(10,50,3)

# 2
> length(vec)
[1] 14

# 3
> vec[7]
[1] 28

# 4
> vec[10] = 24

# 5
> tail(vec,8) # one option
[1] 28 31 34 24 40 43 46 49
> vec[7:14] # another option
[1] 28 31 34 24 40 43 46 49

# 6 (Advanced)
> vec[-c(1:3)] 
[1] 19 22 25 28 31 34 24 40 43 46 49
> subset_vec = vec[-c(1:3)]
> subset_vec 
[1] 19 22 25 28 31 34 24 40 43 46 49
> sum(subset_vec)
[1] 361
```
{% endtab %}
{% endtabs %}

## Lists

Lists are a lot like vectors, except you can store data of multiple types in them! To create a list, we use the `list()` function rather than `c()`. 

```r
> mixed_bag <- list(TRUE, 10, 5+3i, "far_too_many_ducks")

> mixed_bag
[[1]]
[1] TRUE

[[2]]
[1] 10

[[3]]
[1] 5+3i

[[4]]
[1] "far_too_many_ducks"
```

As you can see, calling a list looks quite different to calling a vector. They also show up in a new spot in the environment panel.

![The list is a data object, not just a set of values](../.gitbook/assets/screen-shot-2020-04-28-at-9.24.19-pm.png)

See that little blue circle  with the white triangle on the left? Clicking on that will show us some more information about our list.

![Look at all those data types](../.gitbook/assets/screen-shot-2020-04-28-at-9.29.29-pm.png)

### Looking into a list

Just like with vectors, we can look at the elements of a list with the `head()` and `tail()` functions and reassign them  by using `[]`brackets and indices.

```r
# you can subset lists

> mixed_bag[3:4] 
[[1]]
[1] 5+3i

[[2]]
[1] "far_too_many_ducks"
```

However, see the double square brackets `[[]]` ? The output is stored in a list!  If you want to access an element in a list without the `list` wrapper you need to use double square brackets `[[]]` to access objects in the list:

```r
# Use double sqaure brackets to unwrap the output

> mixed_bag[[4]] 
[1] "far_too_many_ducks"
```

Finally, you can modify a list as well as add elements to it using `[[]]`

```r
# You can modify lists
> mixed_bag[[2]] <- 35

# and add to them
> mixed_bag[[5]] <- strings

> mixed_bag
[[1]]
[1] TRUE

[[2]]
[1] 35

[[3]]
[1] 5+3i

[[4]]
[1] "far_too_many_ducks"

[[5]]
[1] "a" "b" "c" "d" "e" "f" # a vector in a list, freaky
```

### Modifying lists

You might be saying: "Lists are great! Why would I ever want to use vectors?". Unfortunately, when using lists there are fewer calculations and manipulations you can do to them. Fortunately, it's not at all hard to turn a list into a vector - just use the `unlist()` function

```r
# this works totally fine
> a_vector <-  c(1, 2, 3, 4, 5) 
> a_vector + 1
[1] 2 3 4 5 6

# but this does not
> a_list <-  list(1, 2, 3, 4, 5) + 1
Error in a_ list(1, 2, 3, 4, 5) + 1 : non-numeric 
argument to binary operator


```

### Challenges

#### Challenge 2.1

{% tabs %}
{% tab title="Challenge" %}
```r
1. Create a list with the following 4 elements:
I. "I love summer"
II. TRUE
III. "fun temperatures"
IV. c(24,25,26)

2. Access (and unwrap) the third element.

3. Change the second element to FALSE

4. Advanced: Change the third fun temperature to 30 (that is, change 26 to 30)

```
{% endtab %}

{% tab title="Solution" %}
```r
# 1
> list_one = list("I love summer",TRUE,"fun temperatures",c(24,25,26))
# 2
> list_one[[3]]
[1] "fun temperatures"
# 3
> list_one[[2]] = FALSE
# 4 (Advanced)
> list_one[[4]][3] = 30

> list_one
[[1]][1] 
"I love summer"
[[2]][1] FALSE
[[3]][1] "fun temperatures"
[[4]][1] 24 25 30
```
{% endtab %}
{% endtabs %}

## Data Frames

The last data structure we're going to look at today is the **data frame**. Data frames are incredibly powerful as a means for representing tabular data.

Let's say we've a collection of different observations for a group of cats.

```r
> name <- c("Otis", "Luna", "Puss", "Garfield")
> colour <- c("black", "calico", "tabby", "ginger")
> weight <- c(11, 8, 13, 42)
> hates_mondays <- c(FALSE, FALSE, FALSE, TRUE)
```

Rather than storing them in individual lists or vectors, we can combine them all into a data frame!

```r
> cats <- data.frame(name, colour, weight, hates_mondays)
> cats
      name colour weight hates_mondays
1     Otis  black     11         FALSE
2     Luna calico      8         FALSE
3     Puss  tabby     13         FALSE
4 Garfield ginger     42          TRUE
```

Here you can see our vectors have been turned into the **columns** of our data frame, each named after the name of the vector that we used to create them. 

Like lists, data frames appear in the data section of the environment, and clicking the blue circle will show us some more information about our data frame.

![](../.gitbook/assets/screen-shot-2020-04-29-at-9.56.22-am.png)

Additionally, clicking on the little table icon in the top right will open a new window next to our script showing us everything in our data frame in spreadsheet style!

![Garfield is definitely the odd one out here...](../.gitbook/assets/screen-shot-2020-04-29-at-9.57.17-am.png)

### Looking at and modifying data frames

Just like vectors and lists, we can access and edit parts of our data frame by using `[]` brackets and indices. Given that data frames are 2 dimensional, we need to specify both a row index and a column index for the entry we want to modify, separated by a comma.  It looks something like this `[row, column].` 

By leaving one of these entries blank, we can instead access the entire row `[row,]` or column `[,column]` at once. 

```r
# accessing a specific element
> cats[2, 1]
[1] "Luna"

# accessing a whole column
> cats[,1]
[1] "Otis"     "Luna"     "Puss"     "Garfield"

# accessing a whole row
> cats[4,]
      name colour weight hates_mondays
4 Garfield ginger     42          TRUE
```

You can also access the last few rows and the last few rows of your data frame using `head(cats)` and `tail(cats).`

We will often want to access entire columns at a time to manipulate them. In addition to accessing them via index, we can access them by name using the `data_frame$column_name` syntax.

```r
# garfield is looking a little chonky
> cats$weight
[1] 11  8 13 42

# let's put the cats on a diet
> cats$weight <- sqrt(cats$weight) + 5

> cats$weight
[1]  8.316625  7.828427  8.605551 11.480741

# unfortunately, his dislike of mondays has spread 
# let's update the data frame to show this

> cats$hates_mondays <- TRUE

# assigning a single value to a column will
# change the entire column to that value
> cats$ hates_mondays
[1] TRUE TRUE TRUE TRUE
```

### Data frames as vectors and lists

You may have noticed that the operations we can do on data frames fall somewhere between what we can do with vectors, and what we can do with lists. This is no coincidence, a data frame is really just a vector/list hybrid! 

In a data frame, every **row** is a list of attributes for an object or event \(in our example, an individual cat\), while every **column** is a vector of a specific attribute for all our data. So basically, a row is an observation and a column is a variable.

It is this vector property that makes data frames such a powerful tool for data analysis, but more on that next lesson when we jump **into the tidyverse!**

### Challenges

R comes with some datasets. We are going to be suing the `mtcars` dataset for these challenges:

```r
data_f = mtcars
```

#### Challenge 3.1

{% tabs %}
{% tab title="Challenge" %}
```r
# Have a look at the data frame in your environment.
# How many columns and rows does the data frame has?
```
{% endtab %}

{% tab title="Solution" %}
```r
# You can look directly at data_f in your environment 
# or type the following command:
> dim(data_f)
[1] 32 11 
# 32 obseravations (rows)
# 11 variables (columns)
```
{% endtab %}
{% endtabs %}

#### Challenge 3.2

{% tabs %}
{% tab title="Challenge" %}
```r
Access the first 3 rows of the data frame
```
{% endtab %}

{% tab title="Solution" %}
```r
# One option
> head(data_f,3)
               mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4     21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag 21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710    22.8   4  108  93 3.85 2.320 18.61  1  1    4    1

# Another option: 
> data_f[1:3,]
               mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4     21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag 21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710    22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
```
{% endtab %}
{% endtabs %}

#### Challenge 3.3

{% tabs %}
{% tab title="Challenge" %}
```r
# 1. Access the mpg column.
# 2. Change the third element of the mpg column to 33.3
```
{% endtab %}

{% tab title="Solution" %}
```r
> data_f$mpg 
[1] 21.0 21.0 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 17.8 16.4 17.3 15.2 10.4 10.4 14.7 32.4 30.4 33.9 21.5 15.5 15.2[24] 13.3 19.2 27.3 26.0 30.4 15.8 19.7 15.0 21.4

> data_f$mpg[3] = 33.3
> data_f$mpg 
[1] 21.0 21.0 33.3 21.4 18.7 18.1 14.3 24.4 22.8 19.2 17.8 16.4 17.3 15.2 10.4 10.4 14.7 32.4 30.4 33.9 21.5 15.5 15.2[24] 13.3 19.2 27.3 26.0 30.4 15.8 19.7 15.0 21.4
```
{% endtab %}
{% endtabs %}

