# Dimensionality Reduction

Principal component analysis, multidimensional scaling and Isomap, derived from
first principles rather than called from a library.

Assignment 1 of **DD2434 Machine Learning, Advanced Course**, KTH, autumn 2021.

📄 **[Read the report](report.pdf)** · [assignment brief](assignment.pdf)

## What it covers

**PCA.** Why centering is required before PCA, and what happens without it — the
mean ends up in the first component instead of the variance, and the components
stop being decorrelated. Why one SVD does not give you PCA on both the rows and
the columns of a matrix, since row-centering and column-centering are different
operations. Why the pseudo-inverse is the right inverse mapping, and why it
collapses to $W^\top$ when $W$ has orthonormal columns. Finally, a derivation of
PCA by variance maximisation, shown to give the same answer as minimising
reconstruction error, for a projection into $k$ dimensions rather than just one.

**MDS and Isomap.** Classical multidimensional scaling, and where it fails —
when the data lies on a curved manifold, Euclidean distance is the wrong
metric, which is what Isomap's geodesic distances fix.

## The MDS experiment

[`mds/mds.ipynb`](mds/mds.ipynb) reconstructs a world map from nothing but
pairwise distances. Taking the coordinates of world capitals
([`world-capitals.csv`](mds/world-capitals.csv), from
[Kaggle](https://www.kaggle.com/nikitagrec/world-capitals-gps)), it computes the
great-circle distance between every pair of cities, throws the coordinates away,
and hands only the distance matrix to MDS.

What comes back is a recognisable map. It is rotated and reflected, because
distances alone cannot fix orientation or handedness — but the relative
positions of the continents are recovered.

[`mds/mds-appendix.pdf`](mds/mds-appendix.pdf) is the notebook rendered with its
output, as submitted.

```bash
pip install numpy pandas matplotlib seaborn scikit-learn geopy
jupyter notebook mds/mds.ipynb
```
