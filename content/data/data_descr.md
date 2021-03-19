---
title: "Data"
featured_image: "/images/sentinel2_france_1920.jpg"
<!-- toc: true -->
---

The data for our research are Sentinel-2 multispectral images of earth's surface reflectance sourced from two archives: BigEarthNet-S2 and Sentinel-2A collection from the Copernicus program. While the former is an annotated  dataset that we use for fine-tuning of our models using supervised learning, the latter is an unlabeled dataset we leverage for pre-training.

### BigEarthNet-S2

![bens21](/images/ben-s21.png)

[BigEarthNet-S2](http://http://bigearth.net/) is a large scale sentinel benchmark archive consisting of 125 Sentinel-2 tiles, atmospherically corrected and divided into 590,326 non-overlapping image patches. They cover over 10 European countries with each patch annotated by multiple land cover classes that were provided by the [CORINE Land Cover database](https://land.copernicus.eu/user-corner/technical-library/corine-land-cover-nomenclature-guidelines/html)


### Sentinel-2A

![cvCal](/images/ca2.png)

We source Sentinel-2A images of the Central Valley region of California using the Google Earth Engine API. Central valley is not only California’s most productive agricultural region, but also one of the most productive regions in the world. According to Wikipedia, more than 7 million acres of the valley are irrigated via an extensive system of canals and reservoirs. The valley is also home to many major cities like Sacrameto, Fresno, Bakersfield etc. giving us a good mix of irrigated and non-irrigiated data. We use images covering approximately 5000 sqaure miles of area for our self supervised learning.


### Data Preprocessing

Before we feed our data into our models, we convert them into TFRecords so that our models can read the pixel values of our images via Tensors.

![dataprocess](/images/preprocessing.png)
