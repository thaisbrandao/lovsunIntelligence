# LOVSUN — Intelligence Engine

> **¿Qué bikini producir, en qué mercado y cuándo — antes de que empiece la temporada?**

Sistema de inteligencia visual end-to-end que combina Computer Vision, forecasting de series temporales y scraping de tendencias para convertir datos de búsqueda en decisiones de producción.

---

## ¿Qué hace?

Cada mañana a las 06:00, un pipeline automatizado ejecuta cinco módulos en secuencia:

1. **Scraper** — extrae datos de Google Trends para 5 categorías de moda de baño en múltiples países vía `pytrends`
2. **Forecasting** — aplica Holt-Winters sobre las series temporales para proyectar tendencias a 4–8 semanas
3. **Modelo visual** — clasifica imágenes de prendas con ResNet18 fine-tuned (13 clases, 5 estilos macro) y genera un score compuesto por estilo
4. **API REST** — expone los resultados vía Flask en tres endpoints principales
5. **Dashboard** — visualiza el mapa de calor de búsquedas y los gráficos de tendencia en tiempo real con Leaflet.js y Chart.js

El output diario es un archivo `latest_daily.json` con el estilo ganador, variación porcentual, mercado prioritario y acción recomendada de stock.

---

## Stack

| Capa | Tecnología |
|---|---|
| Computer Vision | PyTorch · ResNet18 fine-tuned |
| Forecasting | statsmodels · Holt-Winters |
| Scraping | pytrends · Google Trends |
| API | Flask · REST |
| Dashboard | Leaflet.js · Chart.js |
| Pipeline | Python daemon · cron 06:00 |

---

## Endpoints API

```
GET /winner       → estilo ganador del día + mercado recomendado
GET /analyze      → clasificación visual de una prenda (imagen)
GET /forecast     → proyección de tendencia para un estilo dado
```

---

## Estructura del proyecto

```
lovsun/
├── scraper/          # Google Trends scraping (pytrends)
├── forecast/         # Holt-Winters forecasting
├── model/            # ResNet18 classifier + training
├── server/           # Flask REST API
├── dashboard/        # Leaflet.js + Chart.js frontend
├── pipeline.py       # Orquestador diario (06:00)
└── latest_daily.json # Output del pipeline
```

---

## Demo

Abre `index.html` en el navegador para ver la presentación interactiva del proyecto.

---

## Autora

**Thaís Brandão** · [LinkedIn](https://linkedin.com/in/thaisbrandao) · tjsbrandao@gmail.com
