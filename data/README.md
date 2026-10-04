# Data directory

This project expects the large source dataset at:

```text
data/wave_functions.csv
```

The raw dataset is not committed to the repository. The R Markdown analysis reads a subset of the file using `data.table::fread()` and treats column 113 as the classification target.

Keep this filename and location, or update `data_path` in `autoencoders.Rmd`.
