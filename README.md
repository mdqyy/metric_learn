# metric_learn

Metric Learning algorithms in Python.

**Algorithms**

 * Large Margin Nearest Neighbor (LMNN)
 * Information Theoretic Metric Learning (ITML)
 * Sparse Determinant Metric Learning (SDML)
 * Least Squares Metric Learning (LSML)

**Dependencies**

 * Python 2.6+
 * numpy, scipy, scikit-learn
 * (for the demo only: matplotlib)

**Usage**

For full usage examples, see `test.py` and `demo.py`.

Each metric is a subclass of BaseMetricLearner, which provides default implementations for the methods
`metric`, `transformer`, and `transform`.
Subclasses must provide an implementation for either `metric` or `transformer`.

For an instance of a metric learner named `foo` learning from a set of `d`-dimensional points,
`foo.metric()` returns a `d` by `d` matrix `M` such that a distance between vectors `x` and `y` is
expressed `(x-y).dot(M).dot(x-y)`.

In the same scenario, `foo.transformer()` returns a `d` by `d` matrix `L` such that a vector `x`
can be represented in the learned space as the vector `L.dot(x)`.

For convenience, the function `foo.transform(X)` is provided for converting a matrix of points (`X`)
into the learned space, in which standard Euclidean distance can be used.

**Notes**

If a recent version of the Shogun Python modular (`modshogun`) library is available,
the LMNN implementation will use the fast C++ version from there.
The two implementations differ slightly, and the C++ version is more complete.
