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
Tesselo's most successful deep learning models are presented in this post. We have
used them to do large scale land cover modeling across the world.

We have packaged our most common models into a repository that makes it easy
to use them. You can find the model references in our
[Alquimodelia](https://github.com/tesselo/alquimodelia) repository. It contains
the detailed model definitions for our most successful models. We used Keras with a
Tensorflow backend for our modeling, so the definitions are written in that famework.

The aim of Alquimodelia is to provide a user friendly way to use and change parameters
on the common model architectures used in Tesselo. The model classes can be created without
deep knowledge of keras or tensorflow. The main required parameters are the input and ouput
shape that the models will work with. Then, Arquimodelia will construct the models accordingly.

## Model types

Depending on the context and the goal of the modeling, we have used a series of
different models. They range from pixel based classifiers to time-series based
U-Net type architectures.

## Use all bands

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

The 3D U-Net architeture follows the same patterns and the 2D, but instead of two-dimensional
convolutions it uses three-dimensional convolutions, multiple images across time.
The answer would still be a single image, but produced with time context.
Great to surpass problems like clouds and other imagery artifacts.
