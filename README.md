# One combined-city PCA–KMeans model

Start with reports/model_report.html for the full explanation, figures, metrics and interview guide.

## Run

Install guide/requirements.txt in a Python environment, start Jupyter in this project folder and run all cells in Metro_PCA_KMeans.ipynb. Seven code sections cover data/EDA, shared preparation, one global model, rankings, evaluation and report generation. Inputs are frozen and bundled; no API key is needed. The notebook begins with prepared features rather than downloading remote raw datasets.

## Workflow

29,941 areas from eight metros → eight features → shared scaling and PCA → 4 components (91.70% transformed variance retained) → ONE KMeans model with K=4 → global cluster priorities and within-city candidate rankings.

K=4 is a user-requested choice for finer segmentation; silhouette favors two clusters. The report makes this tradeoff explicit. The revised model reuses the previously inspected holdout, so comparison is exploratory.

Cities share the same preprocessing, component axes, centroids and priority definitions. City names and coordinates are not model features. Spatial holdouts are drawn within cities and pooled to evaluate the one model. They do not create separate city models. No second clustering method is needed: profile and priority tables explain the groups.

## Contents

- data/: feature dataset, mapped Blinkit reference, provenance.
- model/: global_model.joblib and area_assignments.csv (clusters, priority, score, rank and split).
- reports/: self-contained report, EDA/PCA plots, geographic reference comparison, comparison graphs, metrics and ranking CSVs.
- guide/: this guide and dependency versions.
- Metro_PCA_KMeans.ipynb: the only analytical source, with executed outputs.

## Explain results correctly

PCA retention measures variance of transformed features, not accuracy. Cluster priorities are fixed business assumptions, not profit labels. The potential index is a smooth weighted cluster-utility score, not a probability. Compare performance with population-only, weighted-rule and random baselines. Geographic match rates measure retrospective alignment with an incomplete unofficial store reference; they do not establish future-opening accuracy, profitability or suitability of a vacant property.

WorldPop is modeled 2026 population; amenity snapshots vary and stores are from March 2026. Traffic, congestion, income, rents and travel-time isochrones are unavailable, so none were fabricated. Read source metadata before redistributing data.

## Verification

All seven sections executed. The single saved model reproduces every exported cluster assignment and potential score. No separate city-model artifact remains. Reference notebook was read as a workflow example and not modified.
