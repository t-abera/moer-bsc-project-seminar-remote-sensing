---
title: "A word about classifications" 
---

In this course, we focused on and made use of regression models. We used Random Forest to predict a continuous variable (the mean vegetation height) and also used a continuous error metric, the root mean squared error.
If we do not have a continuous variable to predict (e.g. forest types or more broadly the landcover) we speak of classification models.
No worries! Apart from some minor tweaks, the workflow is exactly the same as with regression models (we even can use the same model type).



```yaml

library(raster)
library(sf)
library(caret)
library(ranger)


setwd("~/casestudies/course_sen_lidar/")

# sentinel are the predictors again
sen = stack("../data/sentinel/lahntal_sentinel_NDVI.tif")
names(sen) <- c("blue", "green", "red", "nir", "ndvi")


# training polygons
lc = st_read("../data/classification/trainingsgebiete.gpkg")

plot(lc["Klasse"])
plotRGB(sen, stretch = "lin"); plot(lc["Klasse"], add = TRUE)
```

## Data cleanup


```yaml
# remove underrepresented classes

table(lc$Klasse)
lc = lc[!(lc$Klasse %in% c("Baum", "kuenstliche flaechen")),]
table(lc$Klasse)

# proj4 != proj6 problematic

projection(sen)
projection(lc)

projection(sen) = projection(lc)
```

## Create data frame

(see: The Modelling workflow)


```yaml
# get pixel values underneath the polygons

val <- extract(sen, lc, df = TRUE)

# create a look-up-table with polygon ID and its class
poly_class <- data.frame(ID = seq(465), Klasse = lc$Klasse)

# add the class information to the pixel values
val <- join(val, poly_class, by = "ID")

# save
saveRDS(val, file = "data/training_set.RDS")
```




## Modelling

```yaml

df = readRDS("../data/classification/training_set.RDS")
head(df)
df$Klasse = droplevels(df$Klasse)
# this is the exact same as with the regression model


head(df)

# delete the polygon ID (for now!)
df$ID = NULL

set.seed(1)
train_id <- caret::createDataPartition(y = df$Klasse, times = 1, p = 0.6, list = FALSE)
train_df <- df[train_id,]
test_df <- df[-train_id,]


# define tuning parameters for ranger

# for classification we need a different split rule!

tgrid <- expand.grid(.mtry = 1:5,
                     .splitrule = "gini",
                     .min.node.size = c(5,10,15,20))

# train the model
rfmodel <- caret::train(Klasse ~ ., data = train_df, method = "ranger",
                        tuneGrid = tgrid, trControl = trainControl(method = "cv"),
                        num.trees = 200)

saveRDS(rfmodel, "../data/classification/lcc_ranger.RDS")
```


## Visuals

```yaml
library(ggplot2)

rfmodel = readRDS("../data/classification/lcc_ranger.RDS")
rfmodel

p = raster::predict(object = sen, rfmodel)

plot(p)
p@data@attributes[[1]]

RStoolbox::ggR(p, geom_raster = TRUE)+
  scale_fill_manual(name = "Classes", values = c("grey", "gold1", "yellow3", "red", "lightgreen", "darkgreen", "blue"))+
  theme(axis.text.y = element_text(angle = 90, hjust = 0.5),
        axis.title = element_blank(), legend.position = "bottom", panel.background = element_blank(),
        panel.grid = element_line(color = "grey50"))
  




```

## Validation

```yaml

test_df$Pred <- stats::predict(object = rfmodel, test_df)

# contingency table
ct = table(test_df$Klasse, test_df$Pred)
ct

# accuracy
# sum of all correct classifications / n

table(test_df$Klasse == test_df$Pred)
sum(test_df$Klasse == test_df$Pred) / nrow(test_df)


# kappa value
# takes into account the class sizes and expected probabilities

# kappa of 0: random classification
# kappa of 1: agreement

kappa(ct)


```











