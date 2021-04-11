---
date: 2021-04-04
title: "SimCLR-S2 Finetune"
description: "Self-Supervised Learning"
featured_image: "/images/farmland-simclr.jpg"
summary_image: "/images/fine-tune.jpg"
toc: true
summary: We leverage a similar approach as the baseline models to finetune our pretrained contrastive learning model. Multiple CNN architectures and data splits are trained as well as some hyper parameter tuning to maximize performance of the fine-tuned model.
---

{{< figure src="/images/simclr-2.png" >}}

In this post, we will explore the phase two of the SimCLR methodology, fine-tuning. This phase will use the contrastive model generated from the pre-training step as a starting point to train a supervised model with various percentages of labeled data.

{{< figure src="/images/finetune_accuracy.png" caption="**Figure 1:** *Finetune accuracy for various models*" >}}

{{< figure src="/images/finetune_accuracy.png" caption="**Figure 2:** *Finetune F1 Scores for various models*" >}}
