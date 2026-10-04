# Data directory

This project expects the large source dataset at:

```text
data/wave_functions.csv
```

The file must contain at least 113 columns. The first 112 are treated as predictors and column 113 as the target. The analysis reads a large slice of the source file before drawing a smaller modelling sample.

The historical project materials do not provide a stable public download URL, source version or checksum for the original wave-function dataset. This repository therefore documents the exact file layout and schema without claiming that the raw data can be reconstructed from a public download. If you have the original project data, record its provenance and checksum alongside any reproduced benchmark results.

Keep this filename and location, or update `data_path` in [`../h2o_autoencoder_pipeline.Rmd`](../h2o_autoencoder_pipeline.Rmd).
