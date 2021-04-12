---
date: 2021-04-06
title: "SimCLR-S2 Stage 3: Distillation"
description: "Teacher/Student Knowledge Transfer"
featured_image: "/images/farmland-simclr.jpg"
summary_image: "/images/distillation.jpg"
summary: In the final set of the SimCLR-S2 process we perform knowledge distillation to attempt to gain similar performance to the big ResNet-152 model with fewer parameters. While it is possible to use some labeled data during distillation we experimented with a completely self-supervised approach.
toc: true
---


{{< figure src="/images/simclr-3.png" >}}

In this post, we will explore phase three of the SimCLRv2 methodology, distill learning. This phase will use our various fine-tuned models and distill their knowledge to freshly trained models on unlabelled data. 

The process of distill learning requires the use of a fine-tuned model to provide the training labels to a student model, rather than labels coming from the dataset. This allows a student model to learn on vast amounts of unlabelled data, and in our experiements we analyzed the effectiveness of distillation to models of varying sizes, from models with larger parameter counts like ResNet152 to Xception.

Each distill training run was conducted with 50 epochs over a hold-out test dataset that was not previously seen by the teacher fine-tuned models. We also run an evaluation epoch on both the student and teach models, and stored these results for future comparisons.

In total, 180 distill models were trained with each fine-tuned model training on all 5 of the architechures used in this study. To view and filter through our distillation results click [here](../../results/distill/).