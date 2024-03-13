---
title: "Exersice: Hyperparameter tuning"
---


Models in machine learning usually have multiple parameters which decide how the model looks like.
A simple example is the slope and intercept of a linar model. One common task in machine learning is to find the optimal set of parameters for a particular dataset.
This is called **hyperparameter tuning**.

![Pimp](https://vignette.wikia.nocookie.net/viva-deutschland/images/2/2a/Maxresdefault-2.jpg/revision/latest/scale-to-width-down/220?cb=20191004132056&path-prefix=de)

_source: vignette.wikia.nocookie.net/viva-deutschland_

In R, the `caret` package provides a convinient framework for the hyperparameter tuning of various kinds of models.

Tasks:

* Train your random forest model again, but this time use `caret::train()`. Make sure you set the parameter `importance = "impurity"` (why?).
* Plot the variable importance of the model with `caret::varImp`.
* Get some information about the hyperparameters of random forest in a publication from [Probst et. al 2019](https://onlinelibrary.wiley.com/doi/abs/10.1002/widm.1301) and the help page of `ranger`. 
* Tune one parameter of your choice by creating a `caret::expand.grid()` and the parameter `tune.grid` in `caret::train()`.
* Plot the resulting model object. What do you see?
* Now train a model where you tune all the hyperparameters.
* Save the model as a RDS file.

