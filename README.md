# Processed data and model outputs for *Panax ginseng* ecological suitability analysis

This repository contains selected processed inputs and analysis products for the study provisionally titled **“Ecological suitability, future climate responses, and climate-risk zoning for long-term cultivation planning of *Panax ginseng*.”** The matching analysis code is at [blltdesu/ginseng-ecological-suitability](https://github.com/blltdesu/ginseng-ecological-suitability).

## Contents

Small CSV/JSON products are stored in this repository under `data/`. Large binary files are in the [v1.0.0 release](https://github.com/blltdesu/ginseng-ecological-suitability-data/releases/tag/v1.0.0) as eight ZIP assets:

| Asset | Contents |
| --- | --- |
| `aligned_nonclimate_predictors.zip` | 7 aligned soil and 4 terrain predictor GeoTIFFs plus the reference grid and valid-data mask; see [`WORLDCLIM_REBUILD.md`](WORLDCLIM_REBUILD.md) for the 19 climate variables |
| `trained_models_part1.zip`, `trained_models_part2.zip` | Experiment 1 fitted models and Experiment 3 models for future projection |
| `current_and_driver_maps.zip` | Current suitability and spatial driver/contribution maps |
| `future_suitability_summary.zip` | Future ensemble summary, binary suitability and change maps |
| `uncertainty_agreement.zip` | Agreement and uncertainty layers |
| `novelty_stability_loss.zip` | Environmental novelty, future stability and loss layers |
| `vulnerability_and_final_zoning.zip` | Climate vulnerability and the revised Experiment 6B final zoning layers |

Each ZIP preserves the stage-relative path from the original analysis directory. `MANIFEST.csv` lists each deposited file, its SHA-256 checksum, byte size and, for GeoTIFFs, basic grid metadata. `ASSETS.json` records the release ZIP checksums. The small `data/occurrence/` tables keep GBIF record IDs, coordinates, source dataset keys, per-record licences and processing flags; free-text locality and collector fields were omitted. The `data/results/` tables contain model evaluation, interpretation, scenario and final zoning summaries.

To download all release assets with GitHub CLI:

```bash
gh release download v1.0.0 -R blltdesu/ginseng-ecological-suitability-data --dir assets
```

Extract the ZIPs into one directory while preserving their internal paths. See the matching code repository's `REPRODUCIBILITY.md` for the stage order. Its original scripts use Windows paths rooted at `E:\人参种在哪`; adjust them for a different machine.

## Scope and limitations

This is a curated deposit of the processed occurrence records, aligned non-climate predictors, fitted models, model-result tables, and principal derived suitability and zoning layers. WorldClim's licence does not allow redistribution of its climate rasters without permission, so the 19 aligned BIO layers are omitted; the original source and reconstruction route are documented in [`WORLDCLIM_REBUILD.md`](WORLDCLIM_REBUILD.md). The deposit also excludes raw third-party downloads, duplicated handoff packages, individual future-model continuous maps, figures, logs and other intermediate files. The source file `实验5/05_uncertainty_components/mean_SSP_sd.tif` was excluded because it is only 8 bytes and is not a valid raster.

The creators license their original model outputs, analysis tables and derived layers under CC BY 4.0; see [`RIGHTS.md`](RIGHTS.md) for the scope. The occurrence records derive from GBIF and retain each record's original licence, including some noncommercial records. Other source layers were derived from WorldClim 2.1, SoilGrids 2.0, SRTM-derived terrain, MODIS MCD12Q1 land cover and geoBoundaries. Users should cite the original data providers and the exact download records in addition to this processed dataset. The precise GBIF download DOI and some upstream dataset version identifiers were not recorded in the source directory and must be supplied by the authors when the manuscript is finalized.

The repository itself is versioned with release `v1.0.0`. There is currently no DOI for this dataset; use the versioned release URL and the citation metadata in `CITATION.cff` until a repository DOI is issued. The deposited assets should be checked against the final manuscript before submission.
