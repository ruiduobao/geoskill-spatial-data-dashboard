# Spatial Data Dashboard (geoskill-spatial-data-dashboard)

> Build spatial dashboards combining map layers and statistical charts into HTML

---

## 1. Overview

Summarizes spatial data into a self-contained HTML dashboard: Leaflet map + rendered overlay layers + KPI metric cards + pure-SVG histograms and zone-mean line charts + zonal statistics tables. Charts are drawn with a built-in SVG generator, require no external JS chart library, and can be opened offline.

## 3. Quick Start

```bash
pip install -r requirements.txt
python geoskill-spatial-data-dashboard.py --bbox 116 39 117 40 --synthetic --output-dir ./out
```

## 4. CLI Parameters

Run `python <skill>.py --help` for the full list. Common parameters:

| Parameter | Type | Description |
|---|---|---|
| `--bbox` | `float[4]` | WGS84 bounding box `min_lon min_lat max_lon max_lat` |
| `--input` | `path` | Local input file (GeoJSON/GeoTIFF/etc.) |
| `--output-dir` | `path` | Output directory (default `./output`) |
| `--synthetic` | `flag` | Use synthetic data instead of real input |
| `--quiet` | `flag` | Suppress non-essential stdout |

## 5. Input / Output

| File | Format | Description |
|---|---|---|
| `dashboard.html` | HTML | Dashboard (primary output) |
| `dashboard.json` | JSON | Statistics/histograms/zones (verifiable output) |
| `dashboard_data.tif` | GeoTIFF | Data raster |

Each run also produces `output-manifest.json` (run manifest).

## 6. Technical Principle

raster_histogram/descriptive_stats/zonal_statistics computation → SVG histogram and line-chart generation → render_overlay terrain overlay → Leaflet dashboard assembly.

## 8. License

MIT License. See [`LICENSE`](./LICENSE) for full text.

---

> 中文完整版：[references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)
