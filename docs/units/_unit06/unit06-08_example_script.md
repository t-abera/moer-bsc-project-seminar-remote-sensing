---
title: 'Example: Putting it all together'
---


## Predictors and observations

Example workflow:


```yaml

library(raster)
library(ranger)
library(caret)
library(RStoolbox)
library(viridis)


# Prepared Sentinel 2 Scene

sen = stack("data/sentinel/lahntal_sentinel_NDVI.tif")
names(sen) <- c("B2", "B3", "B4", "B8", "NDVI")

# Prepared Mean vegetation height (mvh) from Lidar

mvh = raster("data/lidar/mvh.tif")

# Terminolgy: 
## sentinel bands are the predictors
## mvh is the response

# combine mhv with the sentinel bands and convert to a data frame

dset <- stack(crop(sen, mvh), mvh)
plot(dset)

dset <- as.data.frame(dset)


# one row of dset was one cell of the raster, the columns were the different layers of the stack
colnames(dset)
head(dset)

# remove the na values and save the data frame as an R object

dset_clean = na.omit(dset)
saveRDS(dset_clean, "data/sentinel_mvh_dataset.RDS")


# split into train and test
set.seed(1)
train_id <- caret::createDataPartition(y = dset_clean$mvh, times = 1, p = 0.6, list = FALSE)
train_df <- dset_clean[train_id,]
test_df <- dset_clean[-train_id,]

```


## Random Forest modelling

```yaml
# define tuning parameters for ranger
tgrid <- expand.grid(.mtry = 1:5,
                     .splitrule = "variance",
                     .min.node.size = c(5,10,15,20))

# train the model
rfmodel <- caret::train(mvh ~ ., data = train_df, method = "ranger",
                        tuneGrid = tgrid, trControl = trainControl(method = "cv"),
                        num.trees = 200)

```


## Validation


```yaml
# visual validation

# predict on Sentinel
p <- raster::predict(object = sen, rfmodel)
plot(p)

# independent validation

test_df$pred <- stats::predict(object = rfmodel, test_df)
plot(test_df$mvh, test_df$pred)


# Root mean squared error
sqrt(mean((test_df$pred - test_df$mvh)^2, na.rm = TRUE))


```

## Export results


```yaml
# save resulting mean vegetation height
writeRaster(p, "output/vegetation_height_prediction.tif")

# save model
saveRDS(rfmodel, "data/models/ranger_mvh_sen.RDS")

# Create a nice map
png("output/vegetation_height_prediction.png")
RStoolbox::ggR(p, geom_raster = TRUE)+
  scale_fill_gradientn(name = "Vegetation height", colors = viridis(50))+
  theme(axis.text.y = element_text(angle = 90, hjust = 0.5),
        axis.title = element_blank(), legend.position = "bottom", panel.background = element_blank(),
        panel.grid = element_line(color = "grey50"))
dev.off()

```















