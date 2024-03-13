---
title: Sentinel-2
---

## What is Sentinel-2

Sentinel-2 is a pair of satellite platforms with multispectral sensor instruments (abbreviated MSI) on board.
They cover almost the entire planet with imagery for a particular spot every 5 days.


## What we don't do

Satellite data is determined by the sensor type and its calibration, distortions, atmospheric conditions like aerosols, the cloud situation and many more.
Imagery is usually classified into Levels depending on their preprocessing steps.

The European Space Agency offers Level 1C data for free download. Level 1C means that the images are corrected for sensor effects and solar effects. 
The information in L1C data represents the so called top of atmosphere reflectance (TOA). If we use only a single Sentinel tile and only one point in time, TOA data is sufficient for analyses of the Earth's surface.

![Satellite preprocessing](https://www.researchgate.net/profile/Aurelie_Shapiro/publication/324537528/figure/fig10/AS:631598747746307@1527596284067/An-overview-of-multispectral-satellite-imagery-processing-steps_W640.jpg) 

To compare different points in time or regions, the imagery needs to be atmospherically corrected. The correction steps take the atmospheric conditions like an estimation of the aerosols into account and calculate the so called surface reflectance (SR) of the sensor. 
The algorithms are provided by the ESA in their Sentinel Toolbox (SNAP with sen2cor plugin) or by GIS applications like GRASS GIS.
Fortunately, since last year the ESA also offers Level 2A data for download, which are already atmospherically corrected.   


Therefore, in this course we can focus on actually using Sentinel-2 data in research and Earth observation without worrying too much about technical details and corrections.

## Sentinel-2 Bands

![S2 band overview](https://s3.amazonaws.com/content.satimagingcorp.com/media/cms_page_media/1530/image001.png)



## Where is Sentinel-1?

The Sentinel Program consists of six missions from which four already launched in 2020. An overview of the program can be found [here](https://sentinel.esa.int/web/sentinel/missions){:target="_blank"}.


## Data acquisition

There are multiple places on the internet to download Sentinel-2 data.
For starters we suggest using the [ESA Open Sentinel Hub](https://scihub.copernicus.eu/dhus/#/home){:target="_blank"}.
Here you can select a region, time and what level of data you want and simply download the whole tile. 
Once you are a bit more experienced, also try the R package [sen2R](https://github.com/ranghetti/sen2r){:target="_blank"}.
