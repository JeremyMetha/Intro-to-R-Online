---
description: Installing R and RStudio on your computer
---

# Setting up

To get into using R and RStudio, you're going to neeed to have a copy installed on your computer \(duh!\). Fortunately, getting set up is relatively quick and easy to do! 

## Installing R

R is a statistical programming language, providing us the **toolbox** needed to do our data science. To access the tools contained within the R language, we need to go ahead and download a copy to our computers.

### Installing R on Windows 10 

Installing R onto Windows 10 is pretty straightforward. The easiest way to go about it is through the Central R Archive Network \(CRAN, for short\). Just jump onto the [CRAN downloads](https://cran.r-project.org) page, click **download R for windows**, then click **install R for the first time**, and then **download R 3.6.3 for Windows**

Once the download is complete, you will have a file called _R-3.6.3-win.exe._ Run this .exe file and step thought he installation wizard - the defaults are generally fien so just click through until the process is complete. Congrats! You now have an R installation ready to go on your computer.

### Installing R on macOS

Installing R onto macOS is very similiar to installing on Windows. The easiest way to go about it is through the Central R Archive Network \(CRAN, for short\), jump onto the [CRAN downloads](https://cran.r-project.org) page, click **download R for \(Mac\) OS X**, then click **R-3.6.3.pkg** under latest relases to start your download.

Run that downloaded _R-3.6.3.pkg_ package, and feel free to leave the defaults, just like in windows and BAM! A shiny new R installation ready for you to play with.

## Installing RStudio

If R is our **toolbox** for data science, then RStudio is the **workshop** in which we can do our data wrangling work. Just like a workshop, RStudio provides us a contained place to build new projects, keep our tools and data organised and up to date, and save us the hassle of the cat walking though the paint tray and traipsing it all through the house...

![Those aren&apos;t my paint pawprints...](../.gitbook/assets/img_0638.jpg)

Anyway, let's go ahead and install RStudio!

**Note: you need to already have a copy of R on your computer for all this RStudio-ing to work.** 

### Installing RStudio on Windows

Like installing R, installing RStudio is pretty straightforward. We're going to go to the [RStudio downloads](https://rstudio.com/products/rstudio/download/#download) page, choose the **RStudio Desktop** version, and download the latest version for Windows 10/8/7 - it should be at the top of the all installers list. Once downloaded, go ahead and run the _RStudio-1.2.5033.exe_ file, again choosing the default options. 

### Installing RStudio on macOS

Much like the windows installation, we're going to head over to the [RStudio downloads](https://rstudio.com/products/rstudio/download/#download) page, choose the **RStudio Desktop** version, and download the latest version for macOS, second form the top of the all installers list. Once downloaded, go ahead and run the _RStudio-1.2.5033.dmg_ file, choosing the default options. Simples. 

### RStudio in the Cloud

One last option if you're struggling to setup R and RStudio on your computer is to run a **cloud instance** of RStudio. This allows you to access RStudio through a web browser and run your code on a distant supercomputer over in RStudio headquarters. Pretty cool, right!

To do this, you'll need to access the RStudio Cloud through [this link](https://rstudio.cloud), and sing up for a free account with them there.

### RStudio in the unimelb cloud

The [Melbourne Research Cloud](https://docs.cloud.unimelb.edu.au/) provides Infrastructure-as-a-Service cloud computing to the University of Melbourne researchers, providing access to a robust set of on-demand virtualized computing resources \(such as servers and storage\). The service makes it easy for researchers to quickly access scalable computational power as their research grows, without the overhead of spending precious time and money setting up their own compute environment.

Using the Melbourne Research Cloud you can install RStudio on a cloud computer and access it through the web. You can find instructions on how to do this [here](https://docs.cloud.unimelb.edu.au/guides/application_rstudio/).

## Installing packages into RStudio

Now that we've got our R toolbox and RStudio workshop, it's time to go ahead and add some tools, known in R lingo as **packages**. These packages provide extra functionality above and beyond what you can do using just R. Today we're going to install the [tidyverse](https://www.tidyverse.org) package, a set of tools for wrangling and analysing _tidy_ data \(more on that later\).

To install this package, go ahead and open RStudio and paste the following into the **interactive console** \(the panel on the left of RStudio\), 

```r
install.packages("tidyverse")
```

and hit enter on your keyboard to execute this code.

You now have everything you need to get started with your RStudio journey!

