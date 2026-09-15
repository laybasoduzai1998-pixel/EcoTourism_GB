# Pakistan Tourism Intelligence Dashboard — Gilgit-Baltistan

A single-file HTML dashboard covering 205 tourism destinations across Pakistan's 7 administrative units, with a dedicated real-map module for Gilgit-Baltistan (GB).

## Open it

Open `Pakistan_Tourism_Dashboard.html` directly in a browser — it's a self-contained file, no build step or server required for the base experience. (Live map tiles, routing, and district search need internet access, since they call external free APIs at runtime — see below.)

## What's in the GB module

- **Globe-first map** (MapLibre GL JS + OpenFreeMap vector tiles): starts as a resting globe; searching "Gilgit-Baltistan" or any of its districts in the search bar flies the camera in.
- **Overview / Tourist points / Hotels / Routing** — four mutually exclusive layers. Switching fully stops the previous layer (closes popups, clears selection, removes any drawn route) before showing the next.
- **Real district boundaries** — GB's 14 districts, extracted from the official `District_Boundary` shapefile, colour-coded by division (Gilgit / Baltistan / Diamer).
- **366 hotels/guest houses/camp sites** from OpenStreetMap (© OpenStreetMap contributors, ODbL), cross-checked against the district boundaries by point-in-polygon join.
- **Live driving routes** from Gilgit to any destination or hotel, via OSRM (open-source routing, no API key).
- **Climate risk assessment** on every tourist point / hotel popup — flood, heatwave, and oxygen-stress (altitude) indicators, derived from real elevation data (Open-Meteo Elevation API, fetched once and baked into the dataset) plus GB's documented climate/altitude patterns. This is an indicative screening heuristic for travellers, not a hydrological or meteorological model.

## Data files

| File | Contents |
|---|---|
| `Pakistan_Tourism_Dashboard.html` | The dashboard itself (all region data, GB district polygons, and hotel data are embedded inline) |
| `GB_Districts.geojson` | GB's 14 district boundaries, simplified for web use, as a standalone reference copy |
| `GB_Lodging_OSM.json` | The 366 OSM-sourced lodging points, as a standalone reference copy |
| `FCDO_GB_Advisory_Cache_2026-09-14.json` | A dated snapshot of UK FCDO travel-advice text for GB (kept for reference; the live advisory panel was later removed from the dashboard UI) |

## Sources & provenance

- District boundaries: official `District_Boundary` shapefile.
- Lodging: OpenStreetMap contributors, © ODbL.
- Base map: OpenFreeMap (free, keyless vector tiles).
- Routing: OSRM public demo server.
- Elevation: Open-Meteo Elevation API.
