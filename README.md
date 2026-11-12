# Mapping the Seafloor

How much of the ocean floor has been directly measured? This site that tracks progress toward fully mapping the seabed.
It is inspired by the [Seabed 2030](https://seabed2030.org/), the Nippon Foundation–GEBCO project to map the
entire ocean floor from real depth soundings.

**Live site:** https://ocean-mapping-production.up.railway.app

## What counts as "mapped"

GEBCO publishes a global depth grid every year, along with a **Type Identifier (TID) grid** that records how each cell's depth was obtained. This project counts a cell as mapped only if its depth comes from a **direct measurement**:

| TID codes | Source | Counted? |
|---|---|---|
| 10–17 | Direct: singlebeam and multibeam sonar, seismic, lidar, soundings from electronic navigational charts, and similar | Yes |
| 40–46 | Indirect: satellite-gravity predictions, interpolation between soundings, iceberg draft, and similar | No |
| 70–72 | Unknown or mixed source | No |
| 0 | Land | Excluded from the total |

Most of GEBCO's grid is filled in with satellite-gravity estimates, which are useful
but have low accuracy.

## Running it locally

Pipeline:

```sh
cd pipeline
uv sync
uv run python -m ocean_pipeline.cli --years 2019 2020 2021 2022 2023 2024 2025 2026
```

Website:

```sh
cd web
npm install
npm run dev
```

## Data and attribution

- **Bathymetry and TID grids:** [GEBCO](https://www.gebco.net/) Compilation Group,
  downloaded from the [CEDA](https://catalogue.ceda.ac.uk/) archive. Placed in the
  public domain by the Nippon Foundation–GEBCO Seabed 2030 Project.
- **Ocean region boundaries:** Flanders Marine Institute (2021),
  [Global Oceans and Seas, version 1](https://www.marineregions.org/),
  https://doi.org/10.14284/542, CC-BY 4.0. This file isn't downloaded automatically.
  Marine Regions asks that it not be redistributed, so download it yourself and place
  it at `pipeline/data/regions/goas_v01.gpkg`.
- **Basemap:** [OpenFreeMap](https://openfreemap.org/), with map data
  © OpenStreetMap contributors.
