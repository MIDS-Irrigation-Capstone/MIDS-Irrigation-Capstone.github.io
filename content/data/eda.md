---
title: "Exploratory Analysis"
description : "Exploratory Data Analysis of BigEarthNet-S2 data"
featured_image: "/images/sentinel2_france_1920.jpg"
summary: "An exploratory analysis on the data to understand the distributions for irrigated data as well as identify additional features that can help with irrigation detection."
layout: single
recent_copy: Recent Updates
---

We perform an exploratory analysis on our data to get better insights into understanding the distributions for irrigated land in our labeled data set and identifying potential features that might enhance our ability to distinguish between permanently irrigated land from those that are not. We also explore pre-processing techniques that will help our models learn better from the data and analyze image augmentations that are more suited to satellite images in the context of irrigation detection

The BigEarthNet-S2 data set covers images from ten European countries: Austria, Belgium, Finland, Ireland, Kosovo, Lithuania, Luxembourg, Portugal, Serbia, Switzerland. These images are annotated with multiple labels. Cultivated land under agricultural use that are either permanently or periodically irrigated, using a permanent infrastructure like irrigation channels, drainage network, spray sprinkler line, rotary sprinkler and additional irrigation facilities are labeled with [*Permanently irrigated land*](https://land.copernicus.eu/user-corner/technical-library/corine-land-cover-nomenclature-guidelines/html/index-clc-212.html). Most of these crops cannot be cultivated without artificial water supply. And these labels do not include sporadically irrigated land. This label is our target label. Only 2.3% of the images in our data are labeled as *Permanently irrigated land*.

![](/images/LabelsCount.png)
*Figure: Distribution of labels in BigEarthNet-S2*

Further reading on the Corine land cover nomenclature showed that there were permanent crops which also potentially included permanently irrigated land and hop plantations but were covered under a different class label. These include [*Vineyards*](https://land.copernicus.eu/user-corner/technical-library/corine-land-cover-nomenclature-guidelines/html/index-clc-221.html), [*Fruit trees and berry plantations*](https://land.copernicus.eu/user-corner/technical-library/corine-land-cover-nomenclature-guidelines/html/index-clc-222.html), [*Olive groves*](https://land.copernicus.eu/user-corner/technical-library/corine-land-cover-nomenclature-guidelines/html/index-clc-223.html) and [*Rice fields*](https://land.copernicus.eu/user-corner/technical-library/corine-land-cover-nomenclature-guidelines/html/index-clc-213.html)

![](/images/rice.png)
*Figure: Rice fields with the irrigation channels between parcels*

Clubbing these above land classes with permanently irrigated land puts the percentage of potentially irrigated land at 6.2%. In our experiments, we compare and contrast our learnings from the pure target labels with those from the extended target labels to see if the latter helps generalize our models better.

![stats](/images/irr_stats.png)
*Figure: Statistics of irrigated land with additional labels*

## Vegetative and Water Canopy Indices

blah blah ...

## Preprocessing of dataset

blah blah ...

## Image augmentations

blah ...
