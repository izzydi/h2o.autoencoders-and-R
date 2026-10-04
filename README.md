# H2O Autoencoders in R

An R project exploring **H2O deep-learning autoencoders** for representation learning and dimensionality reduction on high-dimensional wave-function data.

## Primary workflow

[`h2o_autoencoder_pipeline.Rmd`](h2o_autoencoder_pipeline.Rmd) is the audited source. It loads the dataset from a project-relative path, validates the expected 112-predictor-plus-target schema and creates the final held-out test split before any learned preprocessing or model selection.

## Repository contents

- [`h2o_autoencoder_pipeline.Rmd`](h2o_autoencoder_pipeline.Rmd) — audited R Markdown workflow.
- [`data/README.md`](data/README.md) — expected raw-data layout and provenance note.
- [`R-packages.txt`](R-packages.txt) — version-pinned direct R dependencies.
- [`.github/workflows/r-ci.yml`](.github/workflows/r-ci.yml) — R 4.6.1 / Java 17 dependency and syntax CI.
- [`.gitignore`](.gitignore) — local R/H2O and raw-data exclusions.

## Validation design

Architecture and sparsity are selected using a second split created **inside the overall training partition**. The preprocessing used for this search is fitted only on the representation-training subset, and H2O receives the remaining subset as an explicit `validation_frame`.

The grid is ranked by validation MSE. The selected architecture and sparsity coefficient are then used to train a new final autoencoder after preprocessing has been re-fitted on the complete training partition. The held-out test partition is transformed only after these choices have been made and is not used for model selection.

## Methods and tools

The project uses H2O for sparse deep autoencoders and validation-based grid search, `tidymodels`/`recipes` for data splitting and preprocessing, `data.table` for efficient loading, and `ggplot2`/`dplyr` for analysis and visualization.

The workflow includes hidden-layer feature extraction, PCA comparison, architecture/sparsity selection, reconstruction-error inspection and separate train/test embeddings.

## Reproducibility

The direct R package versions are pinned in [`R-packages.txt`](R-packages.txt). CI uses R 4.6.1, Java 17 and `pak` to install those exact direct package versions, then extracts and parses the canonical R Markdown source. The pinned H2O R package requires a Java runtime in the supported 8–17 range; Java 17 is used consistently in CI.

The modelling workflow creates every required object inside the document, checks that the raw dataset exists before reading it, uses project-relative paths, sets fixed seeds and requests H2O's reproducible mode. H2O internal standardization is disabled because predictors have already been normalized by a training-fitted recipe.

`R-packages.txt` pins the direct dependencies, but it is not a full `renv.lock`; recursive dependency resolution is handled by `pak`. A lockfile generated from a restored project library can be added later if bit-for-bit package-library restoration is required.

## Data requirements

The large raw dataset is not stored in this repository. Place it at `data/wave_functions.csv`, as described in [`data/README.md`](data/README.md).

## Running the analysis

1. Install R 4.6.1 and Java 17.
2. Install `pak`, then install the pinned direct dependencies:

```r
install.packages("pak")
pak::pkg_install(readLines("R-packages.txt"), upgrade = FALSE)
```

3. Place the dataset under `data/`.
4. Run or knit `h2o_autoencoder_pipeline.Rmd` from top to bottom.

## Scope

This is an experimental representation-learning portfolio project, not a production inference service.
