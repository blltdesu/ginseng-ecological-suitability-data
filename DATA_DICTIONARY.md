# Data dictionary

## Processed occurrence tables

The files under `data/occurrence/` preserve the names of the source processing stages. `occurrence_standardized.csv` contains 922 standardized GBIF records, `occurrence_noncultivated_candidate.csv` contains the filtered candidates, and `occurrence_thin_5km.csv`, `occurrence_thin_10km.csv` and `occurrence_thin_20km.csv` are the three spatial thinning variants. `occurrence_filtering_flow.csv` gives counts at each filtering step. Free-text locality and collector fields were removed from the public deposit.

| Column | Meaning |
| --- | --- |
| `gbifID` | GBIF occurrence record identifier; resolve at `https://www.gbif.org/occurrence/<gbifID>` |
| `datasetKey` | GBIF source dataset key |
| `countryCode` | Country code supplied by GBIF |
| `decimalLatitude`, `decimalLongitude` | WGS84 coordinates in decimal degrees |
| `coordinateUncertaintyInMeters` | Source coordinate uncertainty, metres; blank if missing |
| `basisOfRecord` | GBIF record category |
| `license` | Licence of the individual source record |
| `taxon_keep`, `coord_valid`, `coord_quality_pass`, `coord_duplicate`, `status_absent`, `cultivation_flag`, `geo_flag`, `is_final_candidate` | Boolean or source processing flags; blank where that stage did not yet compute the flag |
| `coordinate_quality`, `cultivation_reason` | Processing category or reason, where available |

The geographic-flag table has its original four-column format. Boolean fields are text `True`/`False`. Blank numeric fields indicate missing source values. Consult the matching code's preprocessing scripts for exact filtering rules.

## Rasters and models

`MANIFEST.csv` records each GeoTIFF's CRS, dimensions, number of bands, data type, nodata value and six affine-transform coefficients. Predictor units and class encodings are defined in the matching analysis code and result tables; **do not infer units from file names alone**. The aligned predictor stack contains 19 WorldClim bioclimatic variables, 7 soil variables and 4 terrain variables, plus a grid template and common-validity mask.

The `*.joblib` files are Python serialized models; load them only in a trusted environment with compatible versions from the code repository's `requirements.txt`. They are not interoperable across arbitrary Python/library versions.

## Integrity

`MANIFEST.csv` lists SHA-256 checksums for the individual deposited files. `ASSETS.json` lists SHA-256 checksums and sizes of the release ZIP archives. Restore all ZIPs to one directory to recover the original stage-relative paths.
