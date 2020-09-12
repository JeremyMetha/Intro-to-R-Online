---
description: Finding your way around RStudio
---

# Introduction to RStudio

Throughout this lesson, we're going to teach you some of the fundamentals of the R language as well as some best practices for organising code for scientific projects that will make your life easier using RStudio: a free, open source R integrated development environment. It provides a built in editor, works on all platforms \(including on servers\) and provides many advantages such as integration with version control and project management.

#### **Basic layout**

When you first open RStudio, you will be greeted by three panels:

* The interactive R console \(entire left\)
* Environment/History \(tabbed in upper right\)
* Files/Plots/Packages/Help/Viewer \(tabbed in lower right\)

Once you open files, such as R scripts, an editor panel will also open in the top left, and your console will be visible in the bottom right, like this:

![Men in berets shouldn&apos;t appear in your screen though!](../.gitbook/assets/anatomy-of-rstudio.png)



## Introduction to R

In the lower left portion of RStudio, you'll find the R **interactive console**. This is where you will run all of your code, and can be a useful environment to try out ideas before adding them to an R script file. This console in RStudio is the same as the one you would get if you opened the R application or you just typed in `R` in your command line environment.

The first thing you will see in the R interactive session is a bunch of information, followed by a "&gt;" and a blinking cursor. The console operates on the idea of a "read, evaluate, print loop"

1. You type in your commands and hit enter.
2. R reads and interprets what you've written and tries to execute it.
3. R prints a result to the console.

### Work flow within RStudio <a id="work-flow-within-rstudio"></a>

There are two main ways one can work within RStudio.

1. Test and play within the interactive R console then copy code into a .R file to run later. 
   * This works well when doing small tests and initially starting off.
   * It quickly becomes laborious.
2. Start writing in an .R file and use RStudio's command / short cut to push current line, selected lines or modified lines to the interactive R console. 

We recommend taking approach number 2 for most applications. Let's go ahead and make a new .R script file by clicking the little page icon in the top left corner, and selecting **R script** from the dropdown menu. An **R script** is basically a text file with **R** commands.

#### Running segments of your code

RStudio offers you great flexibility in running code from within the editor window. There are buttons, menu choices, and keyboard shortcuts. To run the current line, you can:

1. Click on the `Run` button just above the editor panel.
2. Select "Run Lines" from the "Code" menu.
3. Hit `Ctrl-Enter` in Windows or Linux or `Command-Enter` on OS X. \(This shortcut can also be seen by hovering the mouse over the button\).

**Hint:** You can also run multiple lines by selecting them and then running your code using 1, 2 or 3.

With that, let's start having a play in the R console!

## Using R as a calculator

The simplest thing you could do with R is do arithmetic. Try typing into the console:

```r
1 + 100
```

Now hit `ENTER`. R should return:

```r
[1] 101
```

You should see the answer, with a preceding "\[1\]" \(Don't worry about this for now, we'll explain that later. For now think of it as indicating output\). 

If you type in an incomplete command, R will wait for you to complete it. Try typing this:

```r
> 1 -
```

At this stage R is effectively waiting for you to complete the command. R lets you know this by showing you a `+` sign rather than the usual `>`

```r
+
```

Any time you hit return and the R session shows a **+** instead of a **&gt;**, it means it's waiting for you to complete the command. If you want to cancel a command you can simply hit `Esc` and RStudio will give you back the **&gt;** prompt, forgetting whatever you'd input beforehand.

Try canceling the command.

When using R as a calculator, the order of operations is the same as you would have learnt back in school.

From highest to lowest precedence:

* Parentheses: `(`, `)`
* Exponents: `^` or `**`
* Division: `/`
* Multiplication: `*`
* Addition: `+`
* Subtraction: `-`

Use parentheses to group operations in order to force the order of evaluation if it differs from the default, or to make clear what you intend.

```r
> 3 + 5 * 2
[1] 13
```

is not the same as

```r
> (3 + 5) * 2
[1] 16
```

This can get unwieldy when not needed, but clarifies your intentions. Remember that others may later read your code.

```r
> (3 + (5 * (2 ^ 2))) # hard to read
> 3 + 5 * 2 ^ 2       # clear, if you remember the rules
> 3 + 5 * (2 ^ 2)     # if you forget some rules, this might help
```

While talking about readable code, make use of **comments** to show what a line is doing

### Comments

The text after each line of code is called a comment. Anything that follows after the hash symbol `#` is ignored by R when executes code.

### Scientific Notation

When returning really small or large numbers R will eschew a bunch of zeroes in favour of scientific notation:

```r
> 2/10000
[1] 2e-04
```

Which is shorthand for "multiplied by `10^XX`". So `2e-4` is shorthand for `2 * 10^(-4)`.

You can write numbers in scientific notation too:

```r
> 5e3  # Note the lack of minus here
[1] 5000
```

### Comparing things <a id="comparing-things"></a>

We can also do comparisons in R:

```r
> 1 == 1  # equality (note two equals signs, read as "is equal to")
[1] TRUE
```

```r
> 1 != 2  # inequality (read as "is not equal to")
[1] TRUE
```

```r
> 2 < 1  # less than
[1] FALSE
```

```r
> 1 <= 1  # less than or equal to
[1] TRUE
```

```r
> 1 > 0  # greater than
[1] TRUE
```

```r
> 1 >= 9 # greater than or equal to
[1] FALSE
```

### Challenges

Now that you're familiar with the fundamentals, here are a few challenges to test what you've learned.

#### Challenge 1.1

{% tabs %}
{% tab title="Challenge" %}
```
How much is 32*19 + 123?
```
{% endtab %}

{% tab title="Solution" %}
```r
> 32*19 + 123 
[1] 731
```
{% endtab %}
{% endtabs %}

#### Challenge 1.2

{% tabs %}
{% tab title="Challenge" %}
```
Copy paste this and run it in the console: 
11*34 + log(10

What happens? Do you get a value?
```
{% endtab %}

{% tab title="Solution" %}
```r
> 11*34 + log(10
+ 

# you can see we're still waiting for an input,
# this is because we didn't close our bracket
```

Any time you hit return and the R session shows a **+** instead of a **&gt;**, it means it's waiting for you to complete the command. If you want to cancel a command you can simply hit `Esc` and RStudio will give you back the **&gt;** prompt, forgetting whatever you'd input beforehand.
{% endtab %}
{% endtabs %}

## Using R as a _fancy_ calculator

_Using functions and finding help_

R has many built in mathematical **functions**. To call a function, we simply type its name, followed by open and closing parentheses. Anything we type inside the parentheses is called the function's **arguments.**

Here are just a few of the functions R has on offer.

```r
sin(1)  # trigonometry functions
[1] 0.841471
```

```r
log(1)  # natural logarithm
[1] 0
```

```r
log10(10) # base-10 logarithm
[1] 1
```

```r
exp(0.5) # e^(1/2)
[1] 1.648721
```

Don't worry about trying to remember every function in R. You can simply look them up on google, or you can find help in RStudio!

### Finding Help

#### Tab Completion

When you start typing a function in RStudio, it will show a list of possible functions alongside what you're writing.This is one advantage that RStudio has over R on its own, it has autocompletion abilities that allow you to more easily look up functions, their arguments, and the values that they take.

#### Finding documentation

Typing a `?` before the name of a command will open the help page for that command. As well as providing a detailed description of the command and how it works, scrolling to the bottom of the help page will usually show a collection of code examples which illustrate command usage. We'll go through an example later.

### Challenges

#### Challenge 2.1

{% tabs %}
{% tab title="Challenge" %}
```
Which one is larger: sin(10) or cos(10)? 

Can you write an expression to solve this?

```
{% endtab %}

{% tab title="Solution" %}
```r
# sin(10) is greater than cos(10), we can run a comparison to show this in R

> sin(10) > cos(10)
[1] TRUE
```
{% endtab %}
{% endtabs %}

#### Challenge 2.2

{% tabs %}
{% tab title="Challenge" %}
```
Find out what the “abs()” function does using the inbuilt help 

How much is abs(10)?
```
{% endtab %}

{% tab title="Solution" %}
```r
# ?abs or help(abs) will pull up the documentation for the function

> abs(10)
[1] 10
```
{% endtab %}
{% endtabs %}

#### Challenge 2.3

{% tabs %}
{% tab title="Challenge" %}
```
What is the square root of 11? 
 
Is there a function for this in R?
```
{% endtab %}

{% tab title="Solution" %}
```r
 # there are a couple of ways to do this, we can use the exponent operator

> 11 * 0.5
[1] 3.316625

# or use the sqrt() function

> sqrt(11)
[1] 3.316625
```
{% endtab %}
{% endtabs %}

#### Challenge 2.4

{% tabs %}
{% tab title="Challenge" %}
```
How do you round numbers to the nearest integer in R?
 
Is there a function? 

Round 3.5 to the nearest integer.
```
{% endtab %}

{% tab title="Solution" %}
```r
# once again there are a few ways to do this!
# you can round to the nearest integer using round()
> round(3.5)
[1] 4

# round up using ceiling()
> ceiling(3.5)
[1] 4


# or round down using floor()
> floor(3.5)
[1] 4
```
{% endtab %}
{% endtabs %}

## Variables

Instead of typing out numbers we might want to use in calculations again and again, we can store their values in **variables** using the assignment operator `<-`, like this:

```r
frequently_used_number <- 1/40
```

Notice that assignment does not print a value. Instead, we stored it for later in something called a **variable**. `frequently_used_number` now contains the **value** `0.025`:

```r
frequently_used_number
[1] 0.025
```

More precisely, the stored value is a _decimal approximation_ of this fraction called a [floating point number](http://en.wikipedia.org/wiki/Floating_point).

You can also assign variables using `=`

```r
frequently_used_number = 1/40
```

Look for the `Environment` tab in the top right pane of RStudio, and you will see that `frequently_used_number` and its value have appeared. Our variable `frequently_used_number` can be used in place of a number in any calculation that expects a number:

```r
log(frequently_used_number)
[1] -3.688879
```

Notice also that variables can be reassigned:

```r
frequently_used_number <- 100
```

`frequently_used_number` used to contain the value 0.025 and and now it has the value 100.

Assignment values can contain the variable being assigned to:

```r
frequently_used_number <- frequently_used_number + 1 
# notice how RStudio updates its description in the environement
```

### Naming variables

When naming variables, you need to follow a few rules:

* Variable names **can** contain:
  * letters
  * numbers
  * underscores
  * periods. 
* They **cannot** start with a number 
* They **cannot** have any spaces. 

Different people use different conventions for long variable names, these include:

* underscores\_between\_words
* periods.between.words
* camelCaseToSeparateWords

What you use is up to you, but **be consistent**, and remember that you're likely going to be typing these out quite a few ties, so try to be _concise_ too.

### Vectorisation <a id="vectorisation"></a>

One final thing to be aware of is that R is **vectorised**, meaning that variables and functions can have vectors as values. For example

```r
> 1:5
[1] 1 2 3 4 5
```

```r
2^(1:5)
[1]  2  4  8 16 32
```

You can create vectors using the `c()` function

```r
> x <- c(3, 1, 4, 1, 5, 9)
> 2^x
[1] 8 2 16 2 32 512
```

This is incredibly powerful, but we will discuss this further in a later lesson. 

### Managing your environment <a id="managing-your-environment"></a>

There are a few useful commands you can use to interact with the R session.

`ls` will list all of the variables and functions stored in the global environment \(your working R session\):

```text
> ls()
[1] "hook_error" "hook_in"    "hook_out"   "frequently_used_number"
```

Note here that we didn't given any arguments to `ls`, but we still needed to give the parentheses to tell R to call the function.

If we type `ls` by itself, R will print out the source code for that function!

```r
> ls
function (name, pos = -1L, envir = as.environment(pos), all.names = FALSE,    
pattern, sorted = TRUE) 
{
    if (!missing(name)) {
        pos <- tryCatch(name, error = function(e) e)
        if (inherits(pos, "error")) {
            name <- substitute(name)
            if (!is.character(name)) 
                name <- deparse(name)
            warning(gettextf("%s converted to character string", 
                sQuote(name)), domain = NA)
            pos <- name
        }
    }
    all.names <- .Internal(ls(envir, all.names, sorted))
    if (!missing(pattern)) {
        if ((ll <- length(grep("[", pattern, fixed = TRUE))) && 
            ll != length(grep("]", pattern, fixed = TRUE))) {
            if (pattern == "[") {
                pattern <- "\\["
                warning("replaced regular expression pattern '[' by  '\\\\['")
            }
            else if (length(grep("[^\\\\]\\[<-", pattern))) {
                pattern <- sub("\\[<-", "\\\\\\[<-", pattern)
                warning("replaced '[<-' by '\\\\[<-' in regular expression pattern")
            }
        }
        grep(pattern, all.names, value = TRUE)
    }
    else all.names
}
<bytecode: 0x34ad398>
<environment: namespace:base> 
```

You can use `rm` to delete objects you no longer need:

```r
> rm(frequently_used_number)
```

If you have lots of things in your environment and want to delete all of them, you can pass the results of `ls` to the `rm` function to do a big spring clean of your environment.

```r
> rm(list = ls())
```

In this case we've combined the two. Just like the order of operations, anything inside the innermost parentheses is evaluated first, and so on.

In this case we've specified that the results of `ls` should be used for the`list` argument in `rm`. When assigning values to arguments by **name**, you _must_ use the `=` operator, not the `<-` operator from before.

### Challenges

#### Challenge 3.1

{% tabs %}
{% tab title="Challenge" %}
```
Which of the following are valid R variable names?    

> min_height
> max.height
> _age
> .mass 
> MaxLength 
> min-length 
> 2widths 
> celsius2kelvin
```
{% endtab %}

{% tab title="Solutions" %}
```r
> min_height # Valid
> max.height # Valid
> _age # Invalid, starts with an underscore.
> .mass # Valid, but does it show up in your environment? 
# Anything starting with a period (.) is called a hidden variable
> MaxLength # Valid
> min-length # Invalid, due to the - sign
> 2widths # Invalid, starts with a letter
> celsius2kelvin # Valid
```
{% endtab %}
{% endtabs %}

#### Challenge 3.2

{% tabs %}
{% tab title="Challenge" %}
```
What will be the value of each variable after each statement 
in the following program?

> mass <- 47.5
> age <- 122
> mass <- mass * 2.3
> age <- age - 20
```
{% endtab %}

{% tab title="Solutions" %}
```r
> mass <- 47.5 # = 47.5
> age <- 122 # = 122
> mass <- mass * 2.3 # = 109.25
> age <- age - 20 # = 102
```
{% endtab %}
{% endtabs %}

#### Challenge 3.3

{% tabs %}
{% tab title="Challenge" %}
```
Create a vector with these numbers: 
1, 11, 111, 1111

B. What is the square root of each of the numbers in A?
```
{% endtab %}

{% tab title="Solution" %}
```r
# to make a vector of numbers we can use the c() function
> vector <- c(1, 11, 111, 1111)


# and we can take the square root using our sqrt() function
> sqrt(vector)
[1] 1.000000  3.316625 10.535654 33.331667
```
{% endtab %}
{% endtabs %}

#### Challenge 3.4

{% tabs %}
{% tab title="Challenge" %}
```
Clean up your working environment by deleting the mass and age variables.
```
{% endtab %}

{% tab title="Solution" %}
```r
# You can run these one at a time...
> rm(mass)
> rm(age)

# Or run them together!
> rm(list = c('mass', 'age'))

# This is a litle more complicated.
# We're creating a vector of names of objects, 
# then removing everything in the vector.
# Don't worry if this doesn't quite make sense yet.
```
{% endtab %}
{% endtabs %}

## R Packages

It is possible to add functions to R by writing a package, or by obtaining a package written by someone else. As of this writing, there are over 15,000 packages available on [CRAN](https://cran.r-project.org/) \(the comprehensive R archive network\). R and RStudio have functionality for managing packages:

* you can see what packages are installed by typing`installed.packages()`
* you can install packages by typing `install.packages("packagename")`where `packagename` is the package name, in quotes. Remember, this is what we did when installing the tidyverse on the [setting up](https://jeremymetha.gitbook.io/introduction-to-r/getting-set-up) page earlier
* you can update installed packages by typing `update.packages()`
* you can remove a package with `remove.packages("packagename")`
* and **most importantly,** you can make a package available for use with `library(packagename)`, without doing this you won't be able to use the contents of the package in the current session

Note that a package has to be installed only once. However, it must be called every time you open R or RStudio by typing

```r
> library(packagename)
```

### Challenges

Here's one last fun challenge for the lesson

#### Challenge 4.1

{% tabs %}
{% tab title="Challenge" %}
```
Install the package "RXKCD"

What can you do with this package?
```
{% endtab %}

{% tab title="Solutions" %}
```r
> install.packages("RXKCD")

# this package lets you see XKCD comics in R!
# if you don't know XKCD, you MUST visit www.xkcd.com 
# and enjoy some geeky stick figures :)
```
{% endtab %}
{% endtabs %}



