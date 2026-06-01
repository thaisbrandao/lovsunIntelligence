# LOVSUN — Intelligence Engine

> **¿Qué bikini producir, en qué mercado y cuándo — antes de que empiece la temporada?**
<br>

![Python](https://img.shields.io/badge/Python-3.10-3776AB?style=flat-square&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-ResNet18-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-REST_API-000000?style=flat-square&logo=flask&logoColor=white)
![statsmodels](https://img.shields.io/badge/statsmodels-Holt--Winters-4B8BBE?style=flat-square)
![Leaflet](https://img.shields.io/badge/Leaflet.js-Dashboard-199900?style=flat-square&logo=leaflet&logoColor=white)

<br>

> Sistema de inteligencia visual end-to-end que combina **Computer Vision**, **forecasting de series temporales** y **scraping de tendencias** para convertir datos de búsqueda en decisiones de producción — cada mañana, de forma completamente automatizada.

</div>

---

## ¿Cómo funciona?

```
Google Trends  ──►  Forecasting  ──►  Modelo Visual  ──►  API REST  ──►  Dashboard
  pytrends          Holt-Winters       ResNet18 · 13c       Flask        Leaflet.js
```

El pipeline se ejecuta diariamente a las **06:00** y genera un `latest_daily.json` con:

- 🏆 Estilo ganador del día
- 📈 Variación porcentual semanal  
- 🌍 Mercado prioritario
- ⚡ Acción recomendada de stock

---

## Módulos

### 🔍 Scraper — Google Trends
Extrae datos de búsqueda para **5 categorías de moda de baño** en múltiples países usando `pytrends`. Normaliza y almacena las series temporales para el módulo de forecasting.

### 📈 Forecasting — Holt-Winters
Aplica suavizado exponencial triple sobre las series históricas para proyectar tendencias a **4–8 semanas**. Genera un score compuesto por estilo que alimenta la recomendación final.

### 🧠 Modelo Visual — ResNet18
Red convolucional fine-tuned sobre un dataset de prendas de baño:
- **13 clases** de estilos específicos
- **5 macro-estilos**: triángulo, asimétrico, bandeau, deportivo, bikini clásico
- Clasificación + top-3 de confianza por imagen

### ⚡ API REST — Flask
```
GET  /winner      →  estilo ganador + mercado recomendado del día
POST /analyze     →  clasificación visual de una prenda (imagen)
GET  /forecast    →  proyección de tendencia para un estilo dado
```

### 🗺️ Dashboard — Leaflet.js + Chart.js
Visualización interactiva con mapa de calor de búsquedas por ciudad y gráficos de tendencia en tiempo real.

---

## Stack tecnológico

| Capa | Tecnología |
|:---|:---|
| Computer Vision | PyTorch · ResNet18 fine-tuned |
| Forecasting | statsmodels · Holt-Winters |
| Scraping | pytrends · Google Trends API |
| Backend | Flask · REST API |
| Frontend | Leaflet.js · Chart.js |
| Pipeline | Python daemon · cron 06:00 |

---

## Estructura del proyecto

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
├── pipeline.py           # Orquestador diario (06:00)
└── latest_daily.json     # Output del pipeline
```

---

## Demo interactiva

🔗 **[Ver presentación del proyecto →](https://thaisbrandao.github.io/lovsunIntelligence/)**

---

<div align="center">

**Thaís Brandão**  
[LinkedIn](https://linkedin.com/in/thaisbrandao) · tjsbrandao@gmail.com

</div>
