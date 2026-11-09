# MSCS-634 Lab 3: K-Means and K-Medoids Clustering

**Student:** Bharath Kumar Origanti  
**Course:** Advanced Big Data and Data Mining (MSCS-634)

## Purpose
Compare K-Means and K-Medoids clustering on the scikit-learn Wine dataset, using three clusters and evaluating the results with Silhouette Score and Adjusted Rand Index (ARI).

## Files
- `MSCS_634_Lab_3_KMeans_KMedoids.ipynb`: Complete executed Jupyter notebook with code, data exploration, results, comparison, and interpretation.
- `clustering_comparison.png`: Side-by-side PCA scatter plots showing clusters and centroids/medoids.

## How to run
1. Install Python 3 and Jupyter Notebook or JupyterLab.
2. Install dependencies: `pip install numpy pandas matplotlib scikit-learn notebook`
3. Open `MSCS_634_Lab_3_KMeans_KMedoids.ipynb` in Jupyter.
4. Choose **Run All**. The notebook saves `clustering_comparison.png` to the current working folder.

The notebook uses the built-in Wine dataset; no separate data download is necessary. K-Medoids is implemented in the notebook using a PAM-style medoid-swap search, so `scikit-learn-extra` is not required.

## Results (run with random seed 42)

| Algorithm | Silhouette Score | Adjusted Rand Index (ARI) |
|---|---:|---:|
| K-Means | 0.2849 | 0.8975 |
| K-Medoids | 0.2676 | 0.7411 |

K-Means achieved the higher Silhouette Score and ARI for this run. Both methods identified meaningful groups, but the methods optimize different distance-based objectives. Cluster numbers themselves are arbitrary and should not be compared directly with the wine class IDs.

## Observations and design decisions
- The dataset contains 178 wine samples, 13 numeric features, and 3 known classes.
- StandardScaler performs z-score normalization so features with larger numeric ranges do not dominate distance calculations.
- The models are fitted on all 13 scaled features; PCA is used **only** to show a two-dimensional visualization.
- K-Means centroids are means and may not correspond to actual observations. K-Medoids centers are real observations.
- The K-Medoids implementation checks medoid swaps and is computationally expensive compared with K-Means. It is appropriate for this small dataset but not ideal for very large datasets.
- Results may differ with other random seeds or K-Medoids implementations.

## Challenges
Implementing K-Medoids without an additional package required explicitly calculating pairwise distances and testing candidate medoid swaps. The solution favors transparency and reproducibility for the small Wine dataset.

## References
- [scikit-learn Wine dataset](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_wine.html)
- [scikit-learn KMeans](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)
- [scikit-learn clustering evaluation](https://scikit-learn.org/stable/modules/clustering.html#clustering-performance-evaluation)
