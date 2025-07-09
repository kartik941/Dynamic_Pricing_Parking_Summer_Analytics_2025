# 🚗 Dynamic Pricing Engine for Urban Parking Lots
Capstone Project | Summer Analytics 2025  
created by: ['Kartik Nanda'] 

---

## 📖 Overview

This project implements a **dynamic pricing engine** for urban parking lots using real-time occupancy and traffic data. The goal is to optimize parking prices dynamically based on demand, congestion, and competitor pricing, improving both parking utilization and user satisfaction.

We developed and simulated three progressive pricing models:

- **Model 1 – Baseline Linear Pricing**: Price increases linearly with occupancy.
- **Model 2 – Demand-Based Pricing**: Factors in queue length, traffic conditions, vehicle type, and special days.
- **Model 3 – Competitive Pricing**: Adds geospatial logic to compare nearby lots and suggest rerouting or price corrections.

Real-time simulation was implemented using **Pathway**, and pricing behaviors are visualized using **Bokeh**.

---

## 🛠️ Tech Stack

| Tool            | Purpose                              |
|-----------------|--------------------------------------|
| `Python 3.x`    | Core programming language             |
| `NumPy`         | Numerical computations                |
| `Pandas`        | Data preprocessing & manipulation     |
| `Bokeh`         | Interactive visualizations in Colab   |
| `Google Colab`  | Cloud-based development environment   |

---

## 📐 Architecture Diagram (Mermaid)

```mermaid
graph TD
    A[Dataset.csv] --> B[Preprocessing with Pandas]
    B --> C1[Model 1: Linear Pricing]
    B --> C2[Model 2: Demand-Based Pricing]
    B --> C3[Model 3: Competitive Pricing]

    C1 --> D[Combined Results]
    C2 --> D
    C3 --> D

    D --> E[Bokeh Visualization]
    D --> F[Pathway Real-Time Simulation]

    F --> G[Live Console Price Output]


Project Architecture & Workflow
📥 1. Data Ingestion
The provided dataset contains parking lot status (Occupancy, QueueLength, TrafficConditionNearby, etc.).

Preprocessing joins time fields and encodes categorical columns.

🔁 2. Pricing Models
✅ Model 1 – Baseline Linear Pricing
📈 Price = Base + α × (Occupancy / Capacity)

Simple approach to raise prices proportionally with demand.

Applied per parking lot over time.

✅ Model 2 – Demand-Based Pricing
🧠 Incorporates a weighted demand formula:

ini
Copy
Edit
Demand = α(Occupancy/Capacity) + β(QueueLength) − γ(Traffic) + δ(IsSpecialDay) + ε(VehicleTypeWeight)
Normalized demand is scaled to price range: $5 – $20.

✅ Model 3 – Competitive Pricing
📍 Adds geolocation-based competition logic

Uses the Haversine formula to detect nearby lots.

If a lot is full and nearby prices are cheaper → suggest reroute or reduce price.

If competitors are expensive → opportunity to increase price.

🔄 3. Real-Time Simulation with Pathway
Pathway simulates a stream of parking lot updates from the dataset.

For each update, Model 2 pricing logic is applied live.

Output is shown on the console or stored for further visualization.

📊 4. Visualization with Bokeh
Dynamic prices over time are plotted interactively for each model.

Bokeh enables zooming, panning, and hover-insight for model comparison.
