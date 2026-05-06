# Machine Learning Detection of Urban Expansion and Vegetation Change Around Ho Chi Minh City Using Sentinel-2

## About The Project

This project uses Sentinel-2 satellite imagery and machine learning to classify land cover around Ho Chi Minh City and the surrounding coastal/mangrove region. The aim is to assess whether urban expansion and vegetation change can be detected between 2018 and 2026.

## Research Question

Can Sentinel-2 imagery and machine learning detect urban expansion and assess vegetation stability around Ho Chi Minh City between 2018 and 2026?

## Methods

The workflow includes:

- Sentinel-2 Level-2A imagery
- RGB visualisation
- NDVI and NDWI calculation
- K-means clustering as an unsupervised baseline
- Random Forest classification using pseudo-labels
- Feature importance analysis
- Land-cover change detection

## Study Area

The study focuses on Ho Chi Minh City and the surrounding coastal region, including Can Gio. This area contains a mixture of urban land, rivers, mangrove vegetation, bare/sediment surfaces and coastal water.

## Land-Cover Classes

| Class | Description |
|---|---|
| Water | Rivers, coast and open water |
| Vegetation / Mangrove | Mangrove, forest and other dense vegetation |
| Urban / Built-up | Buildings, roads and developed land |
| Bare ground / Sediment | Exposed soil, sediment, mudflats and transitional surfaces |

## Key Results

The Random Forest classification produced more consistent land-cover maps than independently fitted K-means clustering. Water bodies and vegetation remained broadly stable between 2018 and 2026. The change map showed mostly localised, pixel-level differences rather than major large-scale land-cover change.

## Limitations

The classification uses pseudo-labels derived from K-means rather than manually validated ground-truth labels. Some change may reflect classification uncertainty, tidal stage, atmospheric conditions, surface moisture or seasonal differences rather than true land-cover change.

## Environmental Cost

The project used Google Colab and downsampled Sentinel-2 imagery to reduce memory demand and computational cost. Although cloud computing has an energy footprint, satellite-based monitoring can reduce the need for field campaigns and allows large areas to be assessed efficiently.
