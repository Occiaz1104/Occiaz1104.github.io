# Land Cover of Benin City with Machine Learning, with Checked Training Labels

Five-class land cover map of Benin City, Edo State (dry season 2025 to 2026) from Sentinel-2, comparing Random Forest and SVM, with spatial cross-validation and a documented label checking log.

![Land cover map](figures/benin_city_lulc_map.png)

## Key results

| | Random Forest | SVM (selected) |
|---|---|---|
| Overall accuracy | 0.819 | 0.847 |
| Kappa | 0.765 | 0.800 |
| Mean F1 | 0.833 | 0.852 |

Spatial 5-fold cross-validation for SVM: 0.741 (random 5-fold: 0.859). Built-up covers 46.9% of the 441 km² study area, Grass/Crop 41.7%, Trees 8.2%.

**Label check:** 41 of 100 visually checked ESA WorldCover 2021 labels were wrong or unusable, including 19 of 20 Trees. See `figures/sample_checking_log.csv`.

![Accuracy per class](figures/benin_f1_comparison.png)

## Method

Cloud masked Sentinel-2 median composite (14 images); 6 bands plus NDVI, NDWI, MNDWI, NDBI; stratified WorldCover samples; visual checking of 20 per class on high resolution imagery; spectral cleaning of unchecked samples; Random Forest vs RBF SVM on one stratified 70/30 split; random vs block (0.05°) cross-validation; final map in Earth Engine; area table from pixel areas.

## Run it

Open `GGA990_Assignment3_BeninCity_LULC.ipynb` in Colab, set your project ID, run to the checking step, record corrections, then run all.

## Limitations

Labels cleaned with the same indices used as features; water samples clustered in three water bodies; accuracy not area weighted (Olofsson et al., 2014).

## Data sources

* Contains modified Copernicus Sentinel data (2025 to 2026), Google Earth Engine
* ESA WorldCover 2021 v200 (Zanaga et al., 2022), CC BY 4.0
* High resolution imagery for checking: Esri World Imagery (viewing only)

## Author

**Osaigbovo (Osas) Onaiwu-Nzegwu**, MSc Geoinformatics and GIS Applications, Institute of Space Science and Engineering, African University of Science and Technology (AUST), Abuja.
Email: oonzegwu@gmail.com | LinkedIn: *add your profile link*

This project was completed as MSc coursework for GGA 990 Emerging Technologies in Geoinformatics (lecturer: Dr. Jude A. Adeleke), November 2026. The starter workflow was provided in class; the analysis, extensions, checks and interpretation are my own.

## Licence

Code: MIT Licence. Text and figures: CC BY 4.0. Third party data remain under their own licences (see Data sources).
