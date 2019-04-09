# STARFM for Python (starfm4py)

Remote sensing image fusion allows the spectral, spatial and temporal enhancement of images. New techniques for image fusion are constantly emerging shifting the focus from pan-sharpening to spatiotemporal fusion of data originating from different sensors and platforms. However, the application of image fusion in the field of Earth observation still remains limited. The number and complexity of the different techniques available today can be overwhelming thus preventing users from fully exploiting the potential of fusion products.

The aim of this study is to make fusion products more accessible to users by providing them with a simple tool for spatiotemporal fusion. This tool will contribute to the better exploitation of data from available sensors making possible to bring the images to the spectral, spatial and temporal resolution required by the user. The fusion algorithm implemented in the tool is based on the spatial and temporal adaptive reflectance fusion model (STARFM) – a well established fusion technique in the field of remote sensing often used as benchmark by other algorithms.


## How to cite?

If you use this code for published work, please cite it using the reference below or the BibTex file provided above:

Mileva, N., Mecklenburg, S. & Gascon, F. (2018). New tool for spatiotemporal image fusion in
remote sensing - a case study approach using Sentinel-2 and Sentinel-3 data. In Bruzzone, L. &
Bovolo, F. (Eds.), *SPIE Proceedings Vol. 10789: Image and Signal Processing for Remote
Sensing XXIV*. Berlin, Germany: International Society for Optics and Photonics. doi:
10.1117/12.2327091; https://doi.org/10.1117/12.2327091

## Installation
It is recommended to use the [Anaconda distribution](https://www.anaconda.com/distribution/) for Python 3. Run the below code from the Anaconda prompt by replacing *myenv* with a name of your choice. For exact list of the requirements, check the [requirements file](requirements.txt).
```
conda create -n myenv dask rasterio zarr matplotlib
```

## Usage
Certain degree of similarity between the images is needed before they can be blended. The most common harmonization steps are:
+ **atmospheric correction**; in case a surface reflectance product is not already available, the atmospheric correction will be the first step to be performed; the algorithm to be used depends on the satellite sensor; popular atmospheric correction models for Sentinel-2 and Sentinel-3 (OLCI) are iCor, Sen2Cor, SMAC, etc.
+ **cloud masking**; cloud pixels should be excluded;
+ **re-projection**; all images should be in the same cartographic coordinate system (e.g. WGS84 UTM 30N)
+ **resampling** to same pixel size, that is usually the pixel size of the fine resolution image;
+ **co-registration** of the images; the images should not only have the exact same extent but they should also match on (sub-)pixel level; useful tools for co-registration are AROSICS (https://pypi.org/project/arosics/), GeFolki (https://w3.onera.fr/medusa/gefolki), etc.
+ **bandpass adjustment**; not mandatory, often handled by the fusion algorithm itself;
+ **BRDF normalization** (not mandatory)
