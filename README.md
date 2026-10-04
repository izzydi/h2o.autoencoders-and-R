# H2O Autoencoders in R

An R project exploring **H2O deep-learning autoencoders** for representation learning, dimensionality reduction and anomaly-oriented analysis on high-dimensional data.

## Project overview

The workflow preprocesses a labelled dataset, converts it to H2O frames, trains sparse deep autoencoders, extracts hidden-layer representations and compares learned features with other dimensionality-reduction approaches.

## Repository contents

- [`autoencoders.Rmd`](autoencoders.Rmd) — complete R Markdown analysis.

## Methods and tools

The source uses H2O deep learning together with a tidymodels-style preprocessing workflow. It includes:

- stratified train/test splitting,
- Yeo-Johnson transformation and normalization,
- sparse autoencoder training,
- extraction of deep features,
- reconstruction-based outputs,
- architecture grid search,
- sparsity hyperparameter search,
- comparison with PCA-style representations.

## Requirements

The analysis assumes that the input dataframe (`df`) has already been prepared before the code shown in `autoencoders.Rmd` is run. It also starts a local H2O instance and therefore requires a working Java/H2O installation.

## Reproducing the analysis

1. Install R and the required packages, including `h2o`, `tidymodels`/`recipes`, `dplyr` and `ggplot2` as used by the workflow.
2. Prepare the input dataframe expected by the R Markdown file.
3. Start the analysis in an environment where H2O can launch locally.
4. Run the document sequentially.

## Scope

This repository is an experimental deep-learning project focused on learned representations rather than a packaged production model.
