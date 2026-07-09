<div align="center">

# LOVSUN — Intelligence Engine

> **Which swimwear style to produce, in which market, and when — before the season starts?**

<br>

![Python](https://img.shields.io/badge/Python-3.10-3776AB?style=flat-square&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-ResNet18-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-REST_API-000000?style=flat-square&logo=flask&logoColor=white)
![statsmodels](https://img.shields.io/badge/statsmodels-Holt--Winters-4B8BBE?style=flat-square)
![Leaflet](https://img.shields.io/badge/Leaflet.js-Dashboard-199900?style=flat-square&logo=leaflet&logoColor=white)

<br>

> End-to-end visual intelligence system combining **Computer Vision**, **time-series forecasting** and **trend scraping** to turn search data into production decisions — every morning, fully automated.

</div>

---

## How it works

```
Google Trends  ──►  Forecasting  ──►  Visual Model  ──►  REST API  ──►  Dashboard
  pytrends          Holt-Winters       ResNet18 · 13c      Flask        Leaflet.js
```

The pipeline runs daily at **06:00** and produces a `latest_daily.json` with:

- 🏆 Winning style of the day
- 📈 Weekly percentage variation
- 🌍 Priority market
- ⚡ Recommended stock action

---

## Modules

### 🔍 Scraper — Google Trends
Extracts search data for **5 swimwear categories** across multiple countries using `pytrends`. Normalizes and stores the time series for the forecasting module.

### 📈 Forecasting — Holt-Winters
Applies triple exponential smoothing over historical series to project trends **4–8 weeks** ahead. Generates a composite score per style that feeds the final recommendation.

### 🧠 Visual Model — ResNet18
Convolutional network fine-tuned on a swimwear dataset:
- **13 classes** of specific styles
- **5 macro-styles**: triangle, asymmetric, bandeau, sporty, classic bikini
- Classification + top-3 confidence per image

### ⚡ REST API — Flask
```
GET  /winner      →  winning style + recommended market of the day
POST /analyze     →  visual classification of a garment (image)
GET  /forecast    →  trend projection for a given style
```

### 🗺️ Dashboard — Leaflet.js + Chart.js
Interactive visualization with a search heatmap by city and real-time trend charts.

---

## Tech stack

| Layer | Technology |
|:---|:---|
| Computer Vision | PyTorch · ResNet18 fine-tuned |
| Forecasting | statsmodels · Holt-Winters |
| Scraping | pytrends · Google Trends API |
| Backend | Flask · REST API |
| Frontend | Leaflet.js · Chart.js |
| Pipeline | Python daemon · cron 06:00 |

---

## Project structure

```
lovsun-Intelligence/
│
├── scraper/              # Google Trends scraping
│   └── trends_scraper.py
│
├── forecast/             # Holt-Winters forecasting
│   └── forecaster.py
│
├── model/                # ResNet18 classifier
│   ├── train.py
│   └── predict.py
│
├── server/               # Flask REST API
│   └── app.py
│
├── dashboard/            # Leaflet.js + Chart.js frontend
│   └── index.html
│
├── pipeline.py           # Daily orchestrator (06:00)
└── latest_daily.json     # Pipeline output
```

---

## Live demo

🔗 **[View project presentation →](https://thaisbrandao.github.io/lovsunIntelligence/)**

---

<div align="center">

**Thaís Brandão**  
[LinkedIn](https://www.linkedin.com/in/thaisbrandão/) · tjsbrandao@gmail.com

</div>
