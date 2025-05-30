# 🌍 Lake Urmia Multi-Index Environmental Monitoring (2000–2024)

This repository contains fully automated Google Earth Engine (GEE) scripts developed for long-term environmental analysis of the Lake Urmia basin. The approach integrates aerosol, vegetation, water surface, and groundwater indicators using remote sensing data from 2000 to 2024.

---

## 📦 Contents

| File                    | Description |
|-------------------------|-------------|
| `ndwi_processing.js`     | Calculates annual NDWI using Landsat 5, 7, and 8 |
| `ndvi_analysis.js`       | Extracts NDVI from Landsat and computes yearly means |
| `aod_analysis.js`        | Retrieves monthly AOD data from MODIS and exports CSV |
| `grace_storage.js`       | Extracts LWE anomalies from GRACE (JPL, CSR, GFZ solutions) |
| `dust_source_mapping.js` | Identifies frequent dust-emitting zones using AOD > 0.35 |

---

## 🛰️ Data Sources

- **MODIS MCD19A2_GRANULES** – Aerosol Optical Depth (AOD)
- **Landsat 5/7/8 Collection 2** – Surface reflectance (NDVI, NDWI)
- **NASA GRACE** – Groundwater storage anomaly (lwe_thickness)

---

## 🔁 Processing Workflow

```text
1. Define study region (Lake Urmia Basin) and time range (2000–2024)
2. Load MODIS, Landsat, and GRACE datasets in GEE
3. Apply preprocessing: cloud masking, radiometric scaling, AOI clipping
4. Compute:
   - Annual NDWI and NDVI composites
   - Water surface area using NDWI threshold
   - Monthly and annual AOD means
   - GRACE LWE anomalies (JPL, CSR, GFZ)
5. Apply pixel-wise Linear Fit Regression (LFR) for trend detection
6. Map high-frequency dust zones (AOD > 0.35 thresholding)
7. Export trend maps, charts, and CSV summaries
