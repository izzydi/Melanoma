# Melanoma Statistical Analysis in R

An academic statistical-analysis project using the `melanoma` dataset distributed with R's `boot` package.

## Primary workflow

[`melanoma_analysis.Rmd`](melanoma_analysis.Rmd) is the audited source. It combines descriptive analysis, non-parametric comparison, correlation, a stratified logistic-regression example and a regression tree for tumour thickness.

## Repository contents

- [`melanoma_analysis.Rmd`](melanoma_analysis.Rmd) — audited R Markdown source.
- [`archive/legacy_assignment.Rmd`](archive/legacy_assignment.Rmd) — original coursework retained for provenance.
- [`R-packages.txt`](R-packages.txt) — direct R dependencies.
- [`.gitignore`](.gitignore) — local R artifacts.

## Audit improvements

The original assignment contained a spelling error in the outcome recoding and stored `glm_model$coefnames` as if it were the coefficient values. The current source uses `coef(glm_model$finalModel)`, stratifies the hold-out split and documents the important limitation that the historical three-level status variable is simplified to a binary educational endpoint.

## Data

No external file is needed: the analysis uses `boot::melanoma` directly.

## Reproducing the analysis

1. Install packages listed in [`R-packages.txt`](R-packages.txt).
2. Open `melanoma_analysis.Rmd` in RStudio.
3. Run or knit the document from top to bottom.

## Scope

This is a statistical-programming portfolio project, **not** a clinical decision-support system. The binary outcome used in the modelling section is an explicit analytical simplification and should not be interpreted as a clinical endpoint definition.
