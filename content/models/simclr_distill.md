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
