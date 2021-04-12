---
title: "SimCLR-S2 Distillation"
featured_image: "/images/distill_results.jpg"
summary_image: "/images/distillation.jpg"
summary: Data vizualization of performance results for the distilled models.
---

The following vizualization shows the F1 scores for each data set and percentage of labeled data used during fine-tune training. It is important to note that distillation training is self-supervised and did not use any labelled data.

{{< distill >}}


{{< figure src="/images/distill_1pc_acc.png" caption="**Figure 1:** *SimCLR-S2 distillation accuracy on 1% data split*" >}}


{{< figure src="/images/distill_10pc_acc.png" caption="**Figure 1:** *SimCLR-S2 distillation accuracy on 10% data split*" >}}
