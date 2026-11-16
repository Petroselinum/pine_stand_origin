# Divergent development patterns in Scots pine forests are linked to land-use history and stand origin

R code for the statistical analyses in the article by Stanisław Zięba, Piotr Budniak, Jan Banaś and Leszek Bujoczek (submitted to *Forest Ecology and Management*).

The study compares stands dominated by Scots pine (*Pinus sylvestris* L.) on 12,620 sample plots of the fourth cycle (2020–2024) of the Polish National Forest Inventory (NFI). There are four types of stand origin:

| Code | Stand origin |
|---|---|
| A | Afforestation of post-agricultural land |
| NS | Natural succession on post-agricultural land |
| AR | Artificial regeneration on land with continuous forest cover |
| NR | Natural regeneration on land with continuous forest cover |

## Contents

- `pine_stand_origin_analysis.ipynb` is a Jupyter notebook (R kernel) with the code and results of all analyses, executed on the full data set. It reproduces Tables 2–5, Figures 3–11 and Supplementary Tables S1–S30 of the article. Figures 1 and 2 are maps prepared in GIS software and are not produced by the notebook.

## Data

The NFI data analyzed in the study are not the property of the authors, and the authors do not have permission to share them. The data are therefore not included in this repository. The notebook shows only aggregated results and the first five rows of each input table, with sequential numbers instead of plot and cluster identifiers.

The notebook reads seven CSV files from the `data/` folder. Their structure is described in Section 1.1 of the notebook:

| File | One row per |
|---|---|
| `plots.csv` | plot (stands up to 120 years old) |
| `site_types.csv` | plot |
| `species_groups.csv` | plot × species group |
| `tree_counts.csv` | plot |
| `standing_dead_trees.csv` | plot |
| `pca_plots.csv` | plot (stands of all ages, for the ordination) |
| `trees.csv` | tree |

## Requirements

- R 4.3.1 with Jupyter and the IRkernel.
- Packages, with the versions used for the published results: mgcv 1.9-0, gamm4 0.2-6, lme4 2.0-6, nlme 3.1-163, emmeans 1.10.0, MASS 7.3-60, sandwich 3.1-0, lmtest 0.9-40, car 3.1-2, multcomp 1.4-25, vegan 2.6-4, ggplot2 4.0.3, ggrepel 0.9.5, cowplot 1.2.0, ragg 1.2.6, dplyr 1.1.3, tidyr 1.3.0, readr 2.1.4 and jsonlite.
- The figures use the Liberation Sans font.

Section 8 of the notebook lists the versions found at run time.

## Running the notebook

1. Put the input files in `data/`.
2. Execute the notebook, for example:

   ```bash
   OPENBLAS_NUM_THREADS=1 jupyter nbconvert --to notebook --execute pine_stand_origin_analysis.ipynb
   ```

   A full run takes about 2–3 minutes.

With `save_outputs <- TRUE` (the default), figures (PNG, 300 dpi) and tables (CSV and JSON) are also written to `output/`. Permutation tests and the cluster bootstrap use a fixed random seed (`set.seed(2026)`), so repeated runs give the same results. The labels in the PCA biplot (Figure 7) may be placed slightly differently between runs. Their placement has a time limit (`ggrepel`), and that limit depends on the computer's load.

The R code was written with the assistance of the generative AI model Claude Opus 5.5 (Anthropic) and was reviewed by the authors (Section 2.6 of the article).

## Citation

If you use this code, please cite the article and the archived version of the code:

- Zięba, S., Budniak, P., Banaś, J., Bujoczek, L. Divergent development patterns in Scots pine forests are linked to land-use history and stand origin. Submitted to *Forest Ecology and Management*.
- Code: Zenodo, https://doi.org/10.5281/zenodo.24203472 (version 1.2). The concept DOI https://doi.org/10.5281/zenodo.24169115 always resolves to the latest version.

## License

CC BY 4.0, as stated in the Zenodo record.
