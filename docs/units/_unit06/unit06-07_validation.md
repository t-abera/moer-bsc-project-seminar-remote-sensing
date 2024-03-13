---
title: "Exercise: Validation"
--- 


## Visual validation

* Use the Sentinel-2 data to predict the mean vegetation height for the entire Lahntal.
* Save the prediction as a tif file and have a look at it with your favorite GIS application.
* What can you say about the quality of the prediction?



## Statistical validation

* Predict the mean vegetation height on your testing set.
* Create a scatterplot with the actual mean vegetation height on the x-axis and the predicted mean vegetation height on the y-axis.

One of the most used error metrics to assess the quality of a model is the `Root Mean Squared Error` or short the `RMSE`.

* How is the RMSE calculated?
* Implement the formula for the RMSE in R and calculate it for your predictions of the test data. How can you interpret this value?
* Divide the RMSE by the mean of the observed vegetation height in the test data. How can you interpret this value?




