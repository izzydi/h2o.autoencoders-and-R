# H2O Autoencoders in R

An R project exploring **H2O deep-learning autoencoders** for representation learning, dimensionality reduction and anomaly-oriented analysis on high-dimensional wave-function data.

## Project overview

The workflow is self-contained: it loads the source data, creates a labelled sample, performs a stratified train/test split, learns preprocessing from the training data only, starts a local H2O instance and trains sparse autoencoders. The learned representation is compared with PCA and explored through architecture and sparsity grid searches.

## Repository contents

- [`h2o_autoencoder_pipeline.Rmd`](h2o_autoencoder_pipeline.Rmd) — complete reproducible R Markdown workflow.
- [`data/README.md`](data/README.md) — expected raw-data layout.
- [`.gitignore`](.gitignore) — local R/H2O and raw-data exclusions.

## Methods and tools

The project uses:

- `h2o` for deep autoencoders and hyperparameter search,
- `tidymodels`/`recipes` for train/test splitting and preprocessing,
- `data.table` for efficient loading of a large CSV,
- `dplyr` for data manipulation,
- `ggplot2` for visualisation.

The analysis includes stratified sampling and splitting, training-only transformation and normalization, sparse autoencoder training, hidden-layer feature extraction, PCA comparison, architecture and sparsity searches, reconstruction inspection and train/test embeddings.

## Reproducibility

The original source depended on an already-created `df` object. The current version loads the dataset explicitly from a project-relative path and creates every object required by the workflow.

## Data requirements

The large raw dataset is not stored in this repository. Place it at `data/wave_functions.csv`, as described in [`data/README.md`](data/README.md).

## Running the analysis

1. Install R and Java.
2. Install the packages used by the workflow.
3. Place the dataset under `data/`.
4. Open `h2o_autoencoder_pipeline.Rmd` in RStudio and run or knit the document.

## Scope

This is an experimental representation-learning project intended to demonstrate unsupervised deep learning and dimensionality reduction. It is not a production inference service.
