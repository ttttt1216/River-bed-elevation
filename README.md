# Hybrid River Rasterization Tool

A Python tool for converting river vectors (Shapefile/GeoJSON) into aligned raster masks using a hybrid area-ratio supersampling method. 

Standard rasterization often forces a binary choice: `all_touched=True` makes rivers "fat", while `all_touched=False` causes narrow streams to disconnect. This tool solves both issues by calculating the exact area-coverage ratio per pixel.

---

## Key Features

- **Area-Ratio Supersampling:** Scales the target grid up by 4x4 sub-pixels, performs fine-grained rasterization, and aggregates back to the original DEM resolution to calculate the exact coverage percentage.
- **Adjustable Threshold:** Dynamically control river thickness via `coverage_threshold` (e.g., `0.3` means a pixel becomes water if $\ge$ 30% of its area is covered).

---

## Requirements

Ensure you have the following Python libraries installed:

```bash
pip install geopandas rasterio numpy
