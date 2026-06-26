# 🗺️ Macro Rides — Hyperlocal EV Mobility Engine

### 🚀 Dynamic Route Corridor & Spatial Hexagonal Grid Optimization

An interactive, high-performance geospatial simulation platform designed for **Macro Rides** to optimize last-mile EV fleet dispatching. The application dynamically computes a smooth routing corridor around a live vehicle vector, projects the continuous bounding geometry into an optimized discrete **Uber H3 hexagonal grid**, and screens active passenger pickup hotspots in constant time ($O(1)$ complexity).

---

## 🔗 Live Deployments

* **🖥️ Interactive Production Demo:** [macro-rides-mobility.netlify.app](https://macro-rides-ev.netlify.app/)
* **📁 Source Code Repository:** [github.com/shaswatgithub/macro-rides-mobility](https://github.com/shaswatgithub/macro-rides-mobility)

---

## 🛠️ Core Engineering Stack

The system utilizes a lightweight, frontend-only single-file architecture deployed via secure CDN endpoints to guarantee rapid processing speeds without server-side compute overhead:

* **⬢ Uber H3 (`h3-js`):** Hexagonal hierarchical spatial indexing framework used to discretize irregular continuous coordinates into unique 64-bit address hashes for ultra-fast spatial querying.
* **📐 Turf.js:** Client-side geospatial mathematical library utilized to calculate precise physical spherical buffers and interpolate smooth vehicle route vectors.
* **🗺️ Leaflet.js:** Lightweight open-source mapping canvas used to efficiently render interactive layers, dynamic SVG paths, map tiles, and live asset markers.
* **🌍 OpenStreetMap Nominatim:** Public geocoding interface enabling on-the-fly keyword address resolution and instant engine teleportation worldwide.

---

## ✨ Features & Controls

* **📍 Click-to-Route Workspace:** Click anywhere directly on the map surface to draw a custom route trajectory dynamically for the simulated vehicle.
* **🔍 Typeable Geocoder Engine:** Input any global landmark or campus identifier (e.g., `IIT Kanpur`) to instantly shift operational simulation contexts.
* **🎛️ Dynamic Corridor Slider:** Adjust the driver's catchment buffer radius in real time from `100m` to `1000m`.
* **💎 Variable H3 Resolution Selector:** Toggle between Resolution 8 (~700m), Resolution 9 (~100m), and Resolution 10 (~40m) to evaluate mathematical grid granularity vs lookup performance overhead.
* **📊 Hotspot Density Adjuster:** Inject up to 100 independent passenger terminal nodes using an automated randomized spatial distribution matrix around your operational center.

---

## 🏎️ Data Processing Pipeline

```text
User Location Query
        │
        ▼
OSM Nominatim Geocoding
        │
        ▼
Map Centering & Route Generation
        │
        ▼
Driver GPS Position Updates
        │
        ▼
Turf.js Buffer Generation
        │
        ▼
H3 Spatial Quantization
        │
        ▼
Hexagonal Cell Index Creation
        │
        ▼
Pickup Eligibility Matching
        │
        ▼
Real-Time Visualization
        │
        ▼
Leaflet Map Rendering
```

### Pipeline Overview

1. **Location Search** – User enters any location worldwide, which is converted into geographic coordinates using the OSM Nominatim Geocoder.

2. **Map Initialization** – The map is centered on the selected location and a simulated ride corridor is generated.

3. **Driver Tracking** – The driver's position is continuously updated along the generated route.

4. **Spatial Buffering** – Turf.js creates a dynamic service corridor around the driver's current location.

5. **H3 Quantization** – The corridor is discretized into H3 hexagonal cells for efficient spatial indexing.

6. **Eligibility Filtering** – Pickup locations are mapped to H3 cells and matched against corridor cells using constant-time set operations.

7. **Visualization Layer** – Eligible pickups are highlighted in red, ineligible pickups in gray, and results are rendered in real time using Leaflet.

```
```
