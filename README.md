# Machine Learning Detection of Urban Expansion and Vegetation Change Around Ho Chi Minh City Using Sentinel-2

---
## Table of Contents

- [Project Overview](#project-overview)
- [Background and Motivation](#background-and-motivation)
- [Research Question](#research-question)
- [Methodology](#methodology)
- [Study Area and Data Acquisition](#study-area-and-data-acquisition)
- [RGB Visualisation](#rgb-visualisation)
- [Spectral Indices](#spectral-indices)
- [K-means Classification](#k-means-classification)
- [Random Forest Classification](#random-forest-classification)
- [Land-Cover Change Detection](#land-cover-change-detection)
- [Explainable AI: Feature Importance](#explainable-ai-feature-importance)
- [Environmental Cost of the Project](#environmental-cost-of-the-project)
- [Limitations](#limitations)
- [Conclusion](#conclusion)

---
## Project Overview

This project applies remote sensing and machine-learning techniques to Sentinel-2 satellite imagery to classify land cover and investigate environmental change around Ho Chi Minh City, Vietnam, between 2018 and 2026.

The workflow combines spectral index analysis with both unsupervised and supervised machine-learning methods, including K-means clustering and Random Forest classification. The project investigates whether urban expansion and vegetation change, particularly within the coastal mangrove regions surrounding Ho Chi Minh City, can be detected using satellite imagery and AI-based classification approaches.

The analysis was performed using Python in Google Colab with Sentinel-2 Level-2A imagery acquired from the Copernicus Dataspace ecosystem.

![Methodology](figures/Methodology.png)

---

# Background and Motivation

Ho Chi Minh City is one of the fastest growing urban regions in Southeast Asia. Rapid urban development, population growth, industrial expansion, and coastal land-use change have placed increasing pressure on surrounding ecosystems, particularly mangrove environments in the Can Gio coastal region.

Mangroves are environmentally significant ecosystems that provide coastal protection, biodiversity support, carbon storage, and sediment stabilisation. Monitoring changes in these environments is therefore important for both environmental management and urban planning.

Traditional field-based environmental monitoring can be time-consuming, expensive, and difficult across large or inaccessible regions. Satellite remote sensing provides a scalable alternative that enables large areas to be analysed efficiently over time(Lillesand, Kiefer and Chipman, 2015). 

This project explores how machine-learning techniques can be combined with Sentinel-2 imagery to investigate land-cover change using freely available Earth observation data.

---

# Research Question

Can Sentinel-2 imagery and machine-learning methods detect urban expansion and vegetation change around Ho Chi Minh City between 2018 and 2026?

---

# Methodology

The project workflow included:

- Sentinel-2 RGB visualisation
- NDVI calculation for vegetation analysis
- NDWI calculation for water-body identification
- K-means clustering as an unsupervised baseline classifier
- Random Forest classification using pseudo-labels
- Land-cover change detection
- Feature importance analysis for Explainable AI (XAI)

The workflow was implemented entirely in Python using Google Colab.

---

# Study Area and Data Acquisition

The study area focuses on Ho Chi Minh City and the surrounding coastal region of southern Vietnam, including Can Gio. The region contains a mixture of:

- Urban and industrial land
- River systems and coastal water
- Mangrove vegetation
- Sediment-rich coastal environments

Sentinel-2 is a multispectral Earth observation mission operated by the European Space Agency (Drusch et al., 2012).
Sentinel-2 Level-2A imagery was acquired for:

- February 2018
- January 2026

Dry-season imagery was selected to minimise cloud cover and reduce seasonal variability between observations.

---

# RGB Visualisation

## 2018 RGB Imagery

![RGB2018](figures/rgb_2018.png)

## 2026 RGB Imagery

![RGB2026](figures/rgb_2026.png)

RGB imagery was used to visually assess land-cover patterns, river systems, vegetation distribution, and urban development across the study area.

---

# Spectral Indices

## NDVI 2018

![NDVI2018](figures/ndvi_2018.png)

## NDVI 2026

![NDVI2026](figures/ndvi_2026.png)

The Normalised Difference Vegetation Index (NDVI) was used to identify vegetated regions and assess vegetation stability between years.

## NDWI 2018

![NDWI2018](figures/ndwi_2018.png)

## NDWI 2026

![NDWI2026](figures/ndwi_2026.png)

The Normalised Difference Water Index (NDWI) was used to highlight rivers, estuaries, and coastal water bodies.

---

# K-means Classification

## 2018 K-means Classification

![KMeans2018](figures/kmeans_2018.png)

## 2026 K-means Classification

![KMeans2026](figures/kmeans_2026.png)

K-means clustering was applied as an unsupervised baseline classification method using Sentinel-2 Blue, Green, Red, and Near-Infrared bands.

Clusters were interpreted using RGB imagery, NDVI, and NDWI outputs to identify four broad land-cover classes:

- Water
- Vegetation / Mangrove
- Urban / Built-up
- Bare ground / Sediment

Initial change detection using independently trained K-means models produced inconsistent class behaviour between years, highlighting limitations of unsupervised classification for temporal comparison.

---

# Random Forest Classification

## 2018 Random Forest Classification

![RF2018](figures/rf_2018.png)

## 2026 Random Forest Classification

![RF2026](figures/rf_2026.png)

To improve classification consistency, a Random Forest classifier was trained using pseudo-labels derived from the 2018 K-means classification and then applied to both time periods.

This ensured that land-cover classes remained consistent between years and produced more reliable change detection results than independently trained K-means models.

---

# Land-Cover Change Detection

![ChangeMap](figures/Land_Cover_Change.png)

The Random Forest-based change map suggests that most land-cover classes remained relatively stable between 2018 and 2026.

Most detected changes were small and spatially scattered, suggesting localised variability rather than major large-scale urban expansion or mangrove loss.

Some observed variation is likely related to:

- Classification uncertainty
- Tidal stage differences
- Atmospheric conditions
- Surface moisture variation
- Sediment redistribution

---

# Explainable AI: Feature Importance

![FeatureImportance](figures/feature_importance.png)

Feature importance analysis was used to investigate which Sentinel-2 bands contributed most strongly to the Random Forest classification.

The Near-Infrared (NIR) band was identified as the most important feature. This reflects the strong response of vegetation in the near-infrared wavelength region, allowing effective separation between vegetation, water, and built-up land.

---

# Environmental Cost of the Project

Machine-learning and remote sensing workflows require computational processing that consumes electricity and therefore contributes indirectly to carbon emissions. Although this project used relatively lightweight machine-learning methods, computational efficiency still became an important consideration due to the large size of Sentinel-2 imagery.

The original Sentinel-2 raster datasets used in this workflow had image dimensions of approximately 10,980 × 10,980 pixels. Processing imagery of this scale within Google Colab resulted in several memory limitations during early stages of analysis, particularly during RGB visualisation and clustering operations.

To reduce computational demand and improve workflow efficiency, image downsampling was introduced prior to classification. This significantly reduced RAM usage and processing time while maintaining sufficient spatial detail for land-cover analysis.

The project primarily used K-means clustering and Random Forest classification, which are relatively computationally efficient machine-learning approaches compared to deep-learning methods such as convolutional neural networks (CNNs) or Vision Transformers. Total active processing time for the workflow was estimated to remain within approximately 1–2 hours of cloud-based CPU computation.

Despite the computational cost associated with cloud processing and large raster datasets, satellite remote sensing still provides substantial environmental advantages compared to traditional field-based monitoring approaches. Large regions can be monitored repeatedly without requiring extensive travel, transport, or logistical support, allowing environmental change to be assessed at regional scales with comparatively low resource demand.

This project therefore highlights the balance between computational cost and the environmental advantages of scalable Earth observation workflows.
---

# Limitations

Several limitations should be considered:

- The project used pseudo-labels rather than manually validated ground-truth data
- K-means clustering produced inconsistent temporal classifications when trained independently
- Some detected change may reflect environmental variability rather than true land-cover change
- Only four Sentinel-2 bands were used
- The analysis was conducted at reduced spatial resolution to minimise memory usage in Google Colab

Future work could incorporate:

- Ground-truth validation
- Additional Sentinel-2 spectral bands
- CNN or deep-learning approaches
- Higher spatial resolution processing
- Multi-temporal time-series analysis

---

# Key Findings

- K-means clustering provided a useful exploratory baseline but produced inconsistent temporal classifications
- Random Forest classification improved classification consistency between years
- Water and vegetation remained broadly stable between 2018 and 2026
- The Near-Infrared band contributed most strongly to classification performance
- Subtle temporal changes highlighted the challenges of environmental change detection using limited spectral inputs

---

# Conclusion

This project demonstrates how Sentinel-2 imagery and machine-learning techniques can be used to investigate land-cover classification and environmental change around Ho Chi Minh City.

While K-means clustering provided a useful exploratory baseline, Random Forest classification produced more stable and interpretable results for temporal comparison. The workflow highlights both the potential and limitations of machine-learning approaches in environmental remote sensing applications.

Overall, the project demonstrates how AI and Earth observation data can support scalable environmental monitoring using freely available satellite imagery.

---

# References

Chuvieco, E., 2020. Fundamentals of Satellite Remote Sensing: An Environmental Approach. 3rd ed. Boca Raton: CRC Press.

Drusch, M., Del Bello, U., Carlier, S., Colin, O., Fernandez, V., Gascon, F., Hoersch, B., Isola, C., Laberinti, P., Martimort, P. and Meygret, A., 2012. Sentinel-2: ESA’s optical high-resolution mission for GMES operational services. Remote Sensing of Environment, 120, pp.25–36.

ESA, 2024. Sentinel-2 User Handbook. European Space Agency.

Jensen, J.R., 2015. Introductory Digital Image Processing: A Remote Sensing Perspective. 4th ed. Pearson.

Lillesand, T., Kiefer, R.W. and Chipman, J., 2015. Remote Sensing and Image Interpretation. 7th ed. Wiley.

Pedregosa, F. et al., 2011. Scikit-learn: Machine Learning in Python. Journal of Machine Learning Research, 12, pp.2825–2830.

Richards, J.A. and Jia, X., 2006. Remote Sensing Digital Image Analysis. 4th ed. Springer.

Rouse, J.W., Haas, R.H., Schell, J.A. and Deering, D.W., 1974. Monitoring vegetation systems in the Great Plains with ERTS. NASA Special Publication, 351, pp.309–317.

Xu, H., 2006. Modification of normalised difference water index (NDWI) to enhance open water features in remotely sensed imagery. International Journal of Remote Sensing, 27(14), pp.3025–3033.
