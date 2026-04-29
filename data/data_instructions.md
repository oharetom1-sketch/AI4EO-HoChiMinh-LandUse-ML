Sentinel-2 imagery for Ho Chi Minh City and Can Gio.
Target years: 2018 and 2025.

# Data Instructions

## Data Source

This project will use Sentinel-2 Level-2A imagery from the Copernicus Data Space Ecosystem.

Sentinel-2 Level-2A provides atmospherically corrected surface reflectance imagery, making it suitable for land-cover classification and vegetation/water analysis.

## Study Area

Ho Chi Minh City and Can Gio, southern Vietnam.

Approximate bounding box:

- Longitude: 106.55 to 107.10
- Latitude: 10.30 to 10.95

## Target Years

Two time periods will be compared:

- 2018
- 2025

## Image Selection Criteria

Images should be selected using the following criteria:

- Sentinel-2 Level-2A product
- Low cloud cover, ideally less than 10–20%
- Similar season/month where possible
- Coverage of Ho Chi Minh City and Can Gio
- Downloaded as `.SAFE` folders or processed band files

## Bands Used

The main Sentinel-2 bands used in this project will be:

| Band | Wavelength region | Purpose |
|---|---|---|
| B02 | Blue | visible reflectance |
| B03 | Green | water and vegetation contrast |
| B04 | Red | vegetation absorption |
| B08 | Near infrared | vegetation detection |
| B11 | Short-wave infrared 1 | moisture, soil and built-up surfaces |
| B12 | Short-wave infrared 2 | soil, sediment and urban contrast |

## Planned Data Processing

1. Download Sentinel-2 Level-2A imagery for 2018 and 2025.
2. Extract the relevant spectral bands.
3. Resample bands to a common spatial resolution if needed.
4. Crop imagery to the Ho Chi Minh City / Can Gio study area.
5. Stack bands into a multi-band dataset.
6. Use the stacked bands as input features for machine-learning classification.
