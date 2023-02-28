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

## Classifiers

Here we are giving a quick overview of the different model types and their use cases.
Detailed posts about some of the models will follow separately as well.

### Pixel based time series classifier

This classifier is quite small but very powerful for small training datasets. It is
non-sequential and based on one-dimensional convolution. It has two branches that
are detecting patterns in time series at different levels.

### Single scene image segmentation

2D U-Net or ResNet based.

### Time series of images

3D U-Net based.
