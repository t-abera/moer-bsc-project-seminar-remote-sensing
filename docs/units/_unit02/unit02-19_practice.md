---
title: Practice your statistics
--- 

Do the following tasks on your own. Write down questions or difficulties you encountered which we can discuss afterwards.
This will be a refresher for basic statistic.

## Workspace setup

> First, create a new R project in an empty directory. Create folders for `data` and `scripts`.

## Data Input


> Load the famous example dataset `iris` into R. You can find the csv file in the Ilias Course Ressources. Obviously, the file goes into the `data` folder of your environment. The csv file has a header, the separator between columns is a comma (,) and the decimal sign is a dot (.)


Get familiar with the dataset. What is the meaning of each column? What does each row stand for?

![Variable Explanation](https://ars.els-cdn.com/content/image/3-s2.0-B9780128147610000034-f03-01-9780128147610.jpg)



## Descriptive statistics of single variables

1. What is the data type of each column? What does that imply for the analysis?
1. Calculate the average sepal length of all flowers.
1. Calculate the standard deviation of the petal width.
1. Which Iris species are included in the dataset? (`?unique`)


## Subsetting the data

1. Create a new `data.frame` which only includes the species "virginica".
1. Create a boxplot of the petal width of "virginica".
1. What information does the boxplot show you?

Now we want to find out if there is any difference between the petal length of the three flower species.

> Create a boxplot of the petal length. This time we want one box for each species. Use the `~` operator inside the boxplot function.

Is there any difference between the species?

> Calculate the median of the petal length of every species. (`aggregate`)

## Statistics with multiple variables

1. Create a scatterplot with the petal length on the x-axis and the petal width on the y-axis. (`plot`)
1. What does the plot show you?
1. Calculate the correlation coefficient between the petal length and petal width. (`cor`)
1. What does this value tell you?

## Linar model

Look at the scatterplot again. Imagine we want to estimate the petal width of flower with a petal length of 3 cm.

1. Create a linear model with the petal width as a function of the petal length. (`lm(formula = ..., data = ...)`) You have to use the `~` again in the formula.
1. Create the scatterplot with the petal length on the x-axis and the petal width on the y-axis again.
1. Add the visual representation of the linear model to the plot (`abline`).














 





