# 🏗️ Efficient Download and Extraction of Google Buildings V3 Data

_Detailed blogpost explaining this GitHub repo and scripts can be read here:_ https://sola.kau.se/deprimap/2025/07/23/google-v3-download/

This repository provides a clean two-step pipeline to **download and extract building footprint data from Google Open Buildings V3**, using **only the tiles and geometries that intersect your region of interest (ROI)**.

---

## 🌍 Why This Workflow?

Google’s V3 building dataset is powerful — but downloading and processing all ~178 GB is unnecessary for most use cases. This repo solves that by:

✅ Downloading **only the tiles** that intersect your ROI  
✅ Processing those tiles **in chunks**, extracting **only** relevant buildings  
✅ Saving output as clean `.gpkg` files ready for spatial analysis

---

## 🧭 Workflow Overview

### **Step 1: Identify and Download Tiles**

- Input: ROI polygons (can be single or multiple disjoint features)
- Output: Only those `.geojson.gz` tiles that intersect your ROI
- 📎 Notebook: [`notebook1_download_tiles.ipynb`](notebook1_download_tiles.ipynb)

![step1 selecting tiles](https://github.com/user-attachments/assets/f759f5a8-d85a-4761-9670-41294c6f1098)

The example shows Algeria as an example with multiple polygons spread across the country as an ROI

---

### **Step 2: Filter and Save Buildings**

- Input: Downloaded tiles and your ROI
- Output: GeoPackage (`.gpkg`) with buildings clipped to your ROI
- 📎 Notebook: [`notebook2_filtered_buildings.ipynb`](notebook2_filtered_buildings.ipynb)

⚠️ *Although the tile files have a `.geojson.gz` extension, they are actually CSVs with WKT geometries — not true GeoJSON. This notebook handles that for you.*

![step2 filtering buildings](https://github.com/user-attachments/assets/de1e5a3d-b329-44f2-931f-a7b8bf7ae534)


---

## 🗺️ Example Use Case

You can use this pipeline for:

- Extracting buildings in disjoint polygon boundaries
- Urban change studies (morphometric studies)
- Lightweight local modelling
- Avoiding unnecessary storage/processing overhead

---

## 🙏 Acknowledgements

- Google Research - https://sites.research.google/gr/open-buildings/
- DEPRIMAP Project- https://sola.kau.se/deprimap/
  
_This code was developed as part of the DEPRIMAP project for large-scale urban deprivation analysis._

<img width="373" height="110" alt="image" src="https://github.com/user-attachments/assets/a180a6e3-1b60-429d-b0b8-c14a45e4e190" />
