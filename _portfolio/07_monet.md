---
title: "Monet-Style Painting Generation Using CycleGAN"
excerpt: "Academic project."
collection: portfolio
permalink: /projects/monet/
---

{% include base_path %}

> This was a short academic project in which I collaborated with other two students for the Advanced Machine Learning for Data Science master’s course at IT University of Copenhagen. You can access the repository with the code here: [carobs9/CycleGAN_Monet](https://github.com/carobs9/CycleGAN_Monet)

**General Method and Architecture**

We aimed to learn and analyze the main strengths and challenges of using CycleGANs to generate a Monet-styled painting based on an input photography.

CycleGAN is a commonly used method for image-to-image translation tasks with unpaired training data. The model aims to learn characteristics from images (in this case, Monet paintings) and translate them into other images.

We implemented the CycleGAN architecture following the Pix2Pix (paired image-to-image translation) architecture. Unlike Pix2Pix models, Cycle GANs use two generators and two discriminators to achieve results, as well as instance normalization instead of batch normalization.

**Data Augmentation**

As there was a class imbalance between the Monet training pictures (240) in comparison to real images (5630), we suspected that this could result in poor performance in generating high-quality Monet-style images. To solve this issue, we performed data augmentation on the Monet images training set, which consisted in applying:

- Random jitter in 50 images
- Vertical flip in 50 images
- Random crop in 50 images
- Saturation in 25 images
- Brightness in 25 images

As a result, we generated an extra 200 Monet training images, resulting in a total of 440 Monet training images.

**Hyperparameter Tuning**

We experimented with different learning rates for the discriminators and generators as well as different epochs. 

**Our final model, choice based on the quality of the output images, was trained on 50 epochs and a 0.004 learning rate on both the discriminators and generators.**

**Results**

These are some visualization of the results on the **test set**:

![Test set example 1](/images/monet/test_set_1.png)
![Test set example 2](/images/monet/test_set_2.png)
![Test set example 3](/images/monet/test_set_3.png)

This is a visualization of the output of the model with an image from **outside of the test set**:

![Example outside test set](/images/monet/no_test.png)

