---
title: "Raster Data"
---

Raster data consists of cells or pixels in a seamless grid system and usually contain only one value per cell or pixel.


## Raster data model

Raster data is commonly used to model spatially continuous data such as environmental temperature or elevation.

In contrast to the vector data model, in the raster data model space is always mapped using two- or three-dimensional objects of any shape or size, 
but without overlaps or gaps in a _grid_ system consisting of _cells_. Attributes in the raster data model are stored as values assigned to each cell. 
These values can be linked to a colour palette for creating coloured maps.

{% include figure image_path="/assets/images/raster_robinlovelace.png" caption="The basic concepts of a raster data model. Source: geocompr.robinlovelace.net" %}




Arranging the non-intersecting cells in rows and columns creates an implicit spatial reference of each cell. 
It should be noted that the origin of a raster image always lies in the _upper left corner_ and is usually counted from there by the two run indices i, j. 
As a result, each pixel is uniquely identifiable and an explicit spatial reference is available for each pixel.


{% include figure image_path="/assets/images/ContinousCategorical_robinlovelace.png" 
caption="Raster data model with continuous and categorical  spatial representation. Source: geocompr.robinlovelace.net" %}


However, this spatial concept of a grid system with cells or pixels is not yet located in a defined Cartesian coordinate system or in the real world. 
Such a localisation is necessary for the joint use of raster and vector data, and it is essential for geographically referencing raster cells within the real world. 
Therefore, raster data models are basically also provided with a _Cartesian coordinate system_. 
Note that Cartesian coordinate systems have their origin in the _lower left corner_. 
Grid cells can therefore be identified both by their index and by a Cartesian coordinate system.


{% include figure image_path="/assets/images/grid_CRS_robinlovelace.png" caption="Raster data with different reference systems. Source: geocompr.robinlovelace.net" %}


### More Information

* More detailed information for raster data can be found at [Geocomputation with R - Raster data](https://geocompr.robinlovelace.net/spatial-class.html#vector-data){:target="_blank"}.


<!-- more examples to be added in some bright future -->




