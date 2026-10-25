# MSCS-634 Lab 5 — Hierarchical and DBSCAN Clustering

**Student:** Vineela Reddy Karnatakam  
**Course:** Advanced Big Data and Data Mining (MSCS-634)

## Purpose
Compare Ward agglomerative hierarchical clustering and DBSCAN on scikit-learn's Wine dataset. Explore feature distributions, standardize the 13 variables, visualize results with PCA scatter plots and a dendrogram, and evaluate silhouette, homogeneity, and completeness.

## Run in VS Code (Windows PowerShell)
1. Unzip this folder and open **MSCS_634_Lab_5** in VS Code.
2. Install Microsoft's **Python** and **Jupyter** VS Code extensions.
3. Open a VS Code terminal and run:
   ```powershell
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   python -m pip install -r requirements.txt
   ```
   If script activation is blocked, run `.\.venv\Scripts\python.exe -m pip install -r requirements.txt` instead.
4. Open `MSCS_634_Lab_5.ipynb`, click **Select Kernel** and choose `.venv` / Python 3.
5. Click **Run All** to reproduce tables and charts.

macOS/Linux alternative: `python3 -m venv .venv && source .venv/bin/activate && python -m pip install -r requirements.txt`.

## Key findings and interpretation
- Standardization prevents large-valued chemical measurements from dominating distance comparisons.
- Hierarchical clustering creates a partition for every chosen `n_clusters` and offers a dendrogram to see merges; the best cluster count should be evaluated, not assumed to match the three known classes.
- DBSCAN is highly sensitive to `eps` and `min_samples`. Small neighborhoods often lead to many noise points, while larger neighborhoods can merge separate groups. It can identify noise but may give only one dense group at larger `eps`.
- Silhouette scores are defined here **only for assigned DBSCAN points** with at least two clusters. Homogeneity and completeness use all labels, including noise. Compare these with the noise fraction and number of clusters.
- The notebook prints experiment-specific results, renders figures, and identifies candidate settings based on silhouette. Its conclusion discusses tradeoffs instead of presenting an invalid metric for a one-cluster result.

## Decisions and challenges
- PCA is used **only to plot** the full-feature clustering output, not for clustering itself.
- Known Wine labels are used exclusively for external evaluation.
- In high dimensions, a single DBSCAN density threshold may not recover the variety classes well, so a parameter sweep is used instead of assuming one eps value fits.

## Files
- `MSCS_634_Lab_5.ipynb` - complete analysis and visualizations (saved with computed outputs).
- `requirements.txt` - Python dependencies.
- `README.md` - setup, analysis description and key findings.

