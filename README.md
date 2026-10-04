# Melanoma Statistical Analysis in R

An academic statistical-analysis project using the `melanoma` dataset distributed with R's `boot` package.

## Primary workflow

[`melanoma_analysis.Rmd`](melanoma_analysis.Rmd) is the audited source. It combines descriptive analysis, non-parametric comparison, correlation, a stratified logistic-regression example and a regression tree for tumour thickness.

## Repository contents

- [`melanoma_analysis.Rmd`](melanoma_analysis.Rmd) — audited R Markdown source.
- [`archive/legacy_assignment.Rmd`](archive/legacy_assignment.Rmd) — original coursework retained for provenance.
- [`R-packages.txt`](R-packages.txt) — version-pinned direct R dependencies.
- [`.github/workflows/r-ci.yml`](.github/workflows/r-ci.yml) — R 4.6.1 dependency and syntax CI.
- [`.gitignore`](.gitignore) — local R artifacts.

## Audit improvements

The original assignment contained a spelling error in the outcome recoding and stored `glm_model$coefnames` as if it were the coefficient values. The current source uses `coef(glm_model$finalModel)`, stratifies the hold-out split and documents the important limitation that the historical three-level status variable is simplified to a binary educational endpoint.

The tumour-thickness regression has also been corrected for temporal/post-outcome leakage: follow-up `time` and outcome `status` are no longer used as predictors of tumour thickness. The regression tree now uses only `sex`, `age`, `year` and `ulcer`, which are available at or near baseline.

## Reproducibility and CI

No external dataset is required because the analysis uses `boot::melanoma`. Direct R package versions are pinned in [`R-packages.txt`](R-packages.txt), and GitHub Actions uses R 4.6.1 plus `pak` to install those exact direct versions and parse the canonical R Markdown source.

`R-packages.txt` pins the direct dependencies; it is not a complete `renv.lock` snapshot for every recursive dependency.

## Reproducing the analysis

1. Install R 4.6.1.
2. Install `pak` and the pinned direct dependencies:

```r
install.packages("pak")
pak::pkg_install(readLines("R-packages.txt"), upgrade = FALSE)
```

3. Open `melanoma_analysis.Rmd` in RStudio.
4. Run or knit the document from top to bottom.

## Scope

This is a statistical-programming portfolio project, **not** a clinical decision-support system. The binary outcome used in the modelling section is an explicit analytical simplification and should not be interpreted as a clinical endpoint definition.
