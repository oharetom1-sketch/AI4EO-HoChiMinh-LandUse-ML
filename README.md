# Machine Learning Detection of Urban Expansion and Vegetation Change Around Ho Chi Minh City Using Sentinel-2

## Project Overview

This project applies remote sensing and machine-learning techniques to Sentinel-2 satellite imagery to classify land cover and investigate environmental change around Ho Chi Minh City, Vietnam, between 2018 and 2026.

The workflow combines spectral index analysis with both unsupervised and supervised machine-learning methods, including K-means clustering and Random Forest classification. The project investigates whether urban expansion and vegetation change, particularly within the coastal mangrove regions surrounding Ho Chi Minh City, can be detected using satellite imagery and AI-based classification approaches.

The analysis was performed using Python in Google Colab with Sentinel-2 Level-2A imagery acquired from the Copernicus Dataspace ecosystem.

---

# Background and Motivation

Ho Chi Minh City is one of the fastest growing urban regions in Southeast Asia. Rapid urban development, population growth, industrial expansion, and coastal land-use change have placed increasing pressure on surrounding ecosystems, particularly mangrove environments in the Can Gio coastal region.

Mangroves are environmentally significant ecosystems that provide coastal protection, biodiversity support, carbon storage, and sediment stabilisation. Monitoring changes in these environments is therefore important for both environmental management and urban planning.

Traditional field-based environmental monitoring can be time-consuming, expensive, and difficult across large or inaccessible regions. Satellite remote sensing provides a scalable alternative that enables large areas to be analysed efficiently over time.

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

Machine-learning and remote sensing workflows require computational processing that consumes energy and contributes to carbon emissions. This project used Google Colab cloud computing and downsampled imagery to reduce computational demand and memory usage.

Despite this computational footprint, satellite-based environmental monitoring provides substantial environmental advantages compared to traditional field surveys. Remote sensing enables large regions to be monitored efficiently without extensive travel, vehicle use, or field logistics.

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

# Conclusion

This project demonstrates how Sentinel-2 imagery and machine-learning techniques can be used to investigate land-cover classification and environmental change around Ho Chi Minh City.

While K-means clustering provided a useful exploratory baseline, Random Forest classification produced more stable and interpretable results for temporal comparison. The workflow highlights both the potential and limitations of machine-learning approaches in environmental remote sensing applications.

Overall, the project demonstrates how AI and Earth observation data can support scalable environmental monitoring using freely available satellite imagery.
