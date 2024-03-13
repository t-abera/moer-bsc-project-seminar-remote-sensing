---
title: "Project management and working environment"
toc: true
toc_label: In this info
---

## A note on data management
Within this course, we will use a variety of datatypes, produce R output and save some (temporary) results, plots and markdown files. Most of the time, data will be used in multiple scripts and subsequent modelling steps.  
An organized file structure from the start will save you many hours, troubles and your mental health!
  

## Working environment
We can give some basic guidelines and recommendations, however in the long term, you have to find a system which works for you!
It is a good idea to have a folder structure like this:

  * top level folder for this course, e.g. *<some-path-to-your-data-disk>\data_analysis*,
  * a *data* folder within your top level folder which also contains a *tmp* folder for temporary files and different subfolders for datasets and/or assignments within this course,
  * a *scripts* folder for all the R scripts.

To make it even more convinient, you can use an R-Project. This ensures, that all the relative file paths in your scripts are consistent within the project.
It is recommended to create a `new R-Project` in a `new directory` out of R-Studio and then create the subfolders within the project directory.

Hence, your data structure could look like this:

```yaml
<some-path-to-your-data-disk>\remote_sensing
  |-- data
    |-- raw
    |-- sentinel
    |-- ...
    |-- tmp
  |-- scripts
    |-- 01_rbasics.R
    |-- ...
    |-- functions
  |-- remote_sensing.Rproj
```


Be aware that a proper organization of the data is the basis for re-use of your data and code as well as for the reproducibility of your analysis. See this R-bloggers contribution by Matt.0 and references therein on [the "gold standard" of data science project management](https://www.r-bloggers.com/the-gold-standard-of-data-science-project-management/){:target="_blank"} (although there might not be such a thing as *one* gold standard).

