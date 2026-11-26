# Equine OA Proteomics Analysis

R Markdown workflows for protein-level quantification and differential expression analysis of equine osteoarthritis (OA) proteomics data.

## Analyses

- `equine_OA_proteomics_analysis_plasma.Rmd` — plasma samples; multidimensional scaling (MDS), differential expression, heatmaps, volcano plots, and protein abundance plots.
- `equine_OA_proteomics_analysis_SF.Rmd` — synovial fluid samples (carpus and fetlock); joint- and condition-related differential expression analyses, visualizations, and a paired synovial-fluid/plasma MDS comparison.

## Input data

The workflows expect the following files in the R working directory:

- `20260206_134557_SpN_Reesink_120EqCabalLaminSyFl_iun25_Report.tsv` — Spectronaut BGS Factory Report.
- `2026.02.05 Peralta AAEP Metadata_combined v2.xlsx` — sample metadata workbook.

These source data are intentionally **not included**. Obtain the files from the data owner and ensure that their use and redistribution are permitted before running or sharing the repository. The scripts currently refer to the filenames above; if your local filenames differ, update `file.use` and `pdata.file` near the beginning of each R Markdown document.

## Software requirements

Use R and RStudio (or another environment that supports `rmarkdown`). The analyses use the following R packages:

- CRAN: `readxl`, `ggplot2`, `dplyr`, `kableExtra`, `viridis`, `ggrepel`, `ggpubr`, `ggsignif`, `tidyr`, `knitr`, `rmarkdown`
- Bioconductor: `limpa`, `ComplexHeatmap`

Install the CRAN packages from R with:

```r
install.packages(c(
  "readxl", "ggplot2", "dplyr", "kableExtra", "viridis",
  "ggrepel", "ggpubr", "ggsignif", "tidyr", "knitr", "rmarkdown"
))
```

Install Bioconductor packages with:

```r
if (!requireNamespace("BiocManager", quietly = TRUE)) {
  install.packages("BiocManager")
}
BiocManager::install(c("limpa", "ComplexHeatmap"))
```

Package availability and installation requirements can vary by R/Bioconductor version. The documents report the R version and `limpa` version used at knit time in their Methods and session information sections.

## Run the analyses

1. Clone or download this repository.
2. Open the project directory in RStudio.
3. Place both required input files in the project directory (or update the input paths in each `.Rmd`).
4. Install the required packages.
5. Knit either R Markdown file to HTML.

The workflows write tab-delimited differential-expression tables, a CSV used for figure data, and figure files/directories to the current working directory. Run each document from the repository root so outputs are collected in a predictable location. Generated outputs and raw input data are excluded from version control by `.gitignore`.

## Reproducibility notes

- Peptide-level data were exported from Spectronaut Viewer 20.4.260109.92449 using the default settings described in the Methods sections.
- Protein-level quantification and differential expression use `limpa` as documented in the manuscripts cited in the R Markdown files.
- The statistical models and analysis choices are retained from the supplied analysis scripts. Review the Methods sections and generated session information when reproducing results.
- The source data are required to execute the analyses; the R Markdown files alone are not a self-contained reproducible dataset.

## Citation

Please cite the relevant `limpa` methods papers and R as listed in the Methods sections of the analysis documents, alongside any project- or dataset-specific citation required by the data owners.
