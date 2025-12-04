# SpaceX Falcon 9 First Stage Landing Prediction  
### Data Collection Using API & Web Scraping  
**IBM Data Science Professional Certificate – Applied Data Science Capstone**

---

## 📘 Project Overview
This repository contains the completed notebooks for data collection tasks required for the SpaceX Falcon 9 Landing Prediction project.  
The goal is to build a historical launch dataset using two techniques:

1. **API Data Collection** – pulling structured launch data from the SpaceX REST API.  
2. **Web Scraping** – extracting additional launch records from a static snapshot of a Wikipedia page.

These datasets will be used later for:
- Exploratory Data Analysis (EDA)
- Feature engineering
- Machine learning classification models to predict whether a Falcon 9 first stage will successfully land.

---

## 📁 Repository Contents

### **`spacex_api_data.ipynb`**
Notebook for:
- Requesting SpaceX API data (`/launches/past`)
- Extracting rocket, payload, launchpad, and core details
- Filtering for Falcon 9 launches
- Cleaning missing values
- Exporting `dataset_part_1.csv`

Exports:
