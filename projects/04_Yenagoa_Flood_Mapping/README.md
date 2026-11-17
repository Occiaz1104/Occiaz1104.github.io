# Mapping the 2022 Yenagoa Flood with Sentinel-1 Radar and a U-Net

Flood extent around Yenagoa, Bayelsa State (15 October to 10 November 2022) from Sentinel-1 VV and VH using a fine-tuned U-Net and change detection, compared with a simple radar threshold, with an honest assessment of what the map misses.

![Flood map](figures/flood_map.png)

## Key results

| | U-Net | VV threshold (< -18 dB) |
|---|---|---|
| IoU / F1, held-out quarter (dry season water) | 0.901 / 0.948 | 0.891 / 0.942 |
| Normal water (km²) | 6.3 | 5.6 |
| Flooded land (km²) | 1.5 | 2.1 |

Agreement between the two flood maps: IoU 0.225. Normal water vs JRC Global Surface Water: IoU 0.825. About 1,675 people (WorldPop 2020) live in mapped flood water; no built-up land was mapped as flooded, although officials reported most streets in Yenagoa LGA under water. Urban double bounce, water under forest canopy and image timing explain most of the gap.

![U-Net vs threshold](figures/flood_map_comparison.png)

## Method

Sentinel-1 GRD IW VV and VH medians with speckle smoothing (dry baseline Dec 2021 to Feb 2022; flood images 18, 25, 30 Oct and 6 Nov 2022); Sentinel-2 MNDWI > 0 water labels; U-Net (ResNet-18 encoder, ImageNet weights) fine-tuned for 40 epochs on 64 x 64 patches with a fixed seed; held-out test quarter moved from the east (0% water) to the west (6.5% water); flooded = flood water AND NOT dry water; same rule applied to the threshold method; JRC GSW, WorldPop and WorldCover checks. `figures/flood_map.tif` is a GeoTIFF (EPSG:32632; 0 land, 1 normal water, 2 flood).

## Run it

Open `GGA990_Assignment4_Yenagoa_Flood.ipynb` in Colab with a T4 GPU runtime, set your project ID, and run all.

## Data sources

* Contains modified Copernicus Sentinel data (2021 to 2022), Google Earth Engine
* JRC Global Surface Water (Pekel et al., 2016)
* WorldPop population 2020, CC BY 4.0
* ESA WorldCover 2021 v200, CC BY 4.0

## Author

**Osaigbovo (Osas) Onaiwu-Nzegwu**, MSc Geoinformatics and GIS Applications, Institute of Space Science and Engineering, African University of Science and Technology (AUST), Abuja.
Email: oonzegwu@gmail.com | LinkedIn: *add your profile link*

This project was completed as MSc coursework for GGA 990 Emerging Technologies in Geoinformatics (lecturer: Dr. Jude A. Adeleke), November 2026. The starter workflow was provided in class; the analysis, extensions, checks and interpretation are my own.

## Licence

Code: MIT Licence. Text and figures: CC BY 4.0. Third party data remain under their own licences (see Data sources).
