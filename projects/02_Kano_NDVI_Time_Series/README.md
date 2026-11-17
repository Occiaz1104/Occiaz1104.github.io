# A Reusable NDVI Time Series Tool: Irrigated Farmland vs City, Kano State

`ndvi_timeseries(aoi, start_date, end_date, max_cloud=60)` turns the Sentinel-2 archive into a clean monthly NDVI curve for any area and date range, using Google Earth Engine from Python.

![NDVI time series](figures/kano_ndvi_timeseries.png)

## Key results (2025)

| | Kadawa irrigated farmland | Kano city |
|---|---|---|
| Lowest NDVI | 0.27 (Dec) | 0.06 (Aug) |
| Highest NDVI | 0.66 (Oct) | 0.12 (Oct) |
| Seasonal swing | about 0.39 | about 0.06 |

The farmland shows the rainy season crop peak in October and a smaller dry season irrigation peak in February to March. The city barely changes.

![Dry vs rainy season](figures/kano_ndvi_dry_vs_rainy_maps.png)

## Method

Sentinel-2 L2A (`COPERNICUS/S2_SR_HARMONIZED`) filtered by area, date and scene cloud; per pixel cloud, cirrus and shadow masking with the Scene Classification band (classes 3, 8, 9, 10); NDVI; area mean at 20 m; images under 30% clear dropped; monthly means with image counts; empty months kept as gaps.

## Run it

Open `GGA990_Assignment2_NDVI_TimeSeries.ipynb` in Colab, set your Earth Engine project ID, and run all. The function works for any `ee.Geometry`.

## Limitations

One year only; few clear images in July, August and February; the farmland square includes a village, canals and roads.

## Data sources

* Contains modified Copernicus Sentinel data (2025), accessed through Google Earth Engine

## Author

**Osaigbovo (Osas) Onaiwu-Nzegwu**, MSc Geoinformatics and GIS Applications, Institute of Space Science and Engineering, African University of Science and Technology (AUST), Abuja.
Email: oonzegwu@gmail.com | LinkedIn: *add your profile link*

This project was completed as MSc coursework for GGA 990 Emerging Technologies in Geoinformatics (lecturer: Dr. Jude A. Adeleke), November 2026. The starter workflow was provided in class; the analysis, extensions, checks and interpretation are my own.

## Licence

Code: MIT Licence. Text and figures: CC BY 4.0. Third party data remain under their own licences (see Data sources).
