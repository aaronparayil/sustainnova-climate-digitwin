# HavaMana Climate Digital Twin

An AI-powered climate digital twin for exploring and forecasting climate conditions in Karnataka, with Bengaluru as the primary pilot location.

The project combines a React + Vite dashboard with a Flask + TensorFlow backend. A ConvLSTM2D model forecasts rainfall, maximum temperature, and minimum temperature, with comparisons against climatology, persistence, and linear-trend baselines.

## Features

- Interactive climate dashboard for the pilot region
- Forecasts for rainfall and temperature
- Model comparison and evaluation metrics
- Spatial metadata and forecast APIs
- Scenario and model exploration views
- Separate frontend and backend development commands

## Technology stack

- **Frontend:** React, Vite, JavaScript
- **Backend:** Flask, Python
- **Machine learning:** TensorFlow, ConvLSTM2D
- **Data:** Gridded climate data and engineered sequences

## Getting started

### Prerequisites

- Node.js 18 or later
- Python 3.11

### Installation

```bash
npm install
pip install -r backend/requirements.txt
```

### Run locally

Start the frontend and backend together:

```bash
npm run dev
```

Or run them separately:

```bash
npm run dev:backend    # Flask API only
npm run dev:frontend   # Vite frontend only
```

The backend runs on port `5005` and the Vite development server provides the frontend.

## Useful commands

```bash
npm run build
npm run lint
```

## Model training and evaluation

```bash
cd backend
python train.py
python evaluate.py
```

Evaluation outputs and figures are written to `backend/outputs/`.

## Project structure

```text
src/                    React frontend
  pages/                Dashboard, model, comparisons, and scenarios
  components/           Globe, terrain, navigation, and UI components
  hooks/                API health and live-condition hooks
backend/
  api/                  Flask API
  data_pipeline/        Data loading and sequence preparation
  models/               ConvLSTM2D model and baselines
  training/             Training workflow
  evaluation/           Metrics and plots
data/                   Climate data documentation and local datasets
```

Large climate-grid files are intentionally excluded from Git. See [`data/README.md`](data/README.md) for data-handling notes.

## API endpoints

| Method | Endpoint | Description |
| --- | --- | --- |
| GET | `/api/health` | API and model status |
| GET | `/api/spatial-metadata` | Region grid coordinates |
| GET | `/api/metrics` | Model evaluation metrics |
| GET | `/api/forecast/date` | Forecast for a selected date |
| GET | `/api/forecast/future` | Forecast for future days |
| GET | `/api/forecast/latest` | Most recent forecast |
| POST | `/api/predict` | Run a custom prediction |

## License

No license has been specified for this repository yet.

## Author

Created by [Aaron Parayil](https://github.com/aaronparayil).
