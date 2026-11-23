# Clustering Superconducting Materials into Chemically Distinct Groups

**CSC1171 Data Analytics, Data Mining & Machine Learning · Presentation II project**

Group TBC: Malhar Phadke, Federico Singh, Dylan Jackson, Lucy McKee

> **Research question:** Can we use unsupervised machine learning to cluster superconductive materials into chemically or structurally distinct groups?

## Dataset

The SuperCon database from the National Institute for Materials Science (NIMS), Japan, in the cleaned and featurised version by Chao Zhuang (Kaggle). The file `featurized.csv` holds 16,521 materials, each with:
- its critical temperature `Tc`
- a known-family label `category`
- 146 descriptors computed from its chemical composition

`Tc` and `category` are held out from the clustering and used only afterwards, to interpret the clusters.

## Files

| File | What |
|---|---|
| `superconductor_clustering_project.ipynb` | The full analysis (Sections 0–13) |
| `featurized.csv` | The dataset (download from Kaggle; not included) |
| `project_outputs/` | Figures (`.png`) and tables (`.csv`) saved by the notebook for the slides |

## How to run

1. Install the requirements:
   ```
   pip install numpy pandas matplotlib scipy "scikit-learn>=1.3" jupyter
   ```
   scikit-learn 1.3 or newer is needed for HDBSCAN (Section 10a). With an older version, the notebook skips that section.
2. Put `featurized.csv` beside the notebook, or in `../data/` (course layout: notebook in `notebooks/`).
3. Open the notebook and run all cells from top to bottom. This takes a minute or two.

All randomness is fixed with `random_state=42`, so every run gives the same numbers.

## What the notebook does

| Section | What |
|---|---|
| 1–2 | Load the data, check quality, decide what to clean |
| 3 | Choose clustering features; keep `category` and `Tc` aside |
| 4 | Standardise, then PCA keeping 90% of the variance |
| 5 | Choose K with the elbow method and silhouette score |
| 6–7 | Fit K-Means and describe the clusters (descriptors, elements, Tc) |
| 8 | Compare the clusters with the known families (ARI, NMI, homogeneity, completeness) |
| 9 | Reliability checks: initialisation, resampling, 80/85/90% PCA, correlation pruning, choice of K, a no-structure baseline, excluding records with uncertain oxygen content |
| 10 | Extensions: HDBSCAN and a Gaussian mixture (soft clustering) |
| 11–13 | Answers to the class questions, limitations, conclusion |

## Sources

- **Data:** SuperCon, NIMS, Japan; *SUPERCON Dataset: A Superconductor Materials Database from NIMS*, Chao Zhuang, Kaggle.
- **Descriptors:** Magpie features (Ward et al., 2016, *npj Computational Materials* 2, 16028), computed with matminer (Ward et al., 2018).
- The notebook's final cell gives the full list of method references.

**AI use:** parts of the code and text were drafted with an AI assistant (Claude, Anthropic). See the disclosure at the end of the notebook.
