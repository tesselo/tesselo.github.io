---
layout: post
title:  "Model Alquemy"
author: joao
categories: [ AI, code ]
image: assets/images/our-models.png
description: "An introduction to Tesselo's AI modeling, explaining the model types we used for our mapping with EO data."
featured: false
hidden: false
---
Tesselo's deep learning models are presented in this post. We have used them to
do large scale land cover modeling across the world.

We have packaged our models into a repository that makes it easy
to use Tesselo's most common models. You can find the model references
in our [Alquimodelia](https://github.com/tesselo/alquimodelia) repository.

The aim of Alquimodelia was to create an user friendly and easy way to use and 
change parameters on the common model architectures used in Tesselo. No need of any
knowledge in keras or tensorflow, just some parameters and you had your model ready to use.

Depending on the context and the goal of the modeling, we have used a series of
different models. They range from pixel based classifiers to time-series based
U-Net type architectures.

## Use all bands

For our modeling, we moslty used all available bands of the multispectral satellite
images. For Sentinel-2 we used the 10 bands that have 10m or 20m resolution. Similarly,
for Landsat we used the available bands.

In our pre-processing pipeline we simply resampled all bands into the target resolution.
Usually this meant to upsample the lower resolution bands to the resolution of the
band with the highest resolution. That is 10m for Sentinel-2 images for instance.

Or using the same approuch we would create super-resolution, by upsampling our imagery data
to the resolution of the target data. We had successful models that would build 1m resolution
images out of 10m resolution data.

## Classifiers

Here we are giving a quick overview of the different model types and their use cases.
Detailed posts about some of the models will follow separately as well.

### Pixel based time series classifier

This classifier is quite small but very powerful for small training datasets. It is
non-sequential and based on one-dimensional convolution. It has two branches that
are detecting patterns in time series at different levels.

### Single scene image segmentation

2D U-Net or ResNet based.

#### ResNet

The ResNet architecture uses two-dimensional convolutions to provide a classification to
a given image. This has been used as a way to classify images with a single class. Or it
could be used to classify a single pixel, but with the context of the surroundings.

#### 2D U-Net

The 2D U-Net is similiar to ResNet in terms of the usage of two-dimensional convolutions, but
instead of giving one answer for each image, it responds with also an image.
Used in image classification and segmentation.

### Time series of images

#### 3D U-Net

The 3D U-Net architeture follows the same patterns and the 2D, but instead of two-dimensional convolutions it uses three-dimensional convolutions, multiple images across time.
The answer would still be a single image, but produced with time context.
Great to surpass problems like clouds and other imagery artifacts.
