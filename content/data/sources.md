---
title: "Data Sources"
summary_image: "/images/sentinel2.png"
featured_image: "/images/satellite-imaging.jpg"
summary: "The data for our research are Sentinel-2 multispectral images of earth's surface reflectance sourced from two archives: BigEarthNet-S2 and Sentinel-2A collection from the Copernicus program."
toc: true
---

The data for our research are Sentinel-2 multispectral images of earth's surface reflectance sourced from two archives: BigEarthNet-S2 and Sentinel-2A collection from the Copernicus program. While the former is an annotated  dataset that we use for fine-tuning of our models using supervised learning, the latter is an unlabeled dataset we leverage for pre-training.

{{< figure src="/images/data.png" caption="**Figure 1:** *Example Sentinel-2 images*" >}}

## BigEarthNet-S2

{{< figure src="/images/ben-s21.png" class="center w-70" caption="**Figure 2:** *Sample images with labels from BigEarthNet-S2*" >}}

[BigEarthNet-S2](http://bigearth.net/) is a large scale sentinel benchmark archive consisting of 125 Sentinel-2 tiles, atmospherically corrected and divided into 590,326 non-overlapping image patches. They cover over 10 European countries with each patch annotated by multiple land cover classes that were provided by the [CORINE Land Cover database](https://land.copernicus.eu/user-corner/technical-library/corine-land-cover-nomenclature-guidelines/html)


## Sentinel-2A
Sentinel-2 is an earth observation mission from the European Space Agency. It acquires optical imagery at a high spatial resolution of 10 to 60 metres (m) over land and coastal waters. The S2 multispectral instrument includes 13 bands, which are captured at different spatial resolutions.

{{< figure src="/images/bands.png" caption="**Figure 3:** *Characteristics of the Multi Spectral Instrument on board Sentinel-2*" >}}

[S2 Super-resolution](https://up42.com/blog/tech/sentinel-2-superresolution) algorithm creates a 10 m resolution band for all the existing spectral bands (including those with 20 m and 60 m) using a trained convolutional neural network (CNN). This processing block's output is a multispectral 12 band, 10 m resolution GeoTIFF file. The first band i.e. B1 is discarded since it's only useful for atmospheric correction.

{{< figure src="/images/ca12.png" class="center w-90" caption="**Figure 4:** *Central Valley, CA and regions of Central Valley used in our data*" >}}

We source Sentinel-2A images of the [Central Valley](https://en.wikipedia.org/wiki/Central_Valley_(California)) region of California using the Google Earth Engine API. Central valley is not only California’s most productive agricultural region, but also one of the most productive regions in the world. According to Wikipedia, more than 7 million acres of the valley are irrigated via an extensive system of canals and reservoirs. The valley is also home to many major cities like Sacrameto, Fresno, Bakersfield etc. giving us a good mix of irrigated and non-irrigiated data. We use images covering approximately 5000 sqaure miles of area for our self supervised learning.


## Data Preprocessing

Before we feed our data into our models, we convert them into TFRecords so that our models can read the pixel values of our images via Tensors.

{{< figure src="/images/preprocessing.png" class="center w-80" caption="**Figure 5:** *Preprocessing pipeline to convert raw Sentinel-2 images into tfrecords files*" >}}

We additionally calculate the mean and standard deviation for each band across the Sentinel-2 California dataset, and use the provided statistics for the BigEarthNet dataset. Applying this normalization step adds the advantage of bringing the bands' data ranges closer together and allows us to perform image augmentations across the whole image rather than having to apply unique or custom augmentations per channel.
