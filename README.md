# 🌍 GEE Agriculture Admin Stats for the Joint Monitoring Reports  

Pipeline for processing satellite data in **Google Earth Engine**, masking to agricultural areas, and aggregating values by administrative boundaries. Outputs **per-dataset CSV tables** (e.g., NDVI, FPAR) for one or more countries. Designed for reproducible analysis and easy sharing via GitHub.  

---

## ✨ Features  
- Pulls **public datasets** from Earth Engine (no private assets required).  
- Masks imagery to **agricultural areas** using ESA WorldCover (cropland / rangeland).  
- Aggregates values by **GAUL administrative boundaries** (ADM0 / ADM1 / ADM2).  
- Supports **multiple countries** in a single run.  
- Exports results as **CSV files**, one per dataset.  
- Optionally **pushes outputs to GitHub** directly from Colab.  

---

## 📊 Currently Supported Datasets  
- **MODIS NDVI (MOD13Q1)** — Vegetation index, 250m, monthly composites.  
- **MODIS FPAR (MOD15A2H)** — Fraction of Photosynthetically Active Radiation, 500m, monthly composites.  

*(Easily extendable to Sentinel-2 NDVI, CHIRPS rainfall, ERA5 temperature, etc.)*  

---

## 🚀 Quick Start  

### 1. Open in Google Colab  
- Clone or fork this repo.  
- Open the notebook `gee_admin_pipeline.ipynb` in **Google Colab**.  

### 2. Authenticate with Earth Engine  
- Run the first cell and follow the authentication prompt.  

### 3. Configure Parameters  
Set your country list, date range, admin level, and reducer:  
```python
COUNTRIES = ["Bangladesh", "Malawi"]
ADMIN_LEVEL = 2       # 0=country, 1=ADM1, 2=ADM2
START_DATE = "2024-01-01"
END_DATE   = "2024-12-31"
REDUCER    = "mean"   # mean, median, pctl_25, etc.
MASK_MODE  = "cropland"  # cropland, rangeland, cropland+rangeland
```

### 4. Run the Pipeline  
- For each dataset × country × month, the script generates aggregated values.  
- Outputs are saved as CSV files in `/content/gee_outputs/`.  

### 5. Push to GitHub  
- Set `GIT_ENABLE_PUSH = True` in the notebook.  
- CSVs will be copied into your repo’s `data/` folder and committed automatically.  

---

## 📂 Repo Structure  

```
repo/
├─ notebooks/
│  └─ gee_admin_pipeline.ipynb     # Main Colab notebook
├─ data/                           # Auto-generated CSV outputs
└─ README.md
```

## 📜 License  
MIT License. See [LICENSE](LICENSE) for details.  
