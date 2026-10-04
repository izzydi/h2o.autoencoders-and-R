# H2O Autoencoders in R

An R project exploring **H2O deep-learning autoencoders** for representation learning, dimensionality reduction and anomaly-oriented analysis on high-dimensional wave-function data.

## Project overview

The workflow is now self-contained: it loads the source data, creates a labelled sample, performs a stratified train/test split, learns preprocessing from the training data only, starts a local H2O instance and trains sparse autoencoders. The learned representation is compared with PCA and explored through architecture and sparsity grid searches.

## Repository contents

- [`autoencoders.Rmd`](autoencoders.Rmd) — complete reproducible R Markdown workflow.
- [`data/README.md`](data/README.md) — expected raw-data layout.

## Methods and tools

The project uses:

- `h2o` for deep autoencoders and hyperparameter search,
- `tidymodels`/`recipes` for train/test splitting and preprocessing,
- `data.table` for efficient loading of a large CSV,
- `dplyr` for data manipulation,
- `ggplot2` for visualisation.

The analysis includes:

1. stratified sampling and splitting,
2. training-only Yeo-Johnson transformation and normalization,
3. sparse deep-autoencoder training,
4. extraction of learned hidden-layer features,
5. PCA comparison,
6. architecture grid search,
7. sparsity-penalty search,
8. reconstruction-error inspection,
9. export of train/test embeddings.

## Reproducibility

The original source depended on an already-created `df` object, so it could not run independently. The current version loads the dataset explicitly from a project-relative path and creates every object it needs inside the document.

## Data requirements

The large raw dataset is not stored in this repository. Place it at `data/wave_functions.csv`, as described in [`data/README.md`](data/README.md).

## Running the analysis

1. Install R and Java.
2. Install `h2o`, `tidymodels`, `data.table`, `dplyr` and `ggplot2`.
3. Place the dataset under `data/`.
4. Open `autoencoders.Rmd` in RStudio and run or knit the document.

## Scope

This is an experimental representation-learning project intended to demonstrate unsupervised deep learning and dimensionality reduction. It is not a production inference service.
