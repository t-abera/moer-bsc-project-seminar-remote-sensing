---
title: "Example: LidR I/O and clipping"
---


Since LiDAR data can have quit large file sizes and need some processing power,
we only take a look at a small example area. This area was created with the script below.
It only uses simple Input / Output commands as well as `lidR::lasclip` which is the aquivalent to `terra::crop`.


```yaml
library(lidR)

library(sp)
library(rgdal)


# load in sample area. 
a = readOGR("data/lidarArea.gpkg")


# full lidar set (needs around 12 GB in RAM)
mof = readLAS("data/raw/mof_lidar_2018.las")

# Check if the crs for study area "a" and lidar data "mof" are the same. If not, project "a" to the lidar "mof" crs. 

SpatVector
# crop out the sample area
sub_mof = clip_roi(mof, a)

# it still takes 921 mb RAM


# clean up the RAM
rm(mof) # removes a object from R
gc() # "garbage collector" -> cleans up the RAM


writeLAS(sub_mof, "/data/lidar/lidar_2018_clipped.las")

```

