# Cross-Study Drug Response Prediction from Gene Expression

Can a cell line's gene expression predict its drug sensitivity, and does the
model still work on data from a different lab?

## Data
Public benchmark from Partin et al. (Zenodo, DOI 10.5281/zenodo.15258451):
CCLE and GDSC1 drug responses (AUC) with DepMap gene expression.
The data is not included here; the notebook downloads it.

## Method
- 16 drugs measured in both CCLE and GDSC1
- Features: 1,000 most variable genes
- Models: Random Forest, Elastic Net
- Within-study: 5-fold cross-validation
- Cross-study: train on one study, test on cell lines unseen in training from the other
- Metric: Spearman correlation

## Results
- Mean cross-study score 0.25 vs within-study 0.30 (difference not statistically conclusive, p = 0.084 pooled)
- Cross-study accuracy tracked how well the two studies agree with each other
  per drug (Spearman ρ ≈ 0.7, p < 0.005)
- Interpretation: predictability is limited by assay reproducibility

![Ceiling vs score](ceiling_vs_score.png)

## Limitations
- Only 16 drugs, with about 80 shared cell lines for many of them
- One feature set and mainly one model family
- Inspired by Xia et al. (2021), "A cross-study analysis of drug response
  prediction in cancer cell lines"; this is a small-scale exploration, not a
  reproduction of the paper

## Run it
Open the notebook in Google Colab and run all cells.
