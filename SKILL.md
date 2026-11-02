---
name: geoskill-spatial-data-dashboard
description: 'Build spatial dashboards combining map layers and statistical charts into HTML'
---

# 空间数据仪表盘 | Spatial Data Dashboard

Aggregates spatial data into a self-contained HTML dashboard: a Leaflet map + rendered overlay layers + KPI metric cards + pure-SVG histogram and zonal-mean line charts + a zonal statistics table.

Charts are drawn by a built-in SVG generator, with no dependency on external JS charting libraries, so the dashboard works offline.

## Core Algorithm / 核心算法

raster_histogram / descriptive_stats / zonal_statistics statistics → SVG histogram and line-chart generation → render_overlay terrain overlay → Leaflet dashboard assembly.

## Dependencies / 依赖

```bash
pip install numpy rasterio scipy matplotlib geopandas shapely pillow
```

## Usage / 使用方法

### Example 1 (Synthetic Data, Offline)

```bash
python geoskill-spatial-data-dashboard.py --bbox 116.0 39.0 117.0 40.0 --synthetic --output-dir ./out
```

### Example 2 (Custom Histogram Binning)

```bash
python geoskill-spatial-data-dashboard.py --input dem.tif --bins 30 --title "watershed dashboard"
```

### Example 3 (Synthetic Mode)

```bash
python geoskill-spatial-data-dashboard.py --bbox 116 39 117 40 --synthetic --bins 24
```

### Example 4 (Custom Title)

```bash
python geoskill-spatial-data-dashboard.py --input dem.tif --title "urban thermal environment"
```

### Example 5 (More Bins to View Distribution)

```bash
python geoskill-spatial-data-dashboard.py --input dem.tif --bins 50
```

## Output / 输出

| File | Format | Description |
|---|---|---|
| `dashboard.html` | HTML | Dashboard (primary output) |
| `dashboard.json` | JSON | Statistics/histogram/zones (verifiable output) |
| `dashboard_data.tif` | GeoTIFF | Data raster |

Each run also produces `output-manifest.json` (run manifest).

## Data Source / 数据源 / Source

Local GeoTIFF / vector files; `--synthetic` mode generates physically consistent simulated data, fully offline.

## Privacy / 隐私声明 / Privacy

- Runs offline by default; `--synthetic` mode requires no network at all.
- All processing is done locally; no user data is uploaded.

## License / License

MIT

---

> 中文完整版：需要时再读 [references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)，不要默认全量加载。
