# Health Facility Access and Data Gaps in Bayelsa State, Nigeria

How many hospitals and clinics in Bayelsa State are within 5 km of a major road, which are most remote, and how does this differ between the eight LGAs?

![LGA choropleth](figures/bayelsa_lga_choropleth.png)

## Key results

| Measure | Result |
|---|---|
| Hospitals and clinics in OpenStreetMap | 31 (19 hospitals, 12 clinics) |
| Within 5 km of a major road | 24 of 31 (77.4%) |
| Median distance to a major road | 0.98 km |
| Yenagoa LGA | 24 of 31 facilities, all within 5 km |
| Ekeremor, Brass, Kolokuma/Opokuma | no facility in OpenStreetMap |

The state figure is driven almost entirely by Yenagoa. Outside the capital every mapped facility is more than 5 km from a major road, and three LGAs have no mapped facility at all.

## Method

1. Overpass API query for `amenity=hospital|clinic` as nodes, ways and relations (`out center`), and motorway, trunk and primary roads with an 11 km margin around the state to avoid edge effects.
2. Reprojection to WGS 84 / UTM zone 32N (EPSG:32632).
3. Duplicate removal, clip to the state, 5 km dissolved road buffer, nearest road distance with `sjoin_nearest`.
4. LGA selection from geoBoundaries ADM2 by interior point test (a plain clip returned 18 slivered "LGAs"; this returns the correct 8).
5. LGA statistics, choropleth (no data shown as hatched, not 0%), interactive Folium map.

## Run it

Open `Health_Facility_Access_in_Bayelsa.ipynb` in Google Colab and choose Runtime > Run all. No uploads or keys are needed. `add_on_cell_static_LGA_map.py` is the cell that saves the static map.

## Limitations

OpenStreetMap is incomplete and urban biased; straight-line distance ignores river transport; LGAs with one or two facilities give unstable percentages.

## Data sources

* OpenStreetMap, © OpenStreetMap contributors, ODbL 1.0
* geoBoundaries ADM1 and ADM2 (Runfola et al., 2020), CC BY 4.0

## Author

**Osaigbovo (Osas) Onaiwu-Nzegwu**, MSc Geoinformatics and GIS Applications, Institute of Space Science and Engineering, African University of Science and Technology (AUST), Abuja.
Email: oonzegwu@gmail.com | LinkedIn: *add your profile link*

This project was completed as MSc coursework for GGA 990 Emerging Technologies in Geoinformatics (lecturer: Dr. Jude A. Adeleke), November 2026. The starter workflow was provided in class; the analysis, extensions, checks and interpretation are my own.

## Licence

Code: MIT Licence. Text and figures: CC BY 4.0. Third party data remain under their own licences (see Data sources).
