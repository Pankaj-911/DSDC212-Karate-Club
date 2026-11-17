# DSC212 Graph Theory – Modularity on the Karate Club Graph

Recursive **spectral modularity partitioning** (Newman, 2006) implemented from scratch with NumPy and
NetworkX on Zachary's Karate Club network, with visualisations, node metrics and a discussion.

## Contents

| File / folder | Description |
|---|---|
| `DSC212_Modularity_Karate_Club.ipynb` | The submission notebook (code, explanations, outputs, plots, discussion) |
| `figures/` | All plots saved as PNG (graph after every split, metric evolution plots) |
| `requirements.txt` | Python packages needed |
| `SUBMISSION_CHECKLIST.md` | Task-by-task checklist |
| `GITHUB_UPLOAD.md` | How to publish the repository |

## What the notebook does

1. Builds the adjacency matrix `A`, degree vector `k` and modularity matrix `B = A - k kᵀ / 2m`.
2. Splits a group using the sign of the leading eigenvector of its block `B^(C)`; stops when the
   leading eigenvalue is ≤ 0 (or the sign split would leave a group empty). Recurses on both halves.
3. Draws the graph after every split (fixed spring layout, one colour per community, node IDs).
4. After every split computes degree, betweenness, closeness centrality and clustering with NetworkX.
5. Plots the evolution of each metric for every node, and discusses the results.

**Result:** 4 successful splits → 5 communities, final modularity Q = 0.4094. The first split (16 + 18 nodes)
matches the real club split for 33 of 34 members.

> Metrics "after a split" are computed *inside each node's community* (induced subgraph); on the whole graph
> they would never change. See §6 and §9 of the notebook for this and other remarks on the handout.

## How to run

```bash
python -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook DSC212_Modularity_Karate_Club.ipynb
```
Then choose **Kernel → Restart & Run All**. No manual input is needed (runtime a few seconds).
The notebook already contains its outputs, so it can also be read directly on GitHub.

## Reference
M. E. J. Newman (2006), *Modularity and community structure in networks*, PNAS 103(23): 8577–8582.
