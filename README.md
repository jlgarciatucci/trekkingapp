# TrekkingApp — OSM Route Planner (BRouter + Robust Elevation)


<p align="center">
  <img src="https://github.com/user-attachments/assets/875bed43-7c0d-41ad-a0d5-f55716676cb0"
       alt="TrekkingApp screenshot"
       width="520" />
</p>


A lightweight, client-side route planner built with **Leaflet + OpenStreetMap** that lets you click waypoints, generate hiking/foot/trekking routes via **BRouter** (with an **OSRM foot** fallback), visualize a **robust elevation profile**, and export your route to **GPX / KML / GeoJSON**. Includes a GPX loader, mobile-friendly UI, basemap switcher, and Waymarked Trails overlay.

**Live demo:** https://jlgarciatucci.github.io/trekkingapp/

---

## Features

- **Click-to-route**: add waypoints by clicking on the map.
- **Draggable markers**: drag waypoints to adjust the route.
- **Remove waypoint**: right-click (desktop) / long-press (mobile) a marker to delete it.
- **Routing providers**
  - Primary: **BRouter** profiles (`hiking`, `foot`, `trekking`)
  - Fallback: **OSRM foot** (routing.openstreetmap.de)
- **Elevation profile (robust)**
  - Samples along the route and fetches elevation in batches
  - Provider 1: **OpenTopoData** (dataset auto-select: `eudem25m` for Europe, otherwise `srtm30m`)
  - Fallback: **Open-Elevation**
  - Built-in smoothing (median filter + moving average, “medium”)
  - Shows **min / max / ascent / descent**
  - Hover/touch tooltip: elevation + distance along the route
- **Basemap switcher** (bottom-left): OSM / Satellite / Topo / Dark  
  - Satellite automatically adds Esri boundary/place labels.
- **Waymarked Trails overlay** toggle (hiking trails)
- **Export formats**: GPX (with `<ele>` if available), KML, GeoJSON
- **Load GPX**: drag a GPX track/route into the map (via file picker), using GPX elevations if present.

---

## How to use

1. Open the app: https://jlgarciatucci.github.io/trekkingapp/
2. **Click** on the map to add waypoints.
3. Choose a **Routing profile**:
   - `hiking` → prefers trails
   - `foot` → pedestrian
   - `trekking` → mixed hike/bike style
4. After 2+ waypoints, the route is computed automatically.
5. Check:
   - **Distance badge** (km) in the top panel
   - **Elevation profile** (bottom panel / mobile sheet)
6. Optional:
   - Toggle **Waymarked Trails (Hiking)** for marked hiking routes
   - Switch basemap (OSM/Satellite/Topo/Dark)
7. Export:
   - Enter a **Route name** (used for file names + metadata)
   - Click **Export GPX**, **KML**, or **GeoJSON**
8. Load an existing track:
   - Click **Load GPX** and select a `.gpx` file

---

## Controls & UX tips

- **Add waypoint**: left click on the map
- **Move waypoint**: drag the marker
- **Delete waypoint**: right-click the marker (desktop)  
  - On mobile, use long-press (browser/device dependent)
- **Clear**: removes all waypoints and route
- **Mobile elevation**: use the floating button to show/hide the bottom sheet elevation panel.

---

## Tech stack

- **Leaflet** (map rendering)
- **Turf.js** (distance and geometry utilities)
- Routing services:
  - **BRouter** (GeoJSON format)
  - **OSRM** foot server (fallback)
- Elevation services:
  - **OpenTopoData**
  - **Open-Elevation**
- Hosted via **GitHub Pages**

All logic runs in the browser; no backend required.

---
