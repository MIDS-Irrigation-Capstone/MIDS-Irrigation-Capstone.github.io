---
date: 2021-04-04
title: "SimCLR-S2 Pretraining"
description: "Self-Supervised Learning"
featured_image: "/images/farmland-simclr.jpg"
summary_image: "/images/training-wheels.jpg"
toc: true
summary: The SimCLR-S2 pretraining uses completely unlabeled data and as the starting point to train out computer vision model. In addition to the Big Earth Net data, we will run pretraining against sentinel-2 images captured of the California central valley.
---

{{< figure src="/images/simclr-1.png" >}}

In this post, we will explore the first phase of the SimCLR methodology, pretraining. As stated previously, pretraining leverages unlabeled data by performing a series of augmentations on a batch of images. With the augmented batch, we train a model to maximize the distance between the positive class, the pair derived from the same base, and all other images.


## Augmentation Techniques

## Training
