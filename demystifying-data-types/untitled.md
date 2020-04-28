---
description: 'A tibble, a vector, and a data frame walk into a bar...'
---

# Data Structures

Just like data types, all of our data objects in R also belong to **data structures**. We're already familiar with **values** and **vectors**, now read on to meet the rest of the family!

### Values

The simplest data structure in R is that of a single value, like what got back in the last chapter from running

```r
frequently_used_number  <- 1/40
```

For all intents and purposes, R treats these values as vectors, just with only a single element! With that said, let's move along to some _real_ vectors \(sorry `frequently_used_number`\).

### Vectors

Vectors are the other data structrue we've already ran into, and are the simplest way of storing multiple data elements in R.

Let's go ahead and make some vectors using the concatentate function `c().`

```r
# a logical vector 
logicals <- c(TRUE, TRUE, FALSE)

# an integer vector
integers <- c(1:10) # the colon ":" gives us the sequence 
                    # of intergers between 1 and 10

# a numeric vector 
doubles <- integers + 0.1 # here we're coercing our integer vector of
                          # 1 to 10 into a numeric vector of 1.1 to 10.1
# a string vector 
strings <- c("a", "f", "b", "v", "f") # remember the quotation marks

# and a looooooong numeric vector, just because

long <- seq(1, 1000, 0.1) # seq will generate a vector from 1 to 1000, 
                          # in 0.1 unit steps
```

At it's core, R is a language built around vectors, and there are a lot of inbuilt functions we can play with 

#### Looking into a vector

head - the start

tail - the end

subsetting \[\] and indices and colon for regions, - sign for avoiding indices 

#### Changing elements in a vector

reassigning with \[\] 

#### Vectors and coercion

One limitation of vectors is that they can only contain one type of data. Let's try to make a vector with some different data types

### Lists

#### Looking into lists



### Matrices

### Data Frames

### Tibbles





