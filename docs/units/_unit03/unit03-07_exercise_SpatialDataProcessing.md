---
title: "Exercise: Spatial Data Processing"
---

This exercise will lead you through some of the most basic and important steps for spatial data processing.


## Things you need for this worksheet
  * [R](https://cran.r-project.org/){:target="_blank"} — the interpreter can be installed on any operation system.
  * [RStudio](https://www.rstudio.com/){:target="_blank"} — we recommend to use R Studio for (interactive) programming with R.



## Spatial Data Processing

Create a map of Germany with the following features:

- a raster background map showing elevation data,
- a vector map showing the country boundary,
- use the vector map to clip the raster map,
- map point locations denoting the places of birth of all course participants 
(use a `SpatialPointsDataFrame` object with the correct CRS for this task),
- map the three largest German cities and Marburg with different symbols, and
- get bonus points by adding a legend, rivers, and other cartographic elements as well as
- the distances of the places of birth to Marburg.




Save your R functions and Rmd file in your project structure, knitr it and upload the html file to Ilias.




<!-- funky chunky

watch out
{: .notice--warning}

OMG
{: .notice--info}




## Aerial images of Marburg Open Forest
The aerial images used within this course cover the area of Marburg Open Forest. They are thankfully provided by the [Hessische Verwaltung für Bodenmanagement und Geoinformation (HVBG)](http://www.hvbg.hessen.de/irj/HVBG_Internet){:target="_blank"}. The dataset consists of several tiles which are visualized in the map below in a reduced spatial resolution.

{% include media url="/assets/misc/aerial_images_map.html" %}
[Full screen version of the map]({{ site.baseurl }}/assets/misc/aerial_images_map.html){:target="_blank"}

-->

