# smart-routes-management
# VYNEX — SMART ROUTES MANAGEMENT
### AI-Powered Traffic Decision-Support Platform

> **"DECISION WITH EVIDENCE"**  
> Transforms raw traffic telemetry into:  
> **DETECT &rarr; DIAGNOSE &rarr; PREDICT &rarr; SIMULATE &rarr; RECOMMEND &rarr; EXPLAIN**

---

## 🚦 Overview

**VYNEX (Smart Routes Management)** is a national hackathon-winning traffic intelligence platform. Unlike standard navigation apps that merely compute shortest geometric paths, VYNEX answers the fundamental operational questions:

1. **What is happening?** (Segment speed, volume, occupancy, and Isolation Forest anomaly flags)
2. **Why is it happening?** (Attribution: capacity pressure, structural bottlenecks, speed collapses)
3. **What is likely to happen next?** (+15, +30, +45 min ML forecasting)
4. **What if conditions change?** (What-if scenario simulations: incidents, closures, surges)
5. **Which route is better?** (Multi-route candidates Route A, B, C evaluated under current and disrupted states)
6. **Why recommend that route?** (Transparent scoring math and evidence-based natural language explanations)

---

## 🏛️ System Architecture

```
RAW DATA
   ↓
DATA UNDERSTANDING (436 Segments, 120 Nodes, 4,320 Timestamps)
   ↓
DETECT (Isolation Forest Outlier Detection)
   ↓
DIAGNOSE (Ranked Root Cause Attribution)
   ↓
PREDICT (+15 / +30 / +45 Min Horizon Forecasting)
   ↓
SIMULATE (What-If Incidents, Closures, Surges)
   ↓
RECOMMEND (Transparent Multi-Criteria Scoring)
   ↓
EXPLAIN (Zero-Hallucination Evidence Generator)
   ↓
HUMAN DECISION
```

---

## 🛠️ Technology Stack

- **Frontend**: React 18, Vite, React-Leaflet, Leaflet, Recharts, Lucide Icons, Vanilla CSS.
- **Backend**: Python 3.14, FastAPI, Pydantic, Uvicorn, HTTPX.
- **Data & ML**: Pandas, NumPy, Scikit-Learn (`IsolationForest`, Ridge Regression), NetworkX.
- **Geospatial**: OpenStreetMap, CartoDB Dark Matter, Haversine spatial bounds, Nominatim abstraction.
- **Live Traffic**: TomTom Traffic Flow API adapter with automatic fallback to high-fidelity dataset mode.

---

## 🚀 Quickstart Guide

### 1. Prerequisites
- Python 3.10+
- Node.js 18+ and npm

### 2. Backend Setup
```bash
cd backend
pip install -r requirements.txt
cp .env.example .env

# Run unit and pipeline verification tests
python -m tests.test_vynex_pipeline

# Start FastAPI server
python -m uvicorn app.main:app --port 8000 --host 127.0.0.1
```
The FastAPI backend runs on `http://127.0.0.1:8000`.  
Swagger API Docs: `http://127.0.0.1:8000/docs`.

### 3. Frontend Setup
```bash
cd frontend
npm install
npm run dev
```
Open `http://127.0.0.1:5173` in your browser.

---

## 🌟 Key Features

1. **Digital Road World**: 436 road segments and 120 nodes centered around the Bengaluru Urban Tech Corridor with complete traffic telemetry (Speed, Flow, Occupancy, Delay, Queue, Congestion Index, Bottlenecks).
2. **Strict Boundary Validation**: Evaluates queries against dataset coverage. Unsupported queries return: `"No supporting traffic dataset found."`
3. **Perception & Anomaly Feed**: Isolation Forest detects multivariate outliers across speed, flow, occupancy, and delay.
4. **Ranked Diagnostics**: Automatically identifies primary and secondary root causes (e.g. Volume-to-Capacity ratio > 0.85).
5. **Route Forecasting**: Projects corridor conditions over $+15$, $+30$, and $+45$ minutes with confidence metrics and Recharts graphs.
6. **Interactive What-If Simulator**: User can choose Major Incidents, Road Closures, Traffic Surges, Lane Reductions, or Weather Slowdowns, set severity, and observe Before vs After route performance.
7. **Transparent Scoring**: Scoring formula is 100% exposed ($35\%$ Travel Time, $25\%$ Congestion, $20\%$ Delay, $10\%$ Reliability, $10\%$ Distance).
8. **Official Decision Report**: Printable executive decision report summarizing evidence, forecasts, and scenario resilience.
9. **1-Click Guided Hackathon Demo**: Automates the 7-step presentation narrative at the click of a button.

---

## 📁 Repository Structure

```
├── backend/
│   ├── app/
│   │   ├── api/          # FastAPI routers and endpoints
│   │   ├── services/     # Data, Route, and Live Traffic services
│   │   ├── ml/           # Isolation Forest, Diagnostics, Forecaster
│   │   ├── routing/      # NetworkX graph and transparent Scorer
│   │   ├── simulation/   # What-If scenario perturbation engine
│   │   ├── explanation/  # Deterministic evidence generator
│   │   ├── schemas/      # Pydantic request/response schemas
│   │   ├── data/         # Synthetic dataset generator & storage
│   │   └── main.py       # FastAPI application gateway
│   ├── tests/            # Test suite for full intelligence pipeline
│   └── requirements.txt
│
├── frontend/
│   ├── src/
│   │   ├── components/   # TrafficMap, RoutePanel, IntelligenceDrawer, Modals
│   │   ├── services/     # REST API client
│   │   ├── App.jsx       # Command-center dashboard
│   │   └── index.css     # Dark command-center styling
│   ├── package.json
│   └── vite.config.js
│
├── data/                 # Canonical raw, processed, and network data
├── docs/                 # ARCHITECTURE.md, API.md, DEMO.md
└── README.md
```

---

## 🔒 Anti-Hallucination Guarantee
All metrics, delays, speeds, and recommendations are strictly calculated from active graph and sensor observations. VYNEX never fabricates artificial traffic values.

