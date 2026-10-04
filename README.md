# H2O Autoencoders in R

An R project exploring **H2O deep-learning autoencoders** for representation learning and dimensionality reduction on high-dimensional wave-function data.

## Primary workflow

[`h2o_autoencoder_pipeline.Rmd`](h2o_autoencoder_pipeline.Rmd) is the audited source. It loads the dataset from a project-relative path, validates the expected 112-predictor-plus-target schema, creates a stratified hold-out split, fits preprocessing on training data only and passes predictor **names** to H2O rather than relying on fragile column positions.

## Repository contents

- [`h2o_autoencoder_pipeline.Rmd`](h2o_autoencoder_pipeline.Rmd) — audited R Markdown workflow.
- [`data/README.md`](data/README.md) — expected raw-data layout.
- [`R-packages.txt`](R-packages.txt) — direct R package dependencies.
- [`.gitignore`](.gitignore) — local R/H2O and raw-data exclusions.

## Methods and tools

The project uses H2O for sparse deep autoencoders and grid search, `tidymodels`/`recipes` for train/test splitting and training-only preprocessing, `data.table` for efficient loading, and `ggplot2`/`dplyr` for analysis and visualization.

The workflow includes hidden-layer feature extraction, PCA comparison, architecture and sparsity searches, reconstruction-error inspection and separate train/test embeddings.

## Reproducibility

The original source depended on an already-created `df` object. The current version creates every required object inside the document, checks that the raw dataset exists before reading it and disables H2O standardization because predictors have already been normalized by the training-fitted recipe.

## Data requirements

The large raw dataset is not stored in this repository. Place it at `data/wave_functions.csv`, as described in [`data/README.md`](data/README.md).

## Running the analysis

1. Install R and Java.
2. Install packages listed in [`R-packages.txt`](R-packages.txt).
3. Place the dataset under `data/`.
4. Run or knit `h2o_autoencoder_pipeline.Rmd` from top to bottom.

## Scope

This is an experimental representation-learning portfolio project, not a production inference service.
