# Rebuilding the aligned climate predictor layers

The analysis used the 19 bioclimatic variables from **WorldClim 2.1 historical climate, 1970–2000, 2.5 arc-minute resolution**. The 19 aligned `bio01_aligned.tif` through `bio19_aligned.tif` files are absent from this public deposit because [WorldClim's licence](https://worldclim.org/about.html) says its data may not be redistributed without prior permission. The source files are available from [WorldClim's historical climate download page](https://worldclim.org/data/worldclim21.html).

To reconstruct the working stack:

1. Download the 2.5-minute BIO archive directly from WorldClim and extract its 19 GeoTIFFs to a local `数据/气候数据/wc2.1_2.5m_bio/` directory.
2. In the matching [code repository](https://github.com/blltdesu/ginseng-ecological-suitability), update the absolute root paths in `00_统一数据预处理/scripts/06_process_current_climate.py` and `12_align_and_qc.py` for your machine.
3. Run the climate-processing and alignment checks against the included `reference_grid_template.tif` and `common_valid_mask.tif`. Check the output grid against the CRS, dimensions and affine transform recorded in `MANIFEST.csv` for the deposited non-climate predictors.
4. Place the resulting `bio01_aligned.tif` through `bio19_aligned.tif` alongside the non-climate files under the original `实验1/01_input/` structure before running the model code.

The code repository records the processing logic. This document describes the access route; it does not grant permission to redistribute WorldClim's climate rasters.
