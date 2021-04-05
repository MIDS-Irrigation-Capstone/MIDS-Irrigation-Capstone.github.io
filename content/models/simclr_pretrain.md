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

Before any training can commence, we needed to determine how and which augmentations to apply to our satellite images. To identify which augmentations were the most effective, we performed a series of training runs with different combinations of augmentations and ran fine-tuning on the resulting models. Exhaustive training runs were completed with random couplets of the augmentations described in _Table 1_.

{{< table caption="**Table 1:** *Augmentation techniques used for SimCLR pretraining*">}}
|Pixel Augmentations|Geometric Augmentations|
|:-------------------:|:-----------------------:|
|blur|flip|
|brightness|rotation|
|contrast|shift|
|gain|zoom|
|speckle||
{{< /table >}}

_Figure 1_ shows the various augmentations used and the corresponding F1 score of the resulting fine-tuned model. Training was performed on 3% of the data to improve iteration time in running experiments. Based on the results, it was inconclusive which augmentations produced the most effective pre-trained model so we decided to remove the bottom 25% of the augmentations from the average score to be used for the full training runs.

{{< figure src="/images/mean-labeled.png" caption="**Figure 1:** *F1 scores of fine-tuned models based on pretraining augmentations. The figure represents the average score between the regular and extended labels.*" >}}

## Training
