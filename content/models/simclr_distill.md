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

In this workflow, we use the supervised fine-tuned model from the previous stage as a teacher, in a knowledge distillation process to teach labels for training the unlabeled student network on an architecture of same or smaller size.

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

We observed that even the smallest model Xception, with 22.9 million parameters, benefited from distillation with an improved F1 score for data splits from 3% and above. We also observed that distillation scores were better for smaller data sizes on many architectures.

{{< figure src="/images/distill_1pc_acc.png" caption="**Figure 1:** *SimCLR-S2 distillation accuracy on 1% data split*" >}}

{{< figure src="/images/distill_10pc_acc.png" caption="**Figure 1:** *SimCLR-S2 distillation accuracy on 10% data split*" >}}
