+++
title="R programming language"
date=2023-09-27
draft=true
+++

## Installation on Debian



Environment pane of RStudio contains all the data
Plots tab contains ggplot package produced drawings.

```r
install.packages("tidyverse")

library(tidyverse)
```

When the data is spread across multiple categories or groups, it can be challenging to manage your analysis, visualize trends, and build graphics. And the more groups of data that you need to work with, the harder those tasks become. That’s where RStudio comes in.

For example, imagine you are analyzing sales data for every city across an entire country. That is a lot of data from a lot of different groups–in this case, each city has its own group of data. 

Here are a few ways RStudio could help in this situation:

    Using RStudio makes it easy to take a specific analysis step and perform it for each group using basic code. In this example, you could calculate the yearly average sales data for every city. 

    RStudio also allows for flexible data visualization. You can visualize differences across the cities effectively using plotting features like facets–which you’ll learn more about later on.

    You can also use RStudio to automatically create an output of summary stats—or even your visualized plots—for each group.

As you learn more about R and RStudio moving forward in this program, you’ll get a better understanding of when RStudio should be your data analysis tool of choice.

- https://www.theanalysisfactor.com/the-advantages-of-rstudio/
- https://lgatto.github.io/2017_11_09_Rcourse_Jena/before-we-start.html

- Tidyverse

Functions and arguments

```r
# Comment
print("Hello World")
variable <- "This is my variable"
second_variable <- 12.5

# An array
vec_1 <- c(1, 2, 3, 4.5, 8.9)
```

- Functions
- Comments
- Variables
- Data types
- Pipes
- Vectors

In programming, a data structure is a format for organizing and storing data. Data structures are important to understand because you will work with them frequently when you use R for data analysis. The most common data structures in the R programming language include: 

    Vectors

    Data frames

    Matrices

    Arrays

There are two types of vectors: atomic vectors and lists. Coming up, you’ll learn about the basic properties of atomic vectors and lists, and how to use R code to create them. 
Atomic vectors 

First, we will go through the different types of atomic vectors. Then, you will learn how to use R code to create, identify, and name the vectors. 

Earlier, you learned that a vector is a group of data elements of the same type, stored in a sequence in R. You cannot have a vector that contains both logicals and numerics. 

There are six primary types of atomic vectors: logical, integer, double, character (which contains strings), complex, and raw.


Lists are different from atomic vectors because their elements can be of any type—like dates, data frames, vectors, matrices, and more. Lists can even contain other lists. 

You can create a list with the list() function. Similar to the c() function, the list() function is just list followed by the values you want in your list inside parentheses: list(x, y, z, …). In this example, we create a list that contains four different kinds of elements: character ("a"), integer (1L), double (1.5), and logical (TRUE). 

list("a", 1L, 1.5, TRUE)

Like we already mentioned, lists can contain other lists. If you want, you can even store a list inside a list inside a list—and so on. 

list(list(list(1 , 3, 5)))


Loading tidyverse and lubridate packages

Before you get started working with dates and times, you should load both tidyverse and lubridate. Lubridate is part of tidyverse. 

First, open RStudio. 

If you haven't already installed tidyverse, you can use the install.packages() function to do so: 

    install.packages("tidyverse") 

Next, load the tidyverse and lubridate packages using the library() function. First, load the core tidyverse to make it available in your current R session: 

    library(tidyverse)

Then, load the lubridate package: 

    library(lubridate)

Now you’re ready to be introduced to the tools in the lubridate package. 
Working with dates and times 

This section covers the data types for dates and times in R and how to convert strings to date-time formats.
Types

In R, there are three types of data that refer to an instant in time:

    A date ("2016-08-16")

    A time within a day (“20:11:59 UTC")

    And a date-time. This is a date plus a time ("2018-03-31 18:15:48 UTC")

The time is given in UTC, which stands for Universal Time Coordinated, more commonly called Universal Coordinated Time. This is the primary standard by which the world regulates clocks and time.


Data frames

Data frames are the most common way of storing and analyzing data in R, so it’s important to understand what they are and how to create them. A data frame is a collection of columns–similar to a spreadsheet or SQL table. Each column has a name at the top that represents a variable, and includes one observation per row. Data frames help summarize data and organize it into a format that is easy to read and use. 

A matrix is a two-dimensional collection of data elements. This means it has both rows and columns. By contrast, a vector is a one-dimensional sequence of data elements. But like vectors, matrices can only contain a single data type. For example, you can’t have both logicals and numerics in a matrix. 

To create a matrix in R, you can use the matrix() function. The matrix() function has two main arguments that you enter in the parentheses. First, add a vector. The vector contains the values you want to place in the matrix. Next, add at least one matrix dimension. You can choose to specify the number of rows or the number of columns by using the code nrow = or ncol =. 

## Data frames

Tibbles: streamlined data frames: never change data types of inputs, never change names of your variables, never create row names, and make printing easier bc they will only print 10  rows and as many columns as will fit on screen.

Tidy data: way to standardize data output in R.

str(dataframe) -> stringify
colnames(dataframe) -> column names
mutate(dataframe) makes changes to dataframe
mutate(dataframe, column_name=column/2) add column
head(dataframe) -> preview


load dataset with data function
view it with view


install.packages("here")

data cleaning: install.packages("skimr") skim through data
library("skimr")

janitor package: install.packages("janitor")

penguins %>% select(species)

every column but species: select(-species)

rename(island_new=island) rename island column to island_new


rename_with(penguins, tolower)
clean_names(penguins)

penguins %>% arrange(bill_length_mm) sort by bill length

descending order: arrange(-bill_length_mm)


renaming:

penguins2 <- penguins %>% arrange(-bill_length_mm)

group by function: combined with other functions. Group by island and use summarize function to get mean bill length

penguins %>% group_by(island) %>% drop_na() %>% summarize(mean_bill_length_mm=mean(bill_length_mm))

penguins %>% group_by(island) %>% drop_na() %>% summarize(max_bill_length_mm = max(bill_length_mm))

penguins %>% filter(species == "Adelie") # exactly equal to ==

create a data frame using columns

dataframe <- data.frame(col1, col2, col3, ...)

separate(dataframe, name, into=c("split1", "split2"), sep=" ")
unite(dataframe, "name", first, last, sep=" ")

 
bias function average amount outcome was greater than predicted outcome.

install.packages("SimDesign")

## Visualization

ggplot2 - visualization tool, most popular
 - plotly, rgl, also cool lattice, dygraphs, leaflet, highcharter, patchwork, gganimate, ggridges

"grammer of graphics plot 2"

- aesthetics: visual property of object in plot (size, shape, color)
- geoms: geometric object to represent data
-facets: display smaller groups or subsets
- labels and annotations: customize plot














