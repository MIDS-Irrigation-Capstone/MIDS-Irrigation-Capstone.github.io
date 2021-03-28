---
title: "About"
description: "Motivation and SimCLR Background"
recent_copy: Recent Updates
layout: single
featured_image: "/images/about.jpg"
---

- [Purpose]({{<ref "#purpose" >}})
- [Contrastive Learning]({{<ref "#contrastive-learning" >}})
- [SimCLR Framework]({{<ref "#simclr-framework" >}})

## Purpose

As the global population grows so too does agricultural demand. This increase in demand must be monitored carefully since agricultural production relies on the ability to deliver water to croplands. In the case for California, more than nine million acres of farmland, representing roughly 80% of all water used for businesses and homes. Being able to accurately measure our current and anticipated water needs is critical to ensure that water resources are allocated appropriately to meet basic needs.

Historically, monitoring water usage has been a largely manual process which is slow and expensive. As technology has evolved we now see ourselves in a situation where we can leverage satellite imagery and computer vision techniques to classify areas of land that are associated with agriculture and irrigation infrastructure. While automation has certainly increased the velocity at which irrigation patterns can be monitored, it still has a highly manual aspect which is a need for labeled data. The aim of this project is to leverage new capabilities in the computer vision space to classify the presence of irrigation in satellite images with a minimal amount of labeled data.


## Contrastive Learning

The core methodology of our training will leverage contrastive learning to generate a self-supervised model. While typical machine learning models leverage labeled data to identify features that are associated with a label, contrastive learning aims to identify similarities. The basic approach used to train a computer vision model is to apply augmentations to an image and apply a loss function that will minimize the distance between images of the positive class and all other images.

The basic process is to apply random augmentations such as crop, blur, rotation, etc. to a batch of N images which results in a training data set of 2N images. Each image in the training set has a corresponding augmented image and which is referred to as the "positive" class. All other images in the training corpus are part of the "negative" class. As our model learns it will attempt to "attract" the positive class and "repel" the negative class which will ultimately generate a model that maximizes distance between positive and negative classes. The following equation describes how the loss is calculated.

`$$l_{i,j} = -{log} \frac{exp(sim(z_i,z_j)/\tau)}{\sum_{k=1}^{2N}1_{k \ne i} exp(sim(z_i,z_j)/\tau))}$$`


![contrastive-learning](/images/contrastive-learning.gif)
*Figure 1: Contrastive learning methodology*

## SimCLR Framework

![simclr-v2](/images/simCLRv2.png)

