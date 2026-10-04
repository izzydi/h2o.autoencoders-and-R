# H2O Autoencoders in R

An R project exploring **H2O deep-learning autoencoders** for representation learning and dimensionality reduction on high-dimensional wave-function data.

## Primary workflow

[`h2o_autoencoder_pipeline.Rmd`](h2o_autoencoder_pipeline.Rmd) is the audited source. It loads the dataset from a project-relative path, validates the expected 112-predictor-plus-target schema and creates the final held-out test split before any learned preprocessing or model selection.

## Repository contents

- [`h2o_autoencoder_pipeline.Rmd`](h2o_autoencoder_pipeline.Rmd) — audited R Markdown workflow.
- [`data/README.md`](data/README.md) — expected raw-data layout.
- [`R-packages.txt`](R-packages.txt) — direct R package dependencies.
- [`.gitignore`](.gitignore) — local R/H2O and raw-data exclusions.

## Validation design

Architecture and sparsity are selected using a second split created **inside the overall training partition**. The preprocessing used for this search is fitted only on the representation-training subset, and H2O receives the remaining subset as an explicit `validation_frame`.

The grid is ranked by validation MSE. The selected architecture and sparsity coefficient are then used to train a new final autoencoder after preprocessing has been re-fitted on the complete training partition. The held-out test partition is transformed only after these choices have been made and is not used for model selection.

## Methods and tools

The project uses H2O for sparse deep autoencoders and validation-based grid search, `tidymodels`/`recipes` for data splitting and preprocessing, `data.table` for efficient loading, and `ggplot2`/`dplyr` for analysis and visualization.

The workflow includes hidden-layer feature extraction, PCA comparison, architecture/sparsity selection, reconstruction-error inspection and separate train/test embeddings.

## Reproducibility

The current workflow creates every required object inside the document, checks that the raw dataset exists before reading it, uses project-relative paths, sets fixed seeds and requests H2O's reproducible mode. H2O internal standardization is disabled because predictors have already been normalized by a training-fitted recipe.

## Data requirements

The large raw dataset is not stored in this repository. Place it at `data/wave_functions.csv`, as described in [`data/README.md`](data/README.md).

## Running the analysis

1. Install R and a Java runtime compatible with your H2O release.
2. Install packages listed in [`R-packages.txt`](R-packages.txt).
3. Place the dataset under `data/`.
4. Run or knit `h2o_autoencoder_pipeline.Rmd` from top to bottom.

## Scope

This is an experimental representation-learning portfolio project, not a production inference service.
