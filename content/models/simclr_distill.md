---
date: 2021-04-06
title: "SimCLR-S2 Stage 3: Distillation"
description: "Teacher/Student Knowledge Transfer"
featured_image: "/images/farmland-simclr.jpg"
summary_image: "/images/distillation.jpg"
summary: In the final set of the SimCLR-S2 process we perform knowledge distillation to attempt to gain similar performance to the big ResNet152 model with fewer parameters. While it is possible to use some labeled data during distillation we experimented with a completely self-supervised approach.
toc: true
---


{{< figure src="/images/simclr-3.png" >}}

## Training

In this workflow, we use the supervised fine-tuned model from the previous stage as a teacher, in a knowledge distillation process to teach labels for training the student network on an architecture of similar or smaller size.

The process of distill learning requires the use of a fine-tuned model to provide the training labels to a student model, rather than labels coming from the dataset. This allows a student model to learn on vast amounts of unlabelled data, and in our experiements we analyzed the effectiveness of distillation to models of varying sizes, from models with larger parameter counts like ResNet152 to Xception.

We started with 36 models fine tuned on RestNet152 architecture from stage 2. Each of these models was trained on 5 different convolutional neural networks: Xception, Inception, ResNet50, ResNet101v2 and ResNet152 giving us a total of 180 models.

{{< table caption="**Table 1:** *Model parameters for the different CNN architectures we distilled with*">}}
|CNN Architecture|Model Parameters (million)|
|:-------------------:|:-----------------------:|
|Xcepion|22.9|
|InceptionV3|23.8|
|ResNet50|25.6|
|ResNet101v2|44.6|
|ResNet152|60.4|
{{< /table >}}

## Observations

We observed that even the smallest model Xception, with 22.9 million parameters, benefited from distillation with an improved F1 score for data splits from 3% and above. We also observed that distillation scores were better for smaller data sizes on many architectures.

Another interesting observation was the difference between using the Adam optimizer vs stochastic gradient descent(SGD), where larger percentage splits in the balanced labelling performed significatly better with the Adam pretrained models than with the SDG model. Meanwhile with the expanded labels, SDG pretrained models consistently performed better than those trained with the Adam based pretrained model.

We were also shocked to see the consistent decline in performance for the 100% splits, and feel we can attribute this to overfitting as we did not employ any early stopping in the distill training process as we were able to in the fine-tune step.

To view and filter through our distillation results click [here](../../results/distill/).
